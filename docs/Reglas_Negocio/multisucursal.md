# Multisucursal — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Pendiente de aprobación.

Cada entrada contiene únicamente su identificador y una descripción autónoma; los PT representan definiciones aún no confirmadas.

## Reglas de negocio (RN)

- **RN-MSU-001** — Cada tenant que utiliza Multisucursal mantiene un catálogo de productos común para todas sus sucursales, sin crear un catálogo independiente por establecimiento.

- **RN-MSU-002** — Las existencias físicas situadas en una sucursal pertenecen al ámbito local de esa sucursal y no constituyen existencias disponibles de otra.

- **RN-MSU-003** — Las ubicaciones internas de cada sucursal forman parte del ámbito físico de esa sucursal y no sustituyen la identificación de la sucursal propietaria de sus existencias.

- **RN-MSU-004** — Al habilitar Multisucursal por primera vez para un tenant que ya tiene existencias registradas, las existencias previas se asignan a su sucursal principal sin registrar movimientos históricos ficticios.

- **RN-MSU-005** — Las operaciones ordinarias que utilizan existencias se realizan contra el inventario de la sucursal correspondiente y no consumen directamente existencias locales de otra sucursal.

- **RN-MSU-006** — Para utilizar físicamente existencias en una sucursal distinta de su origen es necesario completar su traslado entre sucursales antes de ejecutar una operación ordinaria que dependa de ellas.

- **RN-MSU-007** — Un traslado entre sucursales distingue las etapas de salida desde el origen, tránsito y recepción en el destino.

- **RN-MSU-008** — Las existencias despachadas en un traslado permanecen registradas como patrimonio físico del tenant durante el tránsito y no están disponibles para operaciones ordinarias en ninguna de las dos sucursales.

- **RN-MSU-009** — Las existencias recibidas en el destino pasan al inventario local de esa sucursal y solo se consideran disponibles cuando no tienen otras restricciones vigentes.

- **RN-MSU-010** — La autorización para despachar un traslado y la autorización para recibirlo son permisos granulares distintos.

- **RN-MSU-011** — Un usuario limitado tiene asignada como máximo una sucursal y solo puede realizar operaciones ordinarias y consultar información de las sucursales y funcionalidades que tiene autorizadas.

- **RN-MSU-012** — El administrador principal y los administradores completos del tenant pueden acceder a todas sus sucursales, sin que ello les otorgue facultades comerciales reservadas al administrador principal.

- **RN-MSU-013** — Un usuario limitado autorizado en la sucursal de origen puede despachar un traslado y otro usuario limitado autorizado en la sucursal de destino puede registrar la recepción, sin necesitar acceso simultáneo a ambas sucursales.

- **RN-MSU-014** — La devolución de un préstamo debe registrarse en la misma sucursal en la que se originó el préstamo mientras Multisucursal permanezca contratado.

- **RN-MSU-015** — La devolución comercial de una venta debe registrarse en la misma sucursal en la que se originó la venta mientras Multisucursal permanezca contratado.

- **RN-MSU-016** — La recepción de un traslado puede ser parcial y toda diferencia de recepción debe conservar una justificación y quedar vinculada al traslado correspondiente.

- **RN-MSU-017** — Al dejar de estar contratado Multisucursal, solo la sucursal principal conserva habilitadas las operaciones ordinarias y las sucursales secundarias quedan inactivas para esas operaciones.

- **RN-MSU-018** — La retirada de Multisucursal conserva el historial y las existencias identificadas de las sucursales secundarias, sin trasladarlas automáticamente a la sucursal principal ni habilitarlas para operaciones ordinarias.

- **RN-MSU-019** — Después de retirar Multisucursal, únicamente el administrador principal puede realizar los cierres excepcionales de préstamos y devoluciones comerciales originados en sucursales secundarias y resolver los traslados pendientes permitidos.

- **RN-MSU-020** — Después de retirar Multisucursal, únicamente el administrador principal puede registrar el movimiento físico excepcional de existencias conservadas en sucursales secundarias hacia la sucursal principal, respetando las restricciones de inventario y la trazabilidad.

- **RN-MSU-021** — Un usuario limitado asignado a una sucursal secundaria conserva su cuenta y su condición de usuario activo tras retirar Multisucursal, pero carece de acceso operativo hasta que un administrador autorizado lo reasigne expresamente a la sucursal principal o cambie su situación.

- **RN-MSU-022** — Cada sucursal utiliza su zona horaria local para presentar sus eventos y los eventos generales del tenant utilizan la zona horaria de su sucursal principal, manteniendo una referencia temporal consistente.

## Requisitos funcionales (RF)

- **RF-MSU-001** — El sistema permite gestionar varias sucursales de un mismo tenant cuando Multisucursal está contratado, manteniendo un catálogo de productos compartido y existencias físicas diferenciadas por sucursal.

- **RF-MSU-002** — El sistema identifica una sucursal principal para el tenant y muestra las existencias locales por sucursal sin tratarlas como inventario disponible indistintamente en todas ellas.

- **RF-MSU-003** — El sistema asigna a la sucursal principal las existencias registradas antes de la primera habilitación de Multisucursal sin generar movimientos de inventario retroactivos o ficticios.

- **RF-MSU-004** — El sistema vincula cada ubicación interna con la sucursal que corresponda y mantiene separadas las existencias de distintas sucursales aun cuando utilicen un catálogo de productos común.

- **RF-MSU-005** — El sistema permite iniciar un traslado autorizado entre una sucursal de origen y otra de destino, identificando las existencias o unidades y manteniendo su relación con ambas sucursales.

- **RF-MSU-006** — El sistema permite registrar el despacho de un traslado desde la sucursal de origen, disminuye su stock local y registra las existencias despachadas como en tránsito, sin volverlas disponibles en el destino antes de su recepción.

- **RF-MSU-007** — El sistema permite confirmar la recepción de existencias trasladadas en la sucursal de destino, actualiza las cantidades locales y aplica todas las restricciones vigentes para determinar su disponibilidad.

- **RF-MSU-008** — El sistema permite recepciones parciales de traslados, conserva la cantidad despachada, la recibida y la pendiente, y exige justificar cualquier diferencia registrada durante la recepción.

- **RF-MSU-009** — El sistema comprueba por separado los permisos de despacho en origen y recepción en destino y permite que esas acciones sean realizadas por usuarios limitados distintos autorizados cada uno en su única sucursal.

- **RF-MSU-010** — El sistema limita a una sola sucursal la asignación operativa de cada usuario limitado y permite al administrador principal y a los administradores completos consultar y operar en todas las sucursales del tenant.

- **RF-MSU-011** — El sistema asocia cada venta y préstamo a su sucursal de origen e impide registrar devoluciones comerciales o de préstamos en sucursales distintas mientras Multisucursal está contratado.

- **RF-MSU-012** — El sistema deshabilita las operaciones ordinarias de las sucursales secundarias al terminar la contratación de Multisucursal y conserva sus existencias, sus ubicaciones internas y sus historiales para los accesos autorizados.

- **RF-MSU-013** — El sistema permite exclusivamente al administrador principal resolver de forma excepcional préstamos, devoluciones comerciales y traslados pendientes de sucursales secundarias después de retirar Multisucursal, sin iniciar nuevas operaciones ordinarias en ellas.

- **RF-MSU-014** — El sistema permite exclusivamente al administrador principal registrar traslados físicos excepcionales de existencias desde sucursales secundarias inactivas a la sucursal principal y mantiene los movimientos y sus responsables en el historial.

- **RF-MSU-015** — El sistema mantiene activas y contabilizables las cuentas de usuarios limitados asignados a sucursales secundarias tras retirar Multisucursal, pero bloquea sus operaciones hasta que un administrador autorizado los reasigne o desactive.

- **RF-MSU-016** — El sistema registra las etapas de los traslados, las recepciones parciales, sus diferencias justificadas y las intervenciones extraordinarias con usuario responsable, fecha y hora, tenant, sucursales implicadas y movimientos relacionados.

- **RF-MSU-017** — El sistema presenta los eventos de cada sucursal en su zona horaria y los eventos generales en la zona de la sucursal principal, preservando una referencia temporal común en los registros.

## Requisitos no funcionales (RNF)

- **RNF-MSU-001** — El sistema impide accesos cruzados entre tenants y hace cumplir en todas las consultas y operaciones los permisos de sucursal correspondientes a cada usuario.

- **RNF-MSU-002** — El despacho y cada recepción confirmable de un traslado actualizan de manera atómica los registros relacionados con cantidades, tránsito y sucursales, sin dejar movimientos confirmados parcialmente por fallos técnicos.

- **RNF-MSU-003** — El sistema controla las solicitudes concurrentes y repetidas de despacho y recepción para que ninguna existencia sea despachada o recibida dos veces, ni produzca stock local negativo.

- **RNF-MSU-004** — Los registros confirmados de traslados y de intervenciones excepcionales conservan trazabilidad e integridad frente a edición o eliminación ordinaria por usuarios del tenant.

- **RNF-MSU-005** — El almacenamiento y consulta de eventos entre distintas zonas horarias permiten reconstruir su orden temporal real sin depender de la hora local presentada en cada sucursal.

## Reglas comerciales (RC)

- **RC-MSU-001** — Multisucursal es un módulo adicional contratable por los tenants de los cinco giros y la gestión básica de ubicaciones internas permanece incluida sin necesidad de contratarlo.

- **RC-MSU-002** — El precio de Multisucursal es una tarifa fija por tenant que puede variar según el giro, pero no según la cantidad de sucursales ni el nivel base contratado.

- **RC-MSU-003** — La operación ordinaria en varias sucursales se habilita únicamente mientras Multisucursal está contratado y el tenant conserva acceso operativo conforme al estado de su suscripción.

## Pendientes de definición (PT)

- **PT-MSU-001** — Está pendiente definir los datos obligatorios del catálogo de sucursales, sus identificadores, las condiciones para designar o cambiar la sucursal principal y las validaciones de domicilio y zona horaria.

- **PT-MSU-002** — Está pendiente determinar las condiciones de creación, edición, desactivación y reactivación de sucursales, particularmente cuando mantienen existencias o préstamos, ventas y traslados pendientes.

- **PT-MSU-003** — Está pendiente definir el tratamiento y los estados finales de los traslados cuando se registran faltantes o sobrantes, una recepción parcial o una diferencia justificada que no se resuelve.

- **PT-MSU-004** — Está pendiente detallar el procedimiento físico y documental para resolver traslados pendientes y trasladar existencias de sucursales secundarias inactivas a la principal tras descontratar Multisucursal.

- **PT-MSU-005** — Está pendiente establecer si la recontratación de Multisucursal reactiva las sucursales secundarias conservadas automáticamente o requiere autorización y validaciones específicas antes de reanudar sus operaciones.

- **PT-MSU-006** — Está pendiente precisar los permisos granulares adicionales para administrar sucursales, consultar información por sucursal, gestionar traslados, registrar diferencias y ejecutar correcciones autorizadas, sin modificar los permisos ya separados de despacho y recepción.

- **PT-MSU-007** — Está pendiente resolver cómo se agregan las existencias, los mínimos y las alertas entre sucursales y ubicaciones internas para reportes autorizados, sin mezclar cantidades locales con existencias en tránsito.

- **PT-MSU-008** — Está pendiente determinar el tratamiento de usuarios asignados a sucursales secundarias cuando Multisucursal vuelve a contratarse, sin reasignarlos o reactivarles permisos de manera no autorizada.
