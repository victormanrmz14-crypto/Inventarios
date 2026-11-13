# Reportes — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene únicamente su identificador y una descripción autónoma; los PT identifican asuntos todavía no definidos y no constituyen decisiones aprobadas.

## Reglas de negocio (RN)

- **RN-REP-001** — Los reportes generales del tenant abarcan inventario, existencias y movimientos, y pueden incorporar información de módulos adicionales únicamente cuando su consulta esté permitida por la contratación y los permisos vigentes o por las excepciones históricas autorizadas.

- **RN-REP-002** — Los reportes permiten consultar la situación actual y reconstruir información histórica para una fecha de corte o un periodo seleccionado.

- **RN-REP-003** — La autorización para visualizar reportes y la autorización para exportarlos son permisos independientes.

- **RN-REP-004** — La visualización y exportación de un reporte respetan los módulos, las funcionalidades, los registros y los ámbitos de sucursal a los que el usuario tiene acceso.

- **RN-REP-005** — Un usuario sin permiso para consultar costos tampoco puede obtener importes de costo ni indicadores que permitan deducirlos a través de reportes, totales, comparaciones o archivos exportados.

- **RN-REP-006** — Los reportes históricos ofrecen la consulta de los datos según quedaron registrados en su momento y la consulta de sus efectos después de las correcciones posteriores.

- **RN-REP-007** — Los reportes sobre movimientos corregidos conservan la distinción entre movimiento original, movimiento correctivo vinculado y efecto neto correspondiente.

- **RN-REP-008** — Los productos, lotes o unidades desactivados o dados de baja permanecen representados en las consultas históricas pertinentes sin confundirse con las existencias disponibles actuales.

- **RN-REP-009** — Los usuarios limitados solo pueden consultar y exportar datos de la sucursal que tienen asignada cuando el tenant utiliza Multisucursal.

- **RN-REP-010** — Los reportes consolidados de varias sucursales solo están disponibles para usuarios cuyo alcance autorizado comprende todas las sucursales incluidas en el resultado.

- **RN-REP-011** — La información personal de lectores o destinatarios de préstamos se presenta de forma agregada cuando el reporte no requiere identificar individualmente a las personas.

- **RN-REP-012** — La consulta de detalles personales de lectores o destinatarios de préstamos mediante reportes exige un permiso específico y una finalidad justificada.

- **RN-REP-013** — Los reportes se generan a petición de usuarios autorizados y no mediante ejecuciones periódicas programadas como función del producto.

- **RN-REP-014** — Las existencias físicas registradas y las existencias disponibles se distinguen en los reportes de stock cuando ambas magnitudes resultan pertinentes.

- **RN-REP-015** — Los historiales de funcionalidades perdidas por una reducción de nivel o por la descontratación de un módulo extra solo pueden consultarlos el administrador principal y los administradores completos, sin reactivar operaciones ordinarias de esas funcionalidades.

- **RN-REP-016** — Durante la suspensión por impago se permite visualizar y descargar reportes existentes o generados bajo demanda dentro de los permisos del usuario, pero al terminar la suscripción se pierde el acceso directo a los reportes operativos.

## Requisitos funcionales (RF)

- **RF-REP-001** — El sistema ofrece a los usuarios autorizados reportes generales de inventario, existencias y movimientos, y reportes de los módulos adicionales a los que el tenant tenga acceso permitido.

- **RF-REP-002** — El sistema permite solicitar reportes del estado actual, de una fecha histórica de corte y de un periodo histórico seleccionado.

- **RF-REP-003** — El sistema permite consultar la información histórica tal como se registró originalmente o con los efectos de las correcciones efectuadas después del momento consultado.

- **RF-REP-004** — El sistema presenta en los reportes de movimientos corregidos las referencias al movimiento original y al correctivo, así como el efecto neto resultante.

- **RF-REP-005** — El sistema permite incluir en las consultas históricas registros de productos, lotes y unidades que posteriormente fueron desactivados o dados de baja, mostrando su estado correspondiente.

- **RF-REP-006** — El sistema comprueba de manera independiente los permisos para visualizar y para exportar cada reporte antes de ejecutar la acción solicitada.

- **RF-REP-007** — El sistema permite exportar los reportes autorizados en formatos CSV, PDF y XLSX, conservando los filtros y restricciones de acceso que correspondan a la consulta.

- **RF-REP-008** — El sistema excluye de las pantallas, indicadores, agregados y exportaciones los costos y valores derivados de costos cuando el usuario carece del permiso correspondiente.

- **RF-REP-009** — El sistema limita los reportes de usuarios con acceso restringido a la sucursal autorizada y permite consolidaciones entre sucursales únicamente cuando el usuario está autorizado para todos los ámbitos comprendidos.

- **RF-REP-010** — El sistema ofrece vistas de información agregada de lectores o destinatarios de préstamos y solo muestra detalles personales cuando el usuario dispone de la autorización específica correspondiente.

- **RF-REP-011** — El sistema genera reportes cuando un usuario autorizado los solicita y no ofrece generación recurrente automática de reportes.

- **RF-REP-012** — El sistema muestra por separado las existencias físicas y las disponibles en los reportes de stock cuando corresponda al tipo de consulta seleccionado.

- **RF-REP-013** — El sistema permite al administrador principal y a los administradores completos consultar el historial autorizado de módulos extra descontratados o de funcionalidades retiradas por cambios de nivel, sin habilitar nuevas operaciones en ellos.

- **RF-REP-014** — El sistema mantiene la visualización y exportación autorizadas de reportes durante la suspensión por impago e impide el acceso directo a los reportes operativos cuando la suscripción está terminada.

- **RF-REP-015** — El sistema presenta los reportes operativos incluidos en el nivel Básico y habilita los análisis de tendencias, comparaciones e indicadores avanzados a partir del nivel Intermedio.

- **RF-REP-016** — El sistema habilita en el nivel Superior un dashboard compartido personalizable y análisis combinados de información general y de módulos adicionales contratados, reservando la personalización al administrador principal y a los administradores completos.

- **RF-REP-017** — El sistema conserva las configuraciones de dashboard que dejen de estar disponibles tras una reducción de nivel sin mostrarlas como funcionalidades activas hasta recuperar una contratación que las incluya.

## Requisitos no funcionales (RNF)

- **RNF-REP-001** — La obtención y exportación de reportes aplica aislamiento estricto entre tenants y evita incorporar registros de otros negocios en consultas, agregados o archivos.

- **RNF-REP-002** — Los controles de acceso y de visibilidad de costos se aplican también a cálculos intermedios, totales, columnas y archivos exportados, sin exponer información restringida por vías indirectas.

- **RNF-REP-003** — Los resultados históricos mantienen correspondencia con los movimientos confirmados y sus correcciones vinculadas, sin tratar movimientos fallidos o revertidos como operaciones efectivas.

- **RNF-REP-004** — El sistema vuelve a verificar los permisos y el estado de la suscripción antes de entregar un reporte o una exportación, incluso cuando la consulta se preparó antes de un cambio de autorización.

- **RNF-REP-005** — Las fechas y horas de los reportes mantienen una referencia temporal consistente entre sucursales de distintas zonas horarias y distinguen la presentación local de los eventos cuando corresponde.

## Reglas comerciales (RC)

- **RC-REP-001** — Los reportes operativos generales y sus exportaciones CSV, PDF y XLSX están incluidos por defecto en los cinco giros y en los tres niveles de plan sin contratación independiente.

- **RC-REP-002** — El nivel Intermedio incorpora capacidades de análisis de tendencias, comparaciones e indicadores avanzados adicionales a los reportes operativos del nivel Básico.

- **RC-REP-003** — El nivel Superior incorpora un dashboard compartido personalizable y análisis combinados entre áreas permitidas, sin modificar las funcionalidades operativas esenciales ni habilitar datos de módulos extra no contratados.

## Pendientes de definición (PT)

- **PT-REP-001** — Está pendiente especificar el catálogo concreto de reportes, indicadores, columnas, filtros y agrupaciones para cada giro y módulo, sin suponer reportes operativos o financieros no acordados.

- **PT-REP-002** — Está pendiente definir el método de reconstrucción de saldos y estados históricos, incluidos los criterios de fecha efectiva, fecha de registro y correcciones posteriores para cada tipo de movimiento.

- **PT-REP-003** — Está pendiente delimitar qué indicadores y agregados se consideran derivados de costos y cómo se protegen en los casos donde otros datos públicos podrían permitir inferirlos.

- **PT-REP-004** — Está pendiente definir la agregación de existencias físicas, disponibles y en tránsito para reportes generales, por sucursal o por ubicación interna, en coordinación con los pendientes de Control de stock y Multisucursal.

- **PT-REP-005** — Está pendiente definir los campos personales visibles, el permiso granular específico y las condiciones que justifican la consulta identificada de lectores o destinatarios de préstamos.

- **PT-REP-006** — Está pendiente concretar el diseño de los archivos CSV, PDF y XLSX, los límites de tamaño, las convenciones de formato y el manejo de exportaciones voluminosas.

- **PT-REP-007** — Está pendiente delimitar los indicadores avanzados de Intermedio y las opciones de personalización y análisis combinado del dashboard de Superior, sin atribuir capacidades adicionales no aprobadas.

- **PT-REP-008** — Está pendiente precisar qué zona horaria utiliza cada filtro de periodo y cada consolidación de varias sucursales cuando las sucursales tienen husos horarios diferentes.

- **PT-REP-009** — Está pendiente establecer las modalidades de entrega o conservación temporal de archivos exportados y las restricciones aplicables a descargas diferidas, sin asumir programación recurrente de reportes.
