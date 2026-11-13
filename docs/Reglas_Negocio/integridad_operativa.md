# Área 25 — Integridad operativa, concurrencia y recuperación ante fallos

**Versión:** 1.0  
**Estado:** Pendiente de aprobación.  
**Formato:** identificador y descripción completa de cada entrada.

Esta área consolida las condiciones transversales de confirmación, idempotencia, concurrencia, edición simultánea y conectividad, sin alterar las excepciones de cada giro ni las etapas parciales previamente aprobadas. Los identificadores de otras áreas se reutilizan como referencias vigentes y no se suman de nuevo al catálogo global.

## Reglas de negocio (RN)

- **RN-INT-001** — Una operación que modifica registros interdependientes solo se considera confirmada cuando todos sus cambios obligatorios quedan aplicados, salvo las etapas parciales expresamente autorizadas.

- **RN-INT-002** — El reenvío de una misma operación identificada no constituye una operación nueva y no puede producir efectos adicionales a los que ya fueron confirmados.

- **RN-INT-003** — Una operación que modifica información del SaaS requiere conexión al servidor y no puede confirmarse mediante ejecución sin conexión.

- **RN-INT-004** — Una operación enviada cuyo resultado no se recibió por pérdida de conexión conserva un estado no determinado para el usuario hasta que se consulte su resultado registrado.

- **RN-INT-005** — La edición de un registro no puede sobrescribir silenciosamente cambios que otro usuario haya confirmado después de que comenzó la edición.

- **RN-INV-005** — Ninguna operación confirmada de inventario produce existencias negativas en el ámbito de stock que afecta.

- **RN-INV-015** — Una existencia o unidad solo se considera disponible para una operación si satisface todas las restricciones vigentes aplicables.

- **RN-INV-016** — Toda operación que compromete existencias vuelve a validar las cantidades y restricciones aplicables en el momento de su confirmación.

- **RN-CSV-014** — Reenviar una misma ejecución confirmada de importación no puede volver a crear los mismos registros ni duplicar sus movimientos de entrada.

- **RN-USU-025** — La revocación de permisos tiene efecto inmediato incluso en sesiones ya iniciadas, y el cambio entre usuario limitado y administrador completo requiere una nueva autenticación.

## Requisitos funcionales (RF)

- **RF-INT-001** — El sistema permite consultar por identificador el resultado de una operación enviada antes de una interrupción de conexión y evita repetirla cuando ya existe un resultado confirmado.

- **RF-INT-002** — El sistema detecta cambios confirmados por otro usuario en el registro que se está editando y solicita revisar el conflicto antes de permitir sobrescribir la información actualizada.

- **RF-INT-003** — El sistema impide confirmar nuevas operaciones cuando no existe comunicación con el servidor e informa que debe verificarse el resultado de cualquier solicitud enviada antes de la interrupción.

- **RF-INV-010** — El sistema permite consultar el resultado de una operación de inventario mediante su identificador después de una interrupción de conexión y evita repetir efectos ya confirmados.

- **RF-INV-011** — El sistema detecta que un registro de catálogo fue modificado por otro usuario durante su edición y solicita resolver el conflicto antes de sobrescribir información actualizada.

- **RF-CSV-015** — El sistema permite consultar el resultado de una importación por su identificador después de una interrupción de conexión, sin volver a aplicar los efectos de una ejecución ya confirmada.

- **RF-SUS-003** — El sistema crea una referencia única para cada obligación de pago y conserva su estado y los intentos relacionados, sin tratar una solicitud enviada como confirmación definitiva.

- **RF-SUS-005** — El sistema evita procesar dos veces una misma obligación de pago cuando coinciden respuestas de la pasarela y reintentos automáticos o manuales.

## Requisitos no funcionales (RNF)

- **RNF-INT-001** — Los cambios obligatorios asociados a una etapa confirmable de una operación se aplican íntegramente o se revierten, sin impedir las etapas parciales expresamente permitidas por las reglas del sistema.

- **RNF-INT-002** — La ejecución concurrente de operaciones que afectan las mismas existencias o unidades mantiene sus restricciones de disponibilidad y evita cantidades negativas y asignaciones incompatibles.

- **RNF-INT-003** — Las solicitudes repetidas correspondientes a la misma operación identificada producen como máximo un efecto confirmado y permiten recuperar su resultado persistido después de una interrupción.

- **RNF-INV-001** — Cada etapa confirmable de inventario aplica de forma atómica todas las modificaciones relacionadas, de modo que un fallo no deje entradas, movimientos o rectificaciones confirmados parcialmente salvo etapas independientes expresamente admitidas.

- **RNF-INV-002** — La ejecución concurrente de operaciones sobre las mismas existencias mantiene stock no negativo, respeta todas las restricciones de disponibilidad y vuelve a verificar cantidades al confirmar.

- **RNF-INV-003** — La repetición de una operación de inventario con el mismo identificador produce como máximo un efecto y permite recuperar de forma consistente su resultado original.

- **RNF-INV-005** — Las operaciones que modifican inventario requieren comunicación con el servidor y solo se confirman tras la validación vigente de cantidades y restricciones.

- **RNF-VEN-001** — El sistema confirma de manera atómica los registros de entrega o devolución y sus movimientos de inventario asociados, sin dejar confirmaciones comerciales incongruentes con las existencias.

- **RNF-VEN-004** — El sistema consulta el resultado de una venta enviada antes de una interrupción de conexión y solamente permite reintentarla cuando pueda evitar un segundo registro o descuento de existencias.

- **RNF-MAN-001** — Las confirmaciones de inicio y cierre de mantenimiento actualizan de forma atómica los estados de la intervención y las restricciones de disponibilidad relacionadas, sin dejar cambios parciales confirmados.

- **RNF-BAJ-002** — Las solicitudes concurrentes de baja, venta, préstamo, mantenimiento o ajuste sobre las mismas existencias se validan de nuevo antes de confirmar y no generan estados incompatibles ni stock negativo.

- **RNF-MSU-002** — El despacho y cada recepción confirmable de un traslado actualizan de manera atómica los registros relacionados con cantidades, tránsito y sucursales, sin dejar movimientos confirmados parcialmente por fallos técnicos.

- **RNF-MSU-003** — El sistema controla las solicitudes concurrentes y repetidas de despacho y recepción para que ninguna existencia sea despachada o recibida dos veces, ni produzca stock local negativo.

- **RNF-CSV-001** — Cada ejecución de importación confirma atómicamente todas las filas válidas seleccionadas y revierte el conjunto completo ante un error que impida confirmarlo.

- **RNF-CFG-005** — La edición simultánea de un mismo parámetro detecta cambios concurrentes y evita sobrescribir silenciosamente la modificación confirmada por otro administrador.

- **RNF-SUS-002** — El procesamiento de confirmaciones, notificaciones repetidas y reintentos de cobro es idempotente y no genera activaciones ni cargos duplicados por la misma obligación.

- **RNF-ALT-004** — El alta mantiene coherentes el estado del pago, la habilitación de la contratación y los derechos de acceso aunque alguna etapa de confirmación falle parcialmente.

- **RNF-UBI-002** — La confirmación de una reubicación interna actualiza de manera atómica los registros relacionados con el origen, el destino y el movimiento para evitar cambios incompletos.

- **RNF-STO-002** — Las actualizaciones concurrentes o los reenvíos de una operación no generan efectos de stock duplicados ni notificaciones repetidas de una misma transición de alerta.

## Reglas comerciales (RC)

No se identifican reglas comerciales nuevas exclusivas de esta área; se mantienen las reglas aprobadas de planes, pagos y suscripciones.

## Pendientes de definición (PT)

- **PT-INT-001** — Está pendiente de definición técnica cómo se identifican las operaciones para reconocer reenvíos y cuánto tiempo se conservan sus resultados consultables según su tipo.

- **PT-INT-002** — Está pendiente de definición de negocio el inventario completo de operaciones y etapas que admiten confirmaciones parciales, sin ampliar las excepciones actualmente autorizadas.

- **PT-INT-003** — Está pendiente de definición la interacción concreta para revisar un conflicto de edición, incluidas las opciones para recuperar la versión actualizada y conservar cambios aún no confirmados.

- **PT-INT-004** — Está pendiente de definición el procedimiento visible para el usuario cuando, después de restablecer la conexión, todavía no puede determinarse el resultado de una operación enviada.

- **PT-INT-005** — Está pendiente de diseño técnico cómo se coordinan transacciones de base de datos, procesamiento de solicitudes, validaciones de permisos y eventos externos sin permitir confirmaciones incoherentes.

- **PT-INT-006** — Está pendiente de definición el tratamiento de operaciones iniciadas antes de una suspensión de suscripción o revocación de permisos, sin exceptuar su validación obligatoria al momento de confirmar.

- **PT-INV-003** — El diseño técnico documentará el mecanismo de transacciones, control de concurrencia, identificadores idempotentes y verificación de resultados de operaciones de inventario.

- **PT-CSV-008** — Está pendiente especificar el mecanismo técnico de procesamiento, validación transaccional, control de concurrencia e idempotencia de archivos CSV en Laravel y PostgreSQL.

- **PT-SUS-012** — Está pendiente definir el tratamiento de una confirmación de pago tardía recibida después de la terminación por impago, evitando activar sin una regularización o recontratación válida.

## Revisión de consistencia con las áreas aprobadas

- **Inventario, Bajas, Caducidades y Ventas:** la confirmación atómica y la validación concurrente no permiten stock negativo, salidas duplicadas ni ventas con lotes vencidos; las ventas pendientes con stock insuficiente mantienen el tratamiento específico de su giro.
- **Préstamos, Mantenimiento e Incidencias:** se mantienen todas las restricciones simultáneas de disponibilidad; la confirmación de una operación no elimina otras causas de indisponibilidad.
- **Multisucursal:** el despacho y cada recepción se consideran etapas confirmables independientes, y las recepciones parciales autorizadas no se convierten en fallos de atomicidad.
- **Carga CSV:** se mantiene la ejecución atómica del conjunto de filas válidas seleccionadas y la prohibición de repetir efectos de una importación confirmada.
- **Configuración y administración de usuarios:** no se admite sobrescribir silenciosamente un registro desactualizado y las revocaciones de permisos surten efecto inmediato, incluso en sesiones existentes.
- **Suscripciones y alta:** los eventos de pago repetidos o tardíos no habilitan servicios indebidamente y la confirmación del pago sigue siendo requisito para las transiciones comerciales.
- **Conectividad:** la ausencia de respuesta no equivale a una confirmación fallida; el resultado debe consultarse antes de un reintento que pudiera duplicar efectos.

**Resultado:** no se identificaron contradicciones funcionales nuevas con las áreas 01–24. Se mantiene pendiente de corrección global la colisión histórica de identificadores `PRE` entre Préstamos y Prescripciones médicas; esta área no introduce IDs afectados.

## Control de duplicidades

Los identificadores `RN-INT`, `RF-INT`, `RNF-INT` y `PT-INT` son nuevos; los demás identificadores de este documento se incluyen para mostrar la aplicación transversal de requisitos ya aprobados y no constituyen requisitos adicionales.

## Recuento

- **RN:** 5 entradas nuevas y 5 referencias vigentes.
- **RF:** 3 entradas nuevas y 5 referencias vigentes.
- **RNF:** 3 entradas nuevas y 16 referencias vigentes.
- **PT:** 6 entradas nuevas y 3 referencias vigentes.
- **Total:** 17 entradas nuevas y 29 referencias vigentes.
