# Área 19 — Incidencias y garantías básicas

**Versión:** 1.0  
**Estado:** Pendiente de aprobación.  
**Formato:** identificador y descripción autónoma por entrada; los pendientes no constituyen decisiones aprobadas.

## Reglas de negocio (RN)

- **RN-ING-001** — El giro de productos electrónicos permite registrar incidencias de sus unidades físicas aunque el tenant no tenga contratado el módulo adicional Mantenimiento.

- **RN-ING-002** — La biblioteca conserva el registro de los daños y extravíos de ejemplares asociados a préstamos, sin convertir a sus lectores en usuarios con acceso al SaaS.

- **RN-ING-003** — Un ejemplar de biblioteca devuelto con daños permanece indisponible hasta que una persona autorizada determine que es apto para utilizarse y no exista otra restricción vigente.

- **RN-ING-004** — Un ejemplar de biblioteca declarado extraviado conserva su condición de no recuperado hasta registrar su baja, que cierra el préstamo como pérdida definitiva sin simular una devolución física.

- **RN-ING-005** — Una unidad electrónica devuelta con daños permanece indisponible hasta que se autorice expresamente su aptitud y se hayan resuelto las demás restricciones que impidan utilizarla.

- **RN-ING-006** — Un préstamo electrónico con incidencia de extravío permanece abierto hasta determinar definitivamente la no recuperación de la unidad, tras lo cual se cierra como no recuperado y la unidad sigue indisponible hasta tramitar su baja por separado.

- **RN-ING-007** — El registro de una incidencia electrónica no habilita la gestión de reparaciones dentro del SaaS cuando el módulo adicional Mantenimiento no está contratado.

- **RN-ING-008** — Una unidad electrónica devuelta físicamente cuyo préstamo sigue abierto por una incidencia puede ingresar a Mantenimiento si el módulo está contratado, sin que la intervención cierre automáticamente dicho préstamo.

- **RN-ING-009** — La resolución de una incidencia no elimina por sí sola otras causas vigentes de indisponibilidad de un ejemplar o unidad física.

- **RN-ING-010** — La garantía básica de ferretería se identifica mediante su condición y duración registradas, y su plazo comienza con la entrega física del producto vendido.

- **RN-ING-011** — Una reclamación de garantía de ferretería puede registrarse después del vencimiento de su plazo sin que el registro implique aprobación automática de cobertura.

- **RN-ING-012** — Los reemplazos y reembolsos con efecto económico derivados de reclamaciones de garantía de ferretería se gestionan exclusivamente dentro de Ventas.

- **RN-ING-013** — El registro básico de garantías de productos electrónicos permanece disponible aun sin contratar Mantenimiento, mientras que el seguimiento del servicio ante proveedores se realiza dentro del SaaS únicamente con dicho módulo contratado.

- **RN-ING-014** — Una garantía electrónica vigente con cobertura confirmada por el proveedor requiere que ese proveedor atienda el servicio cubierto, sin sustituirlo por mantenimiento propio.

- **RN-ING-015** — Mientras esté pendiente la decisión de cobertura de una garantía electrónica, la unidad permanece indisponible y no puede iniciarse mantenimiento propio.

- **RN-ING-016** — Si la cobertura de una garantía electrónica ya fue resuelta y no existe cobertura confirmada que obligue a la atención del proveedor, un administrador autorizado puede elegir mantenimiento propio o externo únicamente cuando el módulo Mantenimiento está contratado y se respetan las condiciones de garantía aplicables.

## Requisitos funcionales (RF)

- **RF-ING-001** — El sistema permite registrar y consultar incidencias asociadas a unidades electrónicas identificadas, incluidos daños observados, sin exigir la contratación del módulo adicional Mantenimiento.

- **RF-ING-002** — El sistema registra las incidencias de daños o extravío de ejemplares de biblioteca con referencia al ejemplar y al préstamo correspondiente cuando exista, sin asignar credenciales del SaaS al lector.

- **RF-ING-003** — El sistema mantiene indisponibles los ejemplares de biblioteca devueltos con daños y permite registrar una evaluación autorizada de aptitud antes de restablecer su disponibilidad, siempre que no exista otra restricción activa.

- **RF-ING-004** — El sistema registra los extravíos de ejemplares de biblioteca y permite cerrar el préstamo asociado como pérdida definitiva mediante la baja correspondiente, sin registrar una devolución física inexistente.

- **RF-ING-005** — El sistema registra los daños y extravíos de unidades electrónicas asociadas a préstamos, mantiene la indisponibilidad pertinente y permite documentar la determinación definitiva de no recuperación antes de cerrar el préstamo y tramitar la baja separada de la unidad.

- **RF-ING-006** — El sistema permite registrar la aptitud autorizada de una unidad electrónica dañada y calcula su disponibilidad tomando en cuenta todas las restricciones que continúen vigentes.

- **RF-ING-007** — El sistema permite registrar una intervención de Mantenimiento sobre una unidad electrónica físicamente devuelta con préstamo aún abierto por incidencia únicamente cuando el módulo está contratado, manteniendo independientes los estados de ambas operaciones.

- **RF-ING-008** — El sistema permite registrar la condición y duración de la garantía básica de ferretería, calcula su vigencia desde la entrega física y documenta reclamaciones posteriores al vencimiento sin conceder cobertura automáticamente.

- **RF-ING-009** — El sistema vincula los reemplazos y reembolsos derivados de garantías de ferretería con las operaciones de Ventas correspondientes y sus movimientos autorizados de inventario.

- **RF-ING-010** — El sistema permite registrar y consultar información básica de garantías electrónicas sin exigir Mantenimiento y habilita el seguimiento del servicio ante el proveedor dentro del SaaS solo cuando dicho módulo está contratado.

- **RF-ING-011** — Cuando el módulo Mantenimiento está contratado, el sistema registra el estado de cobertura de garantías electrónicas y, mientras la cobertura permanezca pendiente, bloquea el mantenimiento propio y conserva la indisponibilidad de la unidad.

- **RF-ING-012** — El sistema identifica al proveedor encargado de atender una garantía electrónica vigente con cobertura confirmada y, si el tenant contrata Mantenimiento, impide sustituir esa atención por mantenimiento propio.

## Requisitos no funcionales (RNF)

- **RNF-ING-001** — La información de incidencias, garantías y reclamaciones se mantiene aislada por tenant y solo resulta accesible mediante cuentas con autorización vigente y alcance de sucursal aplicable.

- **RNF-ING-002** — El sistema aplica de forma íntegra los cambios confirmados de incidencias, aptitud y disponibilidad relacionados, sin dejar estados parcialmente actualizados que permitan operaciones incompatibles.

- **RNF-ING-003** — El sistema reconoce el reenvío de una misma operación identificada de incidencia o garantía y evita crear efectos confirmados duplicados después de fallos de conexión.

- **RNF-ING-004** — Los cambios relevantes y las resoluciones de incidencias y garantías conservan registros auditables protegidos contra alteraciones ordinarias, con responsable, momento y referencias a los registros afectados.

## Reglas comerciales (RC)

- **RC-ING-001** — El registro de incidencias de biblioteca y productos electrónicos y las garantías básicas de ferretería y productos electrónicos forman parte de las funcionalidades incluidas en los respectivos giros sin contratar un módulo extra denominado Incidencias o Garantías.

- **RC-ING-002** — El seguimiento de la atención de garantías electrónicas dentro del SaaS y la ejecución de intervenciones pertenecen al módulo adicional Mantenimiento, sin retirar las capacidades de registro básico de garantías e incidencias cuando ese módulo no está contratado.

## Pendientes de definición (PT)

- **PT-ING-001** — Está pendiente definir los tipos de incidencia y los campos obligatorios aplicables a ejemplares de biblioteca y unidades electrónicas, sin asumir un catálogo único para ambos giros.

- **PT-ING-002** — Está pendiente definir qué permisos autorizan evaluar daños, determinar aptitud, resolver incidencias y registrar decisiones de no recuperación en cada giro.

- **PT-ING-003** — Está pendiente definir si las incidencias y reclamaciones admitirán evidencias adjuntas, como fotografías o documentos, y los formatos o límites de dichos archivos.

- **PT-ING-004** — Está pendiente precisar los datos y el método de cálculo de vigencia de las garantías básicas de productos electrónicos, sin trasladarles automáticamente la regla de inicio de garantías de ferretería.

- **PT-ING-005** — Está pendiente definir el procedimiento de evaluación y respuesta a reclamaciones de garantía de ferretería y las autorizaciones concretas para aprobar cobertura, reemplazo o reembolso.

- **PT-ING-006** — Está pendiente establecer cómo se relacionan varias incidencias coexistentes de un mismo ejemplar o unidad, qué estados tendrá cada una y qué condiciones permitirán cerrarlas o reabrirlas.

- **PT-ING-007** — Está pendiente definir el procedimiento y las evidencias para confirmar o rechazar cobertura de garantías electrónicas ante proveedores, incluidos casos sin respuesta, coordinándolo con el pendiente de Mantenimiento.

- **PT-ING-008** — Está pendiente precisar cómo afectan la desactivación de un producto y la retirada de módulos contratados al registro y seguimiento de incidencias o reclamaciones anteriores que sigan sin resolverse, respetando las excepciones de cierre ya aprobadas.
