# Préstamos — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene solo su identificador y descripción.

## Reglas de negocio (RN)

- **RN-PRE-001** — El préstamo de un ejemplar de biblioteca requiere que el ejemplar esté disponible y que el lector registrado se encuentre activo.

- **RN-PRE-002** — Los lectores de biblioteca son personas registradas para el préstamo y no adquieren por ese registro una cuenta de acceso al SaaS.

- **RN-PRE-003** — El préstamo de un ejemplar de biblioteca conserva su existencia física registrada y lo vuelve temporalmente indisponible para otros préstamos o ventas.

- **RN-PRE-004** — La duración de los préstamos de biblioteca se determina mediante las políticas configuradas para el tipo de material o la clase de lector y la precedencia elegida por el tenant.

- **RN-PRE-005** — El número de préstamos simultáneos de un lector de biblioteca está sujeto al límite general configurado por el tenant.

- **RN-PRE-006** — La biblioteca aplica las restricciones a lectores con préstamos vencidos de acuerdo con la política configurada por el tenant.

- **RN-PRE-007** — Las renovaciones de préstamos de biblioteca se permiten únicamente bajo las condiciones configuradas por el tenant.

- **RN-PRE-008** — La devolución de un ejemplar de biblioteca en buen estado restablece su disponibilidad cuando no existe ninguna otra restricción activa.

- **RN-PRE-009** — La devolución de un ejemplar de biblioteca dañado mantiene el ejemplar indisponible hasta que una persona autorizada confirme su aptitud.

- **RN-PRE-010** — Un ejemplar de biblioteca declarado extraviado permanece identificado como no recuperado hasta que se aplique la baja correspondiente.

- **RN-PRE-011** — La baja de un ejemplar extraviado de biblioteca cierra el préstamo como pérdida definitiva sin registrarlo como devolución física.

- **RN-PRE-012** — La devolución de un ejemplar cuyo título esté desactivado puede registrarse para cerrar el préstamo y mantiene el ejemplar fuera de las operaciones ordinarias.

- **RN-PRE-013** — Un ejemplar de biblioteca designado para venta no puede incorporarse a nuevos préstamos mientras conserve esa designación.

- **RN-PRE-014** — El préstamo de una unidad electrónica solo se permite cuando la unidad está disponible y no está prestada, en mantenimiento ni sujeta a otra restricción que impida entregarla.

- **RN-PRE-015** — El préstamo de una unidad electrónica conserva su existencia física registrada y la mantiene indisponible para venta y nuevos préstamos mientras continúe prestada.

- **RN-PRE-016** — La condición física documentada al devolver una unidad electrónica determina si puede recuperarse su disponibilidad, sin anular otras restricciones vigentes.

- **RN-PRE-017** — Una unidad electrónica devuelta con daños permanece indisponible hasta que se autorice expresamente su aptitud para volver a utilizarse.

- **RN-PRE-018** — El préstamo de una unidad electrónica reportada como extraviada permanece abierto mientras no exista una determinación definitiva de no recuperación.

- **RN-PRE-019** — Cuando se determina definitivamente que una unidad electrónica prestada no se recuperará, el préstamo se cierra como no recuperado y la unidad permanece indisponible hasta que se tramite su baja por separado.

- **RN-PRE-020** — Una unidad electrónica con préstamo activo no puede darse de baja mientras el préstamo continúe abierto.

- **RN-PRE-021** — Las incidencias por daños de préstamos electrónicos pueden registrarse aunque el tenant no haya contratado Mantenimiento, y la reparación fuera del SaaS requiere autorización de aptitud antes de reutilizar la unidad.

- **RN-PRE-022** — Una unidad electrónica físicamente devuelta de un préstamo que sigue abierto por una incidencia puede incorporarse a mantenimiento únicamente cuando el módulo correspondiente esté contratado.

- **RN-PRE-023** — La devolución de un préstamo previo de producto desactivado se admite como operación de cierre, sin habilitar nuevos préstamos ni volver automáticamente disponible el producto.

- **RN-PRE-024** — Cuando Multisucursal está contratado, los préstamos deben devolverse en la misma sucursal donde se originaron.

- **RN-PRE-025** — Después de descontratar Multisucursal, únicamente el administrador principal puede registrar los cierres excepcionales autorizados de préstamos originados en sucursales secundarias.

- **RN-PRE-026** — Después de retirar el módulo adicional Préstamos de electrónicos, únicamente el administrador principal puede realizar cierres excepcionales de obligaciones anteriores sin iniciar nuevos préstamos.

## Requisitos funcionales (RF)

- **RF-PRE-001** — El sistema permite registrar y consultar lectores de biblioteca sin crearles credenciales ni permisos de acceso al SaaS.

- **RF-PRE-002** — El sistema permite registrar préstamos de ejemplares de biblioteca a lectores activos, comprueba la disponibilidad y los límites configurados y deja indisponible cada ejemplar prestado sin descontarlo del patrimonio físico.

- **RF-PRE-003** — El sistema permite configurar las duraciones de préstamos por tipo de material o clase de lector y establecer cuál de esas reglas prevalece.

- **RF-PRE-004** — El sistema detecta préstamos vencidos de biblioteca y aplica las restricciones configuradas para impedir préstamos nuevos cuando corresponda.

- **RF-PRE-005** — El sistema permite renovar préstamos de biblioteca únicamente cuando se cumplen las condiciones configuradas por el tenant.

- **RF-PRE-006** — El sistema registra la devolución de ejemplares de biblioteca con su condición física y los deja disponibles solo cuando están en buen estado y no tienen otras restricciones, o mantiene su indisponibilidad cuando están dañados.

- **RF-PRE-007** — El sistema permite registrar la evaluación autorizada de ejemplares dañados de biblioteca para restablecer su aptitud sin omitir otras restricciones vigentes.

- **RF-PRE-008** — El sistema permite declarar extraviado un ejemplar de biblioteca y cerrar su préstamo como pérdida definitiva cuando se registra la baja correspondiente, sin simular una devolución.

- **RF-PRE-009** — El sistema permite registrar devoluciones de préstamos anteriores vinculados a títulos o productos desactivados, manteniendo el bloqueo de nuevas operaciones.

- **RF-PRE-010** — El sistema permite prestar unidades electrónicas disponibles cuando el módulo Préstamos está contratado y evita que unidades prestadas entren simultáneamente en venta o en otro préstamo.

- **RF-PRE-011** — El sistema registra la devolución y condición física de cada unidad electrónica prestada y mantiene indisponibles las unidades dañadas o sujetas a otras restricciones.

- **RF-PRE-012** — El sistema permite registrar incidencias, extravíos y determinaciones de no recuperación de unidades electrónicas, cerrando los préstamos irreversiblemente perdidos sin registrar retorno físico y manteniendo las unidades no disponibles hasta su baja separada.

- **RF-PRE-013** — El sistema permite cerrar préstamos únicamente en su sucursal de origen o mediante las excepciones administrativas autorizadas tras retirar Multisucursal.

- **RF-PRE-014** — El sistema permite al administrador principal cerrar obligaciones antiguas del módulo Préstamos de electrónicos después de su descontratación sin habilitar nuevos préstamos.

- **RF-PRE-015** — El sistema audita los registros, renovaciones, devoluciones, incidencias, pérdidas y cierres de préstamos con autor, fecha, tenant y sucursal cuando corresponda.

## Requisitos no funcionales (RNF)

- **RNF-PRE-001** — Cada confirmación de préstamo o devolución actualiza de forma atómica el estado de la operación y la disponibilidad de la unidad, sin alterar indebidamente las existencias físicas registradas.

- **RNF-PRE-002** — Las confirmaciones concurrentes de préstamos vuelven a validar la disponibilidad de cada ejemplar o unidad e impiden asignar simultáneamente la misma unidad a operaciones incompatibles.

- **RNF-PRE-003** — La repetición de una misma solicitud identificada de préstamo, renovación o devolución produce un único efecto confirmado y permite consultar su resultado después de una interrupción de conexión.

- **RNF-PRE-004** — Los historiales confirmados de préstamos, devoluciones, incidencias y cierres se protegen contra alteraciones ordinarias y sus modificaciones relevantes conservan trazabilidad.

## Reglas comerciales (RC)

- **RC-PRE-001** — El módulo Préstamos forma parte de las funcionalidades base de Biblioteca en los tres niveles de plan.

- **RC-PRE-002** — El módulo Préstamos de productos electrónicos se habilita como módulo adicional únicamente después de su contratación y confirmación de pago.

## Pendientes de definición (PT)

- **PT-PRE-001** — Está pendiente definir los datos exigidos para identificar a los destinatarios de préstamos electrónicos y las restricciones de elegibilidad que les resulten aplicables.

- **PT-PRE-002** — Está pendiente precisar los parámetros configurables de biblioteca para límites, duraciones, renovaciones y restricciones por vencimiento, sin alterar las facultades de configuración ya acordadas.

- **PT-PRE-003** — Está pendiente definir el procedimiento y las autorizaciones específicas para comprobar y documentar la aptitud de una unidad electrónica dañada tras un préstamo.

- **PT-PRE-004** — Está pendiente precisar qué información obligatoria se registra en una operación de préstamo y en una devolución, más allá de la unidad, el lector cuando corresponda, el estado y su trazabilidad.
