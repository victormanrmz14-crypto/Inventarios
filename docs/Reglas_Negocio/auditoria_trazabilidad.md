# Área 22 — Auditoría y trazabilidad transversal

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.  
**Formato:** identificador y descripción completa por entrada.  

Este catálogo recoge las obligaciones comunes de auditoría y no sustituye las disposiciones específicas ya aprobadas para cada módulo. Los **PT** expresan decisiones pendientes y no autorizan funcionalidades adicionales.

## Reglas de negocio (RN)

- **RN-AUD-001** — Toda modificación relevante de inventario, ventas, préstamos, mantenimiento, bajas, configuración, usuarios, permisos, sucursales y contratación debe conservar una evidencia auditable de la actuación realizada.

- **RN-AUD-002** — Cada registro de auditoría de una modificación relevante identifica al responsable, al tenant afectado, la fecha y hora, la acción realizada, los registros relacionados y la sucursal cuando corresponda.

- **RN-AUD-003** — Los registros de auditoría confirmados son inalterables para los usuarios del tenant, incluidos el administrador principal y los administradores completos.

- **RN-AUD-004** — La conservación, anonimización o eliminación legalmente procedente de registros auditables solo puede ejecutarse mediante un procedimiento controlado, sin autorizar su manipulación ordinaria por los usuarios del tenant.

- **RN-AUD-005** — La auditoría de un tenant permanece aislada de los demás tenants y las intervenciones extraordinarias del superadmin conservan una justificación y trazabilidad propias.

- **RN-AUD-006** — Una rectificación de una operación confirmada conserva el registro original y la referencia a la actuación correctiva correspondiente, sin sustituir silenciosamente la evidencia anterior.

## Requisitos funcionales (RF)

- **RF-AUD-001** — El sistema registra los cambios relevantes efectuados en los módulos operativos, en la administración de usuarios, en la configuración y en la contratación, identificando la acción que se ejecutó y su resultado confirmado.

- **RF-AUD-002** — El sistema asocia cada modificación auditable con el usuario o actor responsable, el tenant, la fecha y hora, los registros afectados y la sucursal cuando la operación pertenezca a una de ellas.

- **RF-AUD-003** — El sistema conserva las referencias necesarias para relacionar un movimiento, registro o cambio confirmado con las operaciones previas y correctivas que formen parte de su historial.

- **RF-AUD-004** — El sistema registra los cambios de roles, perfiles, permisos y asignaciones de sucursal con el usuario afectado, el responsable, los valores anteriores y nuevos y el momento de la modificación.

- **RF-AUD-005** — El sistema registra los cambios de parámetros de configuración con su ámbito general o de sucursal, su valor anterior, su valor nuevo, su responsable y el momento de confirmación.

- **RF-AUD-006** — El sistema registra los intentos fallidos de acceso y otros eventos de seguridad relevantes de las cuentas conforme a los controles establecidos para la autenticación y la administración de sesiones.

- **RF-AUD-007** — El sistema registra las intervenciones extraordinarias del superadmin sobre la titularidad de un tenant, identificando al responsable de la intervención, al tenant, a las cuentas afectadas, al momento del cambio y a su justificación.

## Requisitos no funcionales (RNF)

- **RNF-AUD-001** — Los registros de auditoría confirmados se mantienen protegidos frente a modificaciones o eliminaciones ordinarias de los usuarios del tenant y preservan la integridad de su historial.

- **RNF-AUD-002** — Los registros de auditoría y su acceso respetan el aislamiento entre tenants y las restricciones de consulta específicas de cada tipo de evento.

- **RNF-AUD-003** — Las marcas temporales de auditoría mantienen una referencia temporal consistente y permiten interpretar los eventos de sucursal en su zona horaria correspondiente.

- **RNF-AUD-004** — La trazabilidad de operaciones relacionadas mantiene coherencia con su confirmación o reversión y no presenta una operación revertida como si hubiera quedado confirmada.

## Reglas comerciales (RC)

No se identifican reglas comerciales nuevas exclusivas de la auditoría transversal; los cobros, modificaciones de contratación y sus historiales permanecen regulados en las áreas comerciales aprobadas.

## Pendientes de definición (PT)

- **PT-AUD-001** — Está pendiente establecer el catálogo exhaustivo de acciones y eventos auditables por módulo, diferenciando modificaciones relevantes, eventos de seguridad y consultas rutinarias.

- **PT-AUD-002** — Está pendiente determinar quiénes podrán consultar las auditorías operativas, de configuración y de contratación, sin modificar que solo el administrador principal consulta la auditoría de roles y permisos del tenant y que cada usuario puede consultar sus propios eventos de seguridad.

- **PT-AUD-003** — Está pendiente determinar si determinadas consultas de información sensible deberán generar eventos de auditoría y, en su caso, cuáles.

- **PT-AUD-004** — Está pendiente definir los periodos de retención y la eliminación o anonimización de registros de auditoría, incluyendo las excepciones legales y su relación con los 180 días de conservación operativa de los tenants terminados.

- **PT-AUD-005** — Está pendiente definir si habrá funciones de búsqueda, filtros, visualización o exportación de bitácoras operativas y qué permisos corresponderán a esas funciones.

- **PT-AUD-006** — Está pendiente precisar qué datos de las actuaciones pueden conservarse en las bitácoras sin exponer contraseñas, credenciales temporales, secretos de integración o información personal innecesaria.

- **PT-AUD-007** — Está pendiente establecer el tratamiento de intentos de modificación rechazados, operaciones revertidas e incidentes de infraestructura para distinguirlos de los cambios confirmados.

- **PT-AUD-008** — Está pendiente definir el mecanismo técnico de almacenamiento, protección, respaldo y verificación de integridad de las bitácoras, sin exigir por ahora una tecnología específica.

- **PT-AUD-009** — Está pendiente determinar el alcance de la consulta de las bitácoras del superadmin y qué información de sus intervenciones extraordinarias, si alguna, podrá visualizar el administrador principal del tenant afectado.

## Revisión de consistencia con las áreas aprobadas

- **Inventario y Bajas:** la auditoría transversal conserva la inmutabilidad de movimientos confirmados y la vinculación con correcciones; no habilita edición de movimientos históricos.
- **Ventas, Préstamos y Mantenimiento:** se conserva el historial de las operaciones y sus cierres sin añadir capacidades nuevas de cancelación o rectificación.
- **Carga CSV:** la trazabilidad de importaciones y sus movimientos sigue siendo la prevista en el catálogo de CSV, sin modificar su ejecución atómica.
- **Configuración y Multisucursal:** los eventos de cambio deben identificar su ámbito y sucursal cuando proceda, sin equiparar una ubicación interna con una sucursal.
- **Administración de usuarios:** se mantiene la consulta exclusiva del administrador principal sobre auditorías de roles y permisos y la consulta individual de eventos de seguridad de la propia cuenta.
- **Superadministración:** las actuaciones extraordinarias mantienen sus controles de justificación y verificación, sin conceder acceso ordinario indiscriminado a información de tenants.
- **Suscripciones:** las obligaciones de pago, reembolsos y conservación documental mantienen sus propias reglas; el presente catálogo solo establece trazabilidad transversal.

**Resultado de revisión:** no se identifican contradicciones críticas nuevas; permanece sin definir el acceso a otras clases de bitácoras y su plazo de conservación, por lo que esas capacidades no se consideran aprobadas.

## Control de duplicidades

Se conservan como requisitos vigentes de sus áreas originales, sin asignarles otro identificador ni contarlos nuevamente, entre otros: `RN-USU-039`, `RN-USU-040`, `RF-USU-023`, `RNF-INV-004`, `RNF-CSV-004`, `RNF-CFG-002`, `RNF-SAD-002` y `RF-SAD-005`.

Este documento formaliza las obligaciones comunes y registra los asuntos aún pendientes; no modifica las decisiones aprobadas en esos catálogos.
