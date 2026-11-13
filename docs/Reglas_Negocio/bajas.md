# Bajas de inventario — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Las entradas contienen únicamente su identificador y una descripción autónoma.

## Reglas de negocio (RN)

- **RN-BAJ-001** — Una baja solo puede confirmarse cuando la cuenta responsable tiene autorización vigente para la operación y el tenant mantiene acceso operativo.

- **RN-BAJ-002** — La confirmación de una baja no puede producir existencias negativas en el ámbito de inventario afectado.

- **RN-BAJ-003** — Una baja confirmada conserva su registro histórico y sus efectos se rectifican mediante operaciones posteriores trazables, sin sobrescribir el registro original.

- **RN-BAJ-004** — En abarrotes se distingue entre bajas temporales y definitivas y se registra el motivo correspondiente.

- **RN-BAJ-005** — En ferretería se distingue entre bajas temporales y definitivas y se utilizan motivos de baja estándar que el tenant puede personalizar.

- **RN-BAJ-006** — Un lote farmacéutico caducado permanece registrado e indisponible para la venta, sin desaparecer automáticamente del historial de inventario.

- **RN-BAJ-007** — Los medicamentos devueltos por clientes permanecen excluidos de la venta mientras se resuelve su baja o devolución al proveedor y no se reincorporan al inventario vendible.

- **RN-BAJ-008** — En farmacia se permite realizar una baja autorizada sobre un producto desactivado como excepción a la prohibición de nuevas operaciones ordinarias.

- **RN-BAJ-009** — En biblioteca, la baja de un ejemplar declarado extraviado cierra su préstamo como pérdida definitiva sin registrar una devolución física ficticia.

- **RN-BAJ-010** — La baja de un ejemplar de biblioteca se asocia a la unidad física identificada y preserva la identidad y el historial del título y de los demás ejemplares.

- **RN-BAJ-011** — En electrónicos se prohíbe dar de baja una unidad mientras mantenga un préstamo activo.

- **RN-BAJ-012** — En electrónicos se prohíbe dar de baja una unidad mientras mantenga una intervención de mantenimiento activa.

- **RN-BAJ-013** — Cuando una unidad electrónica prestada se declara definitivamente no recuperable, se cierra el préstamo como no recuperado y la unidad sigue indisponible hasta registrar su baja por separado.

- **RN-BAJ-014** — La baja de una unidad electrónica no elimina por sí sola otras incidencias, registros de garantías, préstamos cerrados ni intervenciones históricas asociados a ella.

- **RN-BAJ-015** — La baja de un artículo no equivale a la eliminación permanente de un producto que conserva movimientos históricos.

## Requisitos funcionales (RF)

- **RF-BAJ-001** — El sistema permite a los usuarios autorizados registrar bajas de registros de inventario conforme al alcance y la modalidad de seguimiento aplicables y conserva su historial.

- **RF-BAJ-002** — El sistema comprueba al confirmar una baja los permisos vigentes, el acceso operativo del tenant, las existencias afectadas y las restricciones específicas del giro.

- **RF-BAJ-003** — El sistema permite registrar en abarrotes bajas temporales o definitivas con su motivo y consultar sus registros históricos.

- **RF-BAJ-004** — El sistema permite registrar en ferretería bajas temporales o definitivas con motivos estándar configurables por el tenant y consultar sus registros históricos.

- **RF-BAJ-005** — El sistema mantiene visibles en el historial los lotes farmacéuticos caducados y los excluye de las ventas sin eliminarlos automáticamente.

- **RF-BAJ-006** — El sistema identifica los medicamentos devueltos por clientes como no vendibles y permite registrar su baja autorizada o su devolución al proveedor sin habilitar su reventa.

- **RF-BAJ-007** — El sistema permite registrar una baja farmacéutica autorizada sobre un producto desactivado sin reabrir las operaciones ordinarias del producto.

- **RF-BAJ-008** — El sistema permite registrar la baja de un ejemplar extraviado de biblioteca y cierra el préstamo relacionado como pérdida definitiva sin simular una devolución.

- **RF-BAJ-009** — El sistema bloquea la baja de una unidad electrónica cuando existe un préstamo activo o una intervención de mantenimiento activa.

- **RF-BAJ-010** — El sistema conserva indisponible la unidad electrónica cuyo préstamo se cerró como no recuperado hasta que una baja posterior sea registrada expresamente.

- **RF-BAJ-011** — El sistema registra las bajas y los cambios relacionados con autor, fecha y hora, tenant, sucursal cuando corresponda, unidad o producto afectado y vínculo con las operaciones relacionadas.

## Requisitos no funcionales (RNF)

- **RNF-BAJ-001** — La confirmación de una baja y sus efectos sobre existencias, disponibilidad y operaciones vinculadas se ejecutan de forma atómica para evitar registros parcialmente confirmados.

- **RNF-BAJ-002** — Las solicitudes concurrentes de baja, venta, préstamo, mantenimiento o ajuste sobre las mismas existencias se validan de nuevo antes de confirmar y no generan estados incompatibles ni stock negativo.

- **RNF-BAJ-003** — La repetición de una solicitud de baja con el mismo identificador no crea bajas ni movimientos duplicados y permite consultar el resultado confirmado previamente.

- **RNF-BAJ-004** — El sistema protege los registros confirmados de bajas y su auditoría frente a edición o eliminación ordinaria, conservando la trazabilidad de cualquier rectificación.

## Reglas comerciales (RC)

- **RC-BAJ-001** — La funcionalidad de bajas se incluye por defecto en los cinco giros y en los tres niveles de plan, sin contratarla como módulo adicional.

## Pendientes de definición (PT)

- **PT-BAJ-001** — Está pendiente definir los efectos operativos exactos de la baja temporal y de la baja definitiva sobre existencias físicas, disponibilidad y posible reincorporación, distinguiéndolos de la desactivación de productos.

- **PT-BAJ-002** — Está pendiente determinar si los giros distintos de abarrotes y ferretería utilizarán tipos de baja temporal y definitiva u otra clasificación específica.

- **PT-BAJ-003** — Está pendiente definir los motivos obligatorios, catálogos de motivos y posibilidades de personalización de bajas para cada giro, conservando los motivos configurables ya aprobados en ferretería.

- **PT-BAJ-004** — Está pendiente definir el alcance seleccionable de una baja por cantidad, lote o unidad física y cómo se gestionan las bajas parciales cuando correspondan.

- **PT-BAJ-005** — Está pendiente precisar qué permisos granulares autorizan las bajas y sus rectificaciones y si debe distinguirse entre solicitar, aprobar y confirmar una baja.

- **PT-BAJ-006** — Está pendiente precisar las consecuencias de una baja sobre unidades extraviadas sin recuperación física y los movimientos que correspondan sin simular una devolución.

- **PT-BAJ-007** — Está pendiente concretar el procedimiento de evaluación y tratamiento de productos devueltos o caducados que terminan en baja, sin alterar las prohibiciones de venta y las opciones de devolución a proveedor ya aprobadas.
