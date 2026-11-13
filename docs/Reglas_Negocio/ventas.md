# Ventas — Catálogo de requisitos

**Versión:** 1.1 (formato simplificado; contenido de v1.0)  
**Estado:** Aprobada; pendientes de definición conservados.

Cada entrada contiene solo su identificador y descripción.

## Reglas de negocio (RN)

- **RN-VEN-001** — La venta reduce las existencias físicas únicamente cuando se confirma la entrega de los productos al cliente, independientemente de que el pago haya sido realizado.

- **RN-VEN-002** — Una venta pendiente de abarrotes, farmacia o ferretería se cancela cuando la confirmación de la entrega detecta existencias insuficientes.

- **RN-VEN-003** — Una venta confirmada de abarrotes no se cancela directamente y sus efectos posteriores se gestionan mediante el proceso de devolución correspondiente.

- **RN-VEN-004** — Ninguna venta de abarrotes o farmacia entrega productos correspondientes a lotes cuya caducidad ya ha vencido.

- **RN-VEN-005** — La asignación de lotes para una venta de abarrotes o farmacia prioriza los lotes no caducados con fecha de vencimiento más próxima.

- **RN-VEN-006** — Cada producto farmacéutico vendido se identifica con el lote y la fecha de caducidad requeridos por el control farmacéutico definido.

- **RN-VEN-007** — La venta de un medicamento señalado como sujeto a prescripción exige que el cajero confirme la indicación mostrada por el sistema sin registrar el contenido de la receta.

- **RN-VEN-008** — Un medicamento devuelto por un cliente queda permanentemente excluido de la venta y se mantiene pendiente de baja o devolución al proveedor según corresponda.

- **RN-VEN-009** — La devolución comercial de abarrotes asociada a un producto desactivado conserva el artículo recibido fuera de la disponibilidad ordinaria de venta.

- **RN-VEN-010** — Las ventas fraccionarias o por presentaciones de ferretería afectan las existencias expresadas en la unidad base del producto mediante su conversión correspondiente.

- **RN-VEN-011** — Un artículo de ferretería devuelto por un cliente permanece no vendible hasta que una evaluación autorizada determine que puede reincorporarse a la venta.

- **RN-VEN-012** — El plazo de una garantía básica de ferretería comienza en la fecha de entrega física del producto vendido.

- **RN-VEN-013** — Las reclamaciones de garantía de ferretería pueden registrarse aun cuando el plazo de garantía haya vencido, sin conceder cobertura automáticamente.

- **RN-VEN-014** — Los reembolsos y reemplazos con efecto económico derivados de garantías de ferretería se gestionan dentro de Ventas.

- **RN-VEN-015** — La biblioteca solo vende ejemplares expresamente designados para venta y libres de restricciones que impidan su salida.

- **RN-VEN-016** — Un ejemplar de biblioteca designado para venta queda excluido de nuevos préstamos mientras conserve esa designación.

- **RN-VEN-017** — Una unidad electrónica solo puede venderse cuando no está prestada, en mantenimiento ni sujeta a otra restricción vigente que impida su disponibilidad.

- **RN-VEN-018** — Una unidad electrónica devuelta por una venta queda inicialmente no disponible y requiere una inspección antes de volver a considerarse vendible.

- **RN-VEN-019** — Las devoluciones de ventas previamente realizadas sobre productos desactivados se admiten como excepciones de cierre en los giros donde esa posibilidad fue aprobada.

- **RN-VEN-020** — Una devolución comercial se registra en la sucursal donde se originó la venta cuando Multisucursal está contratado.

- **RN-VEN-021** — El registro de una reclamación de garantía no implica la aprobación automática de su cobertura ni de una devolución comercial.

- **RN-VEN-022** — Las ventas de los tenants no generan CFDI desde el SaaS y su facturación fiscal se realiza mediante medios externos a la plataforma.

## Requisitos funcionales (RF)

- **RF-VEN-001** — El sistema registra operaciones de venta únicamente cuando Ventas está disponible para el giro y el usuario cuenta con autorización.

- **RF-VEN-002** — El sistema registra la entrega física de los productos vendidos y genera una única salida de inventario por las unidades efectivamente entregadas, sin disminuir existencias por el solo registro o cobro de la venta y sin permitir stock negativo.

- **RF-VEN-003** — El sistema impide entregar lotes caducados en ventas de abarrotes y farmacia, exige identificar los lotes y su caducidad cuando corresponda y prioriza los lotes aptos con vencimiento más próximo.

- **RF-VEN-004** — El sistema muestra al cajero la indicación de prescripción requerida para medicamentos marcados, solicita su confirmación antes de continuar la venta y no registra el contenido de la receta.

- **RF-VEN-005** — El sistema cancela una venta pendiente de abarrotes, farmacia o ferretería cuando la confirmación de la entrega detecta existencias insuficientes.

- **RF-VEN-006** — El sistema registra devoluciones comerciales vinculadas a ventas previas, conserva fuera de venta los medicamentos devueltos, exige evaluación antes de revender devoluciones de ferretería y electrónicos, y permite las excepciones aprobadas para productos desactivados y sucursales de origen.

- **RF-VEN-007** — El sistema registra ventas de ferretería con cantidades fraccionarias o presentaciones convertibles y descuenta la cantidad equivalente en la unidad base del producto sin generar existencias negativas.

- **RF-VEN-008** — El sistema permite registrar una evaluación autorizada de mercancía devuelta de ferretería y solo reincorpora a la venta los artículos cuya aptitud haya sido confirmada.

- **RF-VEN-009** — El sistema permite registrar la duración de las garantías básicas de ferretería, calcular su vigencia desde la entrega física y documentar reclamaciones incluso después del vencimiento sin aprobar automáticamente su cobertura.

- **RF-VEN-010** — El sistema registra dentro de Ventas los reembolsos y reemplazos con efecto económico que deriven de garantías de ferretería, vinculándolos con la operación comercial correspondiente.

- **RF-VEN-011** — El sistema permite vender ejemplares individuales de biblioteca designados para venta únicamente cuando no tengan restricciones activas y los excluye de nuevos préstamos mientras mantengan dicha designación.

- **RF-VEN-012** — El sistema permite registrar la venta de unidades electrónicas únicamente si están disponibles y no se encuentran prestadas, en mantenimiento o restringidas, y mantiene indisponible cualquier unidad devuelta hasta completar su inspección.

- **RF-VEN-013** — El sistema dispone de cierre de caja como función de Ventas para abarrotes, farmacia y ferretería.

- **RF-VEN-014** — El sistema registra las modificaciones relevantes de ventas y devoluciones con autoría, momento y referencias a los movimientos implicados.

## Requisitos no funcionales (RNF)

- **RNF-VEN-001** — El sistema confirma de manera atómica los registros de entrega o devolución y sus movimientos de inventario asociados, sin dejar confirmaciones comerciales incongruentes con las existencias.

- **RNF-VEN-002** — El sistema identifica las repeticiones de una misma confirmación de entrega o devolución y conserva un único resultado sin duplicar movimientos o registros comerciales.

- **RNF-VEN-003** — Las ventas confirmadas simultáneamente sobre un mismo inventario vuelven a validar existencias y restricciones al confirmar, evitan stock negativo y rechazan o cancelan las operaciones que no puedan completarse conforme al giro.

- **RNF-VEN-004** — El sistema consulta el resultado de una venta enviada antes de una interrupción de conexión y solamente permite reintentarla cuando pueda evitar un segundo registro o descuento de existencias.

## Reglas comerciales (RC)

- **RC-VEN-001** — El módulo de Ventas forma parte de la contratación base de abarrotes, farmacia y ferretería en los tres niveles de plan.

- **RC-VEN-002** — El módulo de Ventas para biblioteca y productos electrónicos se habilita únicamente cuando ha sido contratado y su pago confirmado.

## Pendientes de definición (PT)

- **PT-VEN-001** — Permanece pendiente la definición del modelo de estados de venta y de la admisión o prohibición de entregas parciales.

- **PT-VEN-002** — Permanece pendiente la definición del alcance de devoluciones parciales, modalidades de reembolso o reemplazo y tratamiento de devoluciones comerciales de biblioteca.

- **PT-VEN-003** — Permanece pendiente determinar si Ventas generará comprobantes operativos no fiscales y qué datos deberán contener.

- **PT-VEN-004** — Permanece pendiente la definición del alcance del cierre de caja, sus periodos, conciliación, diferencias y permisos específicos.

- **PT-VEN-005** — Permanece pendiente la definición de precisión y redondeo de cantidades y conversiones a unidad base en ferretería.

- **PT-VEN-006** — Permanece pendiente determinar quién evalúa las devoluciones de electrónicos y cuáles son los resultados autorizados que pueden devolverles disponibilidad.
