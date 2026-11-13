# Caducidades — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene únicamente su identificador y una descripción autónoma; los puntos PT representan decisiones aún no confirmadas.

## Reglas de negocio (RN)

- **RN-CAD-001** — En abarrotes, las existencias sujetas a control de caducidad se identifican por lote y fecha de vencimiento para distinguirlas de otras existencias del mismo producto.

- **RN-CAD-002** — En farmacia, las existencias de medicamentos se registran con su lote y su fecha de caducidad como información obligatoria.

- **RN-CAD-003** — En abarrotes y farmacia, ninguna venta puede entregar existencias procedentes de un lote cuya fecha de caducidad ya haya vencido.

- **RN-CAD-004** — Para las ventas de abarrotes y farmacia sujetas a control de lotes, se priorizan las existencias no caducadas cuya fecha de vencimiento sea la más próxima mediante el criterio FEFO.

- **RN-CAD-005** — La aptitud para venta se determina por cada lote, de manera que la existencia de lotes vigentes del mismo producto no habilita la venta de un lote vencido.

- **RN-CAD-006** — En farmacia, los lotes vencidos permanecen identificables en los registros e historiales del inventario aunque estén excluidos de la venta.

- **RN-CAD-007** — El vencimiento de un lote farmacéutico no implica la eliminación automática de su registro histórico ni equivale por sí mismo a confirmar una baja de inventario.

- **RN-CAD-008** — Los medicamentos devueltos por clientes permanecen fuera de la venta aunque su fecha de caducidad continúe vigente, hasta que se tramite su baja o devolución al proveedor según corresponda.

- **RN-CAD-009** — La caducidad se evalúa junto con las demás restricciones vigentes antes de considerar una existencia disponible para una venta.

- **RN-CAD-010** — La información de lote y caducidad vinculada a las operaciones se conserva en el historial para distinguir el origen y la aptitud de las existencias utilizadas.

## Requisitos funcionales (RF)

- **RF-CAD-001** — El sistema permite registrar y consultar lotes y fechas de vencimiento de productos de abarrotes sujetos al control de caducidad, manteniendo sus existencias diferenciadas por lote.

- **RF-CAD-002** — El sistema exige lote y fecha de caducidad al registrar existencias de medicamentos en farmacia y permite consultar dicha información.

- **RF-CAD-003** — El sistema muestra las existencias por lote con su fecha de caducidad y distingue los lotes vencidos de los lotes todavía aptos para venta.

- **RF-CAD-004** — El sistema rechaza la confirmación de entregas de ventas de abarrotes o farmacia que pretendan utilizar unidades de lotes vencidos.

- **RF-CAD-005** — El sistema prioriza para las ventas de abarrotes y farmacia sujetas a control de lotes las existencias no caducadas con vencimiento más próximo, sin permitir que un lote vencido sea seleccionado para la entrega.

- **RF-CAD-006** — El sistema conserva la identificación del lote y su fecha de caducidad en las operaciones y movimientos de venta farmacéuticos para permitir su consulta histórica.

- **RF-CAD-007** — El sistema mantiene visibles los lotes farmacéuticos caducados en las consultas e historiales de inventario sin eliminarlos automáticamente al vencer.

- **RF-CAD-008** — El sistema mantiene los medicamentos devueltos fuera de la disponibilidad de venta y permite registrar su baja autorizada o devolución al proveedor sin reincorporarlos a la venta.

- **RF-CAD-009** — El sistema verifica en la confirmación de una venta de abarrotes o farmacia la caducidad y las demás restricciones vigentes de los lotes involucrados antes de descontar existencias.

## Requisitos no funcionales (RNF)

- **RNF-CAD-001** — La confirmación de una entrega de venta que utiliza lotes mantiene consistentes el lote seleccionado, la cantidad entregada, el registro comercial y el movimiento de inventario, sin confirmaciones parciales inconsistentes.

- **RNF-CAD-002** — Las ventas concurrentes que utilizan existencias por lote vuelven a comprobar disponibilidad y caducidad antes de confirmarse y no generan salidas duplicadas ni stock negativo.

- **RNF-CAD-003** — El sistema conserva trazabilidad de los registros y modificaciones relevantes de lotes y caducidades mediante información de responsable, fecha y hora, tenant, sucursal cuando aplique y registros afectados.

- **RNF-CAD-004** — Los eventos y movimientos relacionados con lotes y caducidades se presentan con la zona horaria de su sucursal y conservan una referencia temporal consistente para su consulta histórica.

## Reglas comerciales (RC)

- **RC-CAD-001** — La funcionalidad de control de caducidades está incluida por defecto en los giros de abarrotes y farmacia en los tres niveles de plan, sin contratarla como módulo adicional.

## Pendientes de definición (PT)

- **PT-CAD-001** — Está pendiente definir qué categorías y tipos de productos de abarrotes requieren control obligatorio de lote y fecha de caducidad y cuáles pueden operar sin esos datos.

- **PT-CAD-002** — Está pendiente definir cómo se identifica de manera única cada lote dentro del tenant y cómo se diferencian lotes con el mismo código de proveedor o diferentes fechas de vencimiento.

- **PT-CAD-003** — Está pendiente precisar el instante a partir del cual una fecha de caducidad vuelve no vendible a un lote, incluidos productos con fecha sin hora y las zonas horarias aplicables.

- **PT-CAD-004** — Está pendiente definir si el criterio FEFO solo establece la prioridad de selección o si permite excepciones autorizadas para escoger otro lote todavía vigente.

- **PT-CAD-005** — Está pendiente definir si el sistema ofrecerá alertas anticipadas por próximos vencimientos y, en su caso, los plazos, destinatarios y medios de notificación, sin confundirlas con las alertas por stock mínimo.

- **PT-CAD-006** — Está pendiente establecer el tratamiento de lotes que ya estén vencidos al momento de registrar una entrada o devolución y las operaciones distintas de la venta que podrán realizarse sobre ellos.

- **PT-CAD-007** — Está pendiente definir qué campos de identificación y caducidad de un lote con movimientos admiten corrección, qué autorizaciones requiere y cómo se mantiene la trazabilidad de las modificaciones.

- **PT-CAD-008** — Está pendiente especificar el flujo operativo de baja, devolución a proveedor u otro destino de lotes vencidos, sin suponer su eliminación automática ni contradecir las restricciones farmacéuticas aprobadas.
