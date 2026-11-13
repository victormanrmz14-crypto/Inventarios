# Área 24 — Notificaciones y avisos

**Versión:** 1.0  
**Estado:** Pendiente de aprobación.  
**Alcance:** Avisos internos de stock y comunicaciones comerciales de suscripción; las alertas por caducidad y las comunicaciones de incidentes de seguridad continúan pendientes de definición.

Los identificadores ya presentes en áreas aprobadas se reproducen sin reemplazarlos ni contabilizarlos como requisitos nuevos; los identificadores `PT-NOT` representan pendientes nuevos y no constituyen funcionalidades aprobadas.

## Reglas de negocio (RN)

- **RN-STO-009** — Las alertas por nivel mínimo y las alertas por existencias en cero se distinguen como condiciones diferentes de control de stock.

- **RN-STO-010** — Las alertas de existencias son informativas y no impiden por sí mismas realizar una operación que cumpla las demás reglas del inventario.

- **RN-STO-011** — Las alertas de stock se muestran visualmente dentro de la aplicación y se comunican mediante notificaciones internas del SaaS.

- **RN-STO-012** — Una misma condición de alerta no provoca notificaciones internas repetidas mientras permanezca activa y vuelve a habilitar una notificación cuando la condición se resuelve y aparece nuevamente.

- **RN-STO-013** — La desactivación de un producto impide generar nuevas notificaciones de reposición para ese producto y conserva su historial de alertas.

- **RN-STO-014** — El alcance de consulta de existencias y alertas respeta los permisos funcionales y la sucursal asignada al usuario limitado cuando el tenant utiliza Multisucursal.

- **RN-SUS-023** — Únicamente el administrador principal recibe las notificaciones comerciales de pago, renovación, suspensión, reactivación, precios y conservación del tenant.

## Requisitos funcionales (RF)

- **RF-STO-006** — El sistema identifica y muestra las situaciones de existencias en cero aunque el producto no tenga definido un mínimo de stock.

- **RF-STO-008** — El sistema presenta las alertas de stock mediante indicadores visuales y notificaciones internas de la aplicación.

- **RF-STO-009** — El sistema notifica la entrada en una condición de alerta, evita emitir avisos repetidos mientras esa condición continúe y permite una nueva notificación después de la recuperación y la aparición de otra condición de alerta.

- **RF-STO-011** — El sistema suspende las nuevas notificaciones de reposición de productos desactivados y permite consultar su historial de alertas conservado.

- **RF-SUS-018** — El sistema envía al administrador principal avisos por correo electrónico a los 30 y 7 días anteriores al fin del plazo de conservación y presenta notificaciones internas cuando exista acceso a la cuenta.

- **RF-SUS-019** — El sistema comunica al administrador principal por correo electrónico y notificación interna los pagos confirmados o fallidos, renovaciones próximas, suspensiones, reactivaciones y cambios de contratación o precio.

- **RF-SUS-025** — El sistema presenta al administrador principal los avisos de cambios de precio antes de su aplicación y los incorpora únicamente en la renovación afectada conforme a la regla comercial vigente.

## Requisitos no funcionales (RNF)

- **RNF-STO-002** — Las actualizaciones concurrentes o los reenvíos de una operación no generan efectos de stock duplicados ni notificaciones repetidas de una misma transición de alerta.

- **RNF-STO-003** — La información de existencias, mínimos, alertas y su historial se aísla por tenant y respeta las restricciones de acceso por sucursal cuando corresponde.

- **RNF-SUS-002** — El procesamiento de confirmaciones, notificaciones repetidas y reintentos de cobro es idempotente y no genera activaciones ni cargos duplicados por la misma obligación.

## Reglas comerciales (RC)

No se identifican reglas comerciales nuevas exclusivas de esta área; se mantienen las condiciones comerciales de suscripciones y planes previamente aprobadas.

## Pendientes de definición (PT)

- **PT-STO-005** — Está pendiente precisar quién puede configurar mínimos y bases de alerta, y qué destinatarios reciben las notificaciones internas según rol, permiso y sucursal.

- **PT-STO-007** — Está pendiente concretar la conservación, visualización y depuración del historial de alertas, especialmente cuando un producto cambia de estado o el tenant termina su suscripción.

- **PT-STO-008** — Está pendiente definir el detalle operativo de las notificaciones internas de stock, su estado de lectura y su agrupación visual, sin incorporar canales externos no aprobados.

- **PT-CAD-005** — Está pendiente definir si el sistema ofrecerá alertas anticipadas por próximos vencimientos y, en su caso, los plazos, destinatarios y medios de notificación, sin confundirlas con las alertas por stock mínimo.

- **PT-SUS-007** — Está pendiente definir la anticipación de los avisos preventivos de renovación, fin de gracia y aumento de precios, sin alterar los avisos ya fijados a 30 y 7 días del fin de la conservación.

- **PT-SEG-009** — Está pendiente establecer el procedimiento de respuesta ante incidentes de seguridad y exposición de datos, incluidas responsabilidades de investigación, escalamiento, conservación de evidencias y comunicaciones que resulten aplicables.

- **PT-NOT-001** — Está pendiente decidir si las notificaciones internas de distintas áreas compartirán una bandeja transversal o se consultarán únicamente en las pantallas de cada módulo, sin añadir nuevos eventos de notificación.

- **PT-NOT-002** — Está pendiente definir si los avisos de diferentes áreas tendrán prioridad, agrupación o mecanismos de búsqueda comunes y, en su caso, sus criterios, sin alterar las condiciones de emisión ya aprobadas.

- **PT-NOT-003** — Está pendiente definir el tratamiento de fallos en el envío de correos de suscripción, incluidos los reintentos técnicos, el registro del resultado y los mecanismos de seguimiento, sin asumir que el mensaje fue entregado.

- **PT-NOT-004** — Está pendiente definir el contenido mínimo, la presentación y las plantillas de las notificaciones comerciales e internas, sin incluir datos sensibles que no correspondan al destinatario autorizado.

- **PT-NOT-005** — Está pendiente determinar si los usuarios podrán marcar, archivar o silenciar avisos operativos y bajo qué restricciones, sin considerar opcional la emisión de los avisos comerciales ya confirmados.

- **PT-NOT-006** — Está pendiente precisar la consulta y permanencia de notificaciones internas durante la suspensión y terminación de una suscripción, respetando que la suspensión solo habilita consultas autorizadas y la terminación no devuelve acceso operativo.

## Comprobación de coherencia

Las notificaciones de stock son internas y se sujetan a permisos de producto y sucursal; las comerciales se comunican únicamente al administrador principal dentro del SaaS y por correo electrónico; los avisos de eliminación a los 30 y 7 días anteriores al fin de la conservación tienen plazo ya fijado, mientras que otros plazos preventivos no están definidos.

Los avisos contextuales de prescripción farmacéutica ya pertenecen al área Prescripciones médicas y no se interpretan como notificaciones automáticas; las posibles alertas anticipadas de caducidad no se incluyen entre las funcionalidades confirmadas.

No se han detectado incompatibilidades funcionales nuevas con las áreas aprobadas; continúa pendiente de resolver la colisión previa del prefijo `PRE` entre Préstamos y Prescripciones médicas durante la consolidación global.

## Control de duplicidades

Los requisitos de las áreas Control de stock y Suscripciones incluidos aquí son referencias vigentes y no se sumarán una segunda vez en el catálogo consolidado; los pendientes heredados conservan sus identificadores originales y únicamente `PT-NOT-001` a `PT-NOT-006` son entradas nuevas.
