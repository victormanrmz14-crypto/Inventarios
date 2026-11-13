# Ubicaciones internas — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene solo su identificador y su descripción autónoma; los PT indican decisiones no confirmadas.

## Reglas de negocio (RN)

- **RN-UBI-001** — Una ubicación interna identifica un espacio físico dentro de un establecimiento del tenant y no constituye por sí misma una sucursal independiente.

- **RN-UBI-002** — Cada ubicación interna pertenece exclusivamente al tenant que la registra y no puede utilizarse para acceder o asociar existencias de otro tenant.

- **RN-UBI-003** — La funcionalidad de ubicaciones internas está disponible aun cuando el tenant no tenga contratado el módulo adicional Multisucursal.

- **RN-UBI-004** — Cuando Multisucursal está contratado, las ubicaciones internas de una sucursal no constituyen existencias compartidas con las demás sucursales.

- **RN-UBI-005** — Cambiar la ubicación interna de existencias no representa por sí mismo una venta, devolución comercial, préstamo ni baja de inventario.

- **RN-UBI-006** — En abarrotes, el traslado de existencias entre ubicaciones internas del mismo establecimiento conserva la cantidad total registrada en el ámbito de inventario correspondiente.

- **RN-UBI-007** — En abarrotes, una reubicación interna no puede confirmar una salida desde el origen superior a las existencias aptas para dicha operación.

- **RN-UBI-008** — La reubicación física de una unidad con seguimiento individual conserva el identificador y el historial de esa unidad.

- **RN-UBI-009** — La asignación o modificación de una ubicación interna no elimina las restricciones de disponibilidad derivadas de préstamos, mantenimiento, caducidad, incidencias, desactivación u otras causas vigentes.

- **RN-UBI-010** — Los usuarios limitados solo pueden operar sobre ubicaciones y existencias comprendidas en la sucursal a la que están asignados cuando el tenant utiliza Multisucursal.

- **RN-UBI-011** — La retirada de Multisucursal no habilita operaciones ordinarias en ubicaciones de sucursales secundarias desactivadas y conserva las referencias históricas correspondientes.

- **RN-UBI-012** — Una reubicación interna confirmada conserva un registro histórico de origen y destino que no se sustituye mediante edición directa cuando requiere rectificación.

## Requisitos funcionales (RF)

- **RF-UBI-001** — El sistema permite a los usuarios autorizados registrar y consultar ubicaciones internas pertenecientes exclusivamente a su tenant sin exigir la contratación de Multisucursal.

- **RF-UBI-002** — El sistema permite consultar la ubicación interna registrada de las existencias o unidades físicas cuando ese dato se encuentre disponible en el seguimiento del inventario.

- **RF-UBI-003** — El sistema permite registrar en abarrotes traslados de existencias entre ubicaciones internas del mismo establecimiento sin modificar el total de existencias del establecimiento.

- **RF-UBI-004** — El sistema comprueba las existencias y restricciones vigentes en la ubicación de origen antes de confirmar una reubicación interna de abarrotes e impide que produzca cantidades negativas.

- **RF-UBI-005** — El sistema conserva el identificador de cada unidad física individual y su historial cuando cambia su ubicación interna.

- **RF-UBI-006** — El sistema mantiene activas las restricciones de disponibilidad de los productos o unidades aunque se registre una nueva ubicación interna.

- **RF-UBI-007** — El sistema separa las ubicaciones internas de cada sucursal y evita que una reubicación interna se utilice para transferir existencias entre sucursales distintas.

- **RF-UBI-008** — El sistema restringe las consultas y operaciones de ubicaciones de cada usuario limitado a su sucursal autorizada y permite a los administradores completos el alcance global previsto para el tenant.

- **RF-UBI-009** — El sistema bloquea las operaciones ordinarias sobre ubicaciones de sucursales secundarias después de descontratar Multisucursal y conserva sus registros para consultas históricas autorizadas y excepciones previamente aprobadas.

- **RF-UBI-010** — El sistema registra cada reubicación interna confirmada con ubicación de origen, ubicación de destino, existencias o unidades afectadas, responsable y fecha y hora, y mantiene trazables las rectificaciones posteriores.

## Requisitos no funcionales (RNF)

- **RNF-UBI-001** — El sistema aplica aislamiento multitenant a las ubicaciones internas y a las relaciones entre ubicación, producto, unidad, movimiento y sucursal cuando corresponda.

- **RNF-UBI-002** — La confirmación de una reubicación interna actualiza de manera atómica los registros relacionados con el origen, el destino y el movimiento para evitar cambios incompletos.

- **RNF-UBI-003** — Las reubicaciones concurrentes sobre las mismas existencias vuelven a validar el origen antes de confirmarse y evitan cantidades negativas o duplicación de efectos.

- **RNF-UBI-004** — Los registros confirmados de reubicación y su auditoría quedan protegidos frente a alteraciones ordinarias y permiten recuperar el resultado de un reenvío identificado sin ejecutar otra vez el movimiento.

## Reglas comerciales (RC)

- **RC-UBI-001** — La gestión básica de ubicaciones internas está incluida por defecto en los cinco giros y en los tres niveles de plan, mientras que la gestión de varias sucursales requiere el módulo adicional Multisucursal.

## Pendientes de definición (PT)

- **PT-UBI-001** — Está pendiente definir la estructura del catálogo de ubicaciones internas, sus datos obligatorios, los identificadores y la posible organización jerárquica de almacenes, zonas o estantes.

- **PT-UBI-002** — Está pendiente determinar si asignar una ubicación interna será obligatorio para algún giro o producto y cómo se representarán las existencias sin ubicación asignada.

- **PT-UBI-003** — Está pendiente definir la granularidad del seguimiento de existencias por ubicación interna según producto, lote, cantidad o unidad física y su correspondencia con las modalidades de inventario por giro.

- **PT-UBI-004** — Está pendiente decidir si los traslados internos expresamente previstos para abarrotes también estarán disponibles en biblioteca, farmacia, ferretería y electrónicos, y con qué restricciones específicas.

- **PT-UBI-005** — Está pendiente establecer las condiciones para editar, desactivar, reactivar o eliminar una ubicación interna que tenga existencias asociadas o referencias históricas.

- **PT-UBI-006** — Está pendiente precisar los permisos granulares para crear ubicaciones, modificarlas, consultar sus existencias y registrar o rectificar reubicaciones internas.

- **PT-UBI-007** — Está pendiente definir cómo se registrará la ubicación o custodia física de unidades prestadas, en mantenimiento o enviadas a un proveedor externo sin confundir esos estados con disponibilidad en almacén.

- **PT-UBI-008** — Está pendiente precisar la forma de consultar y evaluar existencias y mínimos cuando un producto utiliza simultáneamente varias ubicaciones internas dentro de una misma sucursal, respetando el control de stock ya aprobado.

- **PT-UBI-009** — Está pendiente definir el procedimiento de rectificación de reubicaciones internas por diferencias físicas, errores de ubicación o cantidades, manteniendo la inmutabilidad de movimientos confirmados.
