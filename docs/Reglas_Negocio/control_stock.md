# Control de stock — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene únicamente su identificador y una descripción autónoma; los PT identifican decisiones que todavía no están confirmadas.

## Reglas de negocio (RN)

- **RN-STO-001** — Cada producto del tenant puede tener configurado un nivel mínimo general de existencias para su control de stock.

- **RN-STO-002** — El tenant puede establecer mínimos locales adicionales por ubicación interna o sucursal, cuando ese ámbito exista y corresponda al producto.

- **RN-STO-003** — Los mínimos generales y los mínimos locales se evalúan independientemente, sin sustituirse unos por otros.

- **RN-STO-004** — El stock físico registrado y el stock disponible para operar se presentan como magnitudes distintas, aunque se refieran al mismo producto.

- **RN-STO-005** — La disponibilidad de existencias considera todas las restricciones aplicables al producto, lote o unidad y no equivale automáticamente a su cantidad física registrada.

- **RN-STO-006** — La base de evaluación de alertas por producto puede configurarse sobre existencias físicas, existencias disponibles o ambas.

- **RN-STO-007** — No se genera una alerta por nivel mínimo bajo en un ámbito que no tenga configurado el mínimo correspondiente.

- **RN-STO-008** — La ausencia de un mínimo configurado no impide generar una alerta de existencias en cero.

- **RN-STO-009** — Las alertas por nivel mínimo y las alertas por existencias en cero se distinguen como condiciones diferentes de control de stock.

- **RN-STO-010** — Las alertas de existencias son informativas y no impiden por sí mismas realizar una operación que cumpla las demás reglas del inventario.

- **RN-STO-011** — Las alertas de stock se muestran visualmente dentro de la aplicación y se comunican mediante notificaciones internas del SaaS.

- **RN-STO-012** — Una misma condición de alerta no provoca notificaciones internas repetidas mientras permanezca activa y vuelve a habilitar una notificación cuando la condición se resuelve y aparece nuevamente.

- **RN-STO-013** — La desactivación de un producto impide generar nuevas notificaciones de reposición para ese producto y conserva su historial de alertas.

- **RN-STO-014** — El alcance de consulta de existencias y alertas respeta los permisos funcionales y la sucursal asignada al usuario limitado cuando el tenant utiliza Multisucursal.

## Requisitos funcionales (RF)

- **RF-STO-001** — El sistema permite a usuarios autorizados consultar y establecer el mínimo general de cada producto del tenant para evaluar alertas de existencias.

- **RF-STO-002** — El sistema permite configurar mínimos adicionales por ubicación interna o sucursal cuando el tenant dispone de ese ámbito y mantiene separada su evaluación respecto del mínimo general del producto.

- **RF-STO-003** — El sistema presenta por separado las existencias físicas registradas y las existencias disponibles de cada producto en los ámbitos de inventario consultables.

- **RF-STO-004** — El sistema permite seleccionar para cada producto si sus alertas se calculan con las existencias físicas, las disponibles o ambas.

- **RF-STO-005** — El sistema evalúa por separado el mínimo general y cada mínimo local configurado para mostrar las condiciones de stock bajo que correspondan.

- **RF-STO-006** — El sistema identifica y muestra las situaciones de existencias en cero aunque el producto no tenga definido un mínimo de stock.

- **RF-STO-007** — El sistema diferencia visualmente las condiciones de mínimo bajo y de existencias en cero sin utilizarlas como prohibición adicional para las operaciones permitidas.

- **RF-STO-008** — El sistema presenta las alertas de stock mediante indicadores visuales y notificaciones internas de la aplicación.

- **RF-STO-009** — El sistema notifica la entrada en una condición de alerta, evita emitir avisos repetidos mientras esa condición continúe y permite una nueva notificación después de la recuperación y la aparición de otra condición de alerta.

- **RF-STO-010** — El sistema actualiza la evaluación de stock físico y disponible después de operaciones confirmadas que modifiquen existencias o restricciones de disponibilidad, incluidas las que procedan de ventas, préstamos, mantenimiento, bajas o movimientos autorizados cuando correspondan.

- **RF-STO-011** — El sistema suspende las nuevas notificaciones de reposición de productos desactivados y permite consultar su historial de alertas conservado.

- **RF-STO-012** — El sistema restringe la consulta de existencias y alertas a los productos, funcionalidades y sucursales que el usuario tiene autorizados dentro de su tenant.

## Requisitos no funcionales (RNF)

- **RNF-STO-001** — La evaluación de existencias y alertas mantiene consistencia con las cantidades y restricciones confirmadas del inventario, sin considerar como definitivos los cambios de operaciones fallidas.

- **RNF-STO-002** — Las actualizaciones concurrentes o los reenvíos de una operación no generan efectos de stock duplicados ni notificaciones repetidas de una misma transición de alerta.

- **RNF-STO-003** — La información de existencias, mínimos, alertas y su historial se aísla por tenant y respeta las restricciones de acceso por sucursal cuando corresponde.

- **RNF-STO-004** — Las modificaciones relevantes de mínimos y de criterios de alerta conservan trazabilidad del responsable, la fecha y hora, el tenant y el ámbito afectado, sin permitir alteraciones ordinarias de los registros confirmados de auditoría.

## Reglas comerciales (RC)

- **RC-STO-001** — El módulo general de Control de stock se incluye por defecto en los cinco giros y en los tres niveles de plan, sin cobro independiente ni pérdida de sus funciones operativas al reducir el nivel del plan.

## Pendientes de definición (PT)

- **PT-STO-001** — Está pendiente definir la comparación exacta para activar una alerta de stock bajo respecto del mínimo configurado, incluidos los casos de igualdad y los valores mínimos permitidos.

- **PT-STO-002** — Está pendiente precisar cómo se agregan y comparan las existencias del mínimo general, las sucursales y las distintas ubicaciones internas de una misma sucursal, en coordinación con el pendiente de ubicaciones internas.

- **PT-STO-003** — Está pendiente definir la presentación y consolidación de alertas cuando un producto utiliza simultáneamente existencias físicas y disponibles como bases de evaluación y ambas producen alertas relacionadas.

- **PT-STO-004** — Está pendiente determinar el criterio inicial de alertas por producto y si al crear un producto el mínimo general se propone vacío, en cero o mediante otro valor, sin asumir un mínimo obligatorio.

- **PT-STO-005** — Está pendiente precisar quién puede configurar mínimos y bases de alerta, y qué destinatarios reciben las notificaciones internas según rol, permiso y sucursal.

- **PT-STO-006** — Está pendiente definir cómo se registra una recuperación de stock y cómo se tratan las transiciones de alerta causadas por cambios de configuración del mínimo o de la base de evaluación.

- **PT-STO-007** — Está pendiente concretar la conservación, visualización y depuración del historial de alertas, especialmente cuando un producto cambia de estado o el tenant termina su suscripción.

- **PT-STO-008** — Está pendiente definir el detalle operativo de las notificaciones internas de stock, su estado de lectura y su agrupación visual, sin incorporar canales externos no aprobados.
