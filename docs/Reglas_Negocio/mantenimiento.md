# Mantenimiento de productos electrónicos — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

## Reglas de negocio (RN)

- **RN-MAN-001** — Cada intervención de mantenimiento de productos electrónicos se asocia a una unidad física identificada dentro del inventario de su tenant.

- **RN-MAN-002** — Una unidad electrónica con mantenimiento activo permanece indisponible para ventas y nuevos préstamos.

- **RN-MAN-003** — Una intervención de mantenimiento propio solo puede iniciarse después de asignar un técnico registrado a la intervención.

- **RN-MAN-004** — Una intervención de mantenimiento externo solo puede iniciarse después de identificar al proveedor responsable del servicio.

- **RN-MAN-005** — Los técnicos registrados para trabajos de mantenimiento son personas asociadas a las intervenciones y no adquieren por ese registro una cuenta de acceso al SaaS.

- **RN-MAN-006** — Cuando una garantía vigente tiene cobertura confirmada por el proveedor, la atención cubierta corresponde a dicho proveedor y no se sustituye por mantenimiento propio.

- **RN-MAN-007** — Cuando la cobertura de una garantía vigente está pendiente de confirmación, la unidad permanece indisponible y no puede iniciarse mantenimiento propio.

- **RN-MAN-008** — Cuando no existe cobertura de garantía confirmada y la decisión de cobertura ya fue resuelta, un administrador autorizado puede seleccionar mantenimiento propio o externo conforme a las condiciones aplicables de la garantía.

- **RN-MAN-009** — El registro básico de una garantía de productos electrónicos está disponible aunque el tenant no tenga contratado el módulo Mantenimiento.

- **RN-MAN-010** — El seguimiento del servicio de garantía ante el proveedor se gestiona dentro del SaaS únicamente cuando el módulo Mantenimiento está contratado, y de otro modo se realiza fuera de la plataforma.

- **RN-MAN-011** — Una unidad electrónica devuelta físicamente de un préstamo que continúa abierto por una incidencia puede ingresar a mantenimiento cuando el módulo está contratado, sin que ello cierre automáticamente el préstamo.

- **RN-MAN-012** — La finalización de un mantenimiento exige que una persona autorizada determine si la unidad es apta para volver a utilizarse.

- **RN-MAN-013** — El cierre de un mantenimiento no elimina otras restricciones vigentes de la unidad ni restablece por sí solo su disponibilidad para venta o préstamo.

- **RN-MAN-014** — Una unidad electrónica con una intervención de mantenimiento activa no puede darse de baja mientras esa intervención permanezca abierta.

- **RN-MAN-015** — El mantenimiento de una unidad vinculada a un producto desactivado puede concluirse como operación anterior pendiente sin habilitar nuevas operaciones ordinarias sobre ese producto.

- **RN-MAN-016** — Después de descontratar el módulo Mantenimiento, únicamente el administrador principal puede ejecutar cierres excepcionales indispensables de intervenciones anteriores sin iniciar intervenciones nuevas.

- **RN-MAN-017** — Las intervenciones de mantenimiento y los préstamos de una unidad conservan sus estados y restricciones por separado cuando una incidencia permite que coexistan temporalmente.

- **RN-MAN-018** — Una incidencia de una unidad electrónica, incluidos los daños observados, puede registrarse sin contratar Mantenimiento, pero ese registro no habilita la gestión de una intervención dentro del módulo descontratado.

## Requisitos funcionales (RF)

- **RF-MAN-001** — El sistema permite registrar y consultar intervenciones de mantenimiento asociadas a unidades físicas identificadas cuando el módulo Mantenimiento de productos electrónicos está contratado y el usuario tiene autorización.

- **RF-MAN-002** — El sistema permite asignar a cada intervención de mantenimiento propio un técnico registrado sin credenciales del SaaS y bloquea el inicio de la intervención mientras no exista dicha asignación.

- **RF-MAN-003** — El sistema permite asociar un proveedor identificado a cada intervención externa y bloquea su inicio cuando no se ha registrado el proveedor responsable.

- **RF-MAN-004** — El sistema registra el estado de confirmación de cobertura de garantía y mantiene bloqueado el mantenimiento propio y la disponibilidad de la unidad mientras la cobertura permanezca pendiente.

- **RF-MAN-005** — El sistema vincula la intervención cubierta por una garantía vigente con su proveedor cuando este confirma la cobertura, impidiendo sustituirla por una intervención propia.

- **RF-MAN-006** — El sistema permite a un administrador autorizado elegir entre mantenimiento propio y externo cuando la decisión de cobertura de garantía ya está resuelta y no existe cobertura confirmada que obligue a la atención del proveedor.

- **RF-MAN-007** — El sistema permite registrar y consultar información básica de garantías de unidades electrónicas sin exigir la contratación del módulo Mantenimiento y habilita el seguimiento del servicio ante proveedores solo cuando dicho módulo está contratado.

- **RF-MAN-008** — El sistema mantiene indisponibles para venta y nuevos préstamos las unidades con mantenimiento activo y conserva todas las restricciones adicionales que también las afecten.

- **RF-MAN-009** — El sistema permite iniciar mantenimiento sobre una unidad físicamente devuelta cuya operación de préstamo sigue abierta por una incidencia, sin cerrar ese préstamo de forma automática.

- **RF-MAN-010** — El sistema permite finalizar una intervención anterior de mantenimiento vinculada a un producto desactivado, sin habilitar intervenciones ordinarias nuevas sobre ese producto.

- **RF-MAN-011** — El sistema registra al finalizar el mantenimiento la determinación de aptitud realizada por una persona autorizada y solo recupera la disponibilidad de la unidad cuando ninguna otra restricción vigente impide su uso.

- **RF-MAN-012** — El sistema impide registrar la baja de una unidad electrónica mientras mantenga activa una intervención de mantenimiento.

- **RF-MAN-013** — El sistema permite únicamente al administrador principal efectuar cierres excepcionales de intervenciones anteriores después de descontratar el módulo Mantenimiento, sin habilitar nuevas intervenciones.

- **RF-MAN-014** — El sistema registra los cambios relevantes de intervenciones, asignaciones, decisiones de cobertura y cierres de mantenimiento con autoría, momento, tenant y sucursal cuando aplique.

## Requisitos no funcionales (RNF)

- **RNF-MAN-001** — Las confirmaciones de inicio y cierre de mantenimiento actualizan de forma atómica los estados de la intervención y las restricciones de disponibilidad relacionadas, sin dejar cambios parciales confirmados.

- **RNF-MAN-002** — Las operaciones concurrentes sobre una misma unidad vuelven a verificar sus restricciones al confirmar y evitan que una venta, un préstamo o una baja incompatibles se completen durante un mantenimiento activo.

- **RNF-MAN-003** — La repetición de una misma solicitud identificada de mantenimiento conserva un único efecto confirmado y permite consultar su resultado tras una interrupción de conexión.

- **RNF-MAN-004** — El sistema conserva el historial de cambios y cierres de mantenimiento protegido contra alteraciones ordinarias y registra las actuaciones relevantes para su auditoría.

## Reglas comerciales (RC)

- **RC-MAN-001** — El módulo Mantenimiento se comercializa como módulo adicional exclusivo del giro de productos electrónicos y ofrece las mismas funciones operativas en los niveles Básico, Intermedio y Superior.

- **RC-MAN-002** — Las operaciones ordinarias del módulo Mantenimiento se habilitan únicamente durante una contratación vigente y pagada, y su retirada al finalizar el periodo contratado conserva exclusivamente los cierres excepcionales autorizados de obligaciones previas.

- **RC-MAN-003** — La falta de contratación del módulo Mantenimiento no elimina las funciones básicas de garantías ni el registro de incidencias que el giro de productos electrónicos incluye por defecto.

## Pendientes de definición (PT)

- **PT-MAN-001** — Permanece pendiente definir los campos obligatorios y los estados de una intervención de mantenimiento propio o externo, incluidos los datos de diagnóstico, ejecución y cierre que resulten necesarios.

- **PT-MAN-002** — Permanece pendiente definir qué rol o permiso granular autoriza la determinación de aptitud al finalizar un mantenimiento y qué evidencia debe registrarse para respaldarla.

- **PT-MAN-003** — Permanece pendiente definir cómo se registra la ubicación o la custodia física de una unidad durante un mantenimiento externo y su eventual recepción, sin presuponer movimientos de baja del inventario.

- **PT-MAN-004** — Permanece pendiente establecer el procedimiento de confirmación o rechazo de cobertura por parte del proveedor y el tratamiento de solicitudes de garantía que queden sin respuesta.

- **PT-MAN-005** — Permanece pendiente definir los datos identificativos obligatorios de los técnicos de mantenimiento y las reglas para registrar su participación en varias intervenciones.

- **PT-MAN-006** — Permanece pendiente especificar el alcance de las intervenciones permitidas como cierre excepcional después de descontratar Mantenimiento, sin habilitar nuevas operaciones ordinarias.
