# Suscripciones, pagos y facturación del SaaS — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene solo el identificador y una descripción autónoma; los pendientes de definición no constituyen decisiones aprobadas.

## Reglas de negocio (RN)

- **RN-SUS-001** — Una contratación en registro sin pago confirmado conserva su información para retomar la compra, pero no concede acceso operativo al tenant.

- **RN-SUS-002** — Ninguna contratación inicial, ampliación de nivel, incorporación de módulo extra o reactivación por impago habilita las funcionalidades solicitadas hasta existir una confirmación válida del pago exigible.

- **RN-SUS-003** — Un pago pendiente de confirmación mantiene sin activar los cambios comerciales solicitados y conserva las funcionalidades cuya vigencia ya esté pagada.

- **RN-SUS-004** — El fracaso del cobro por una ampliación o un aumento de nivel no suspende la contratación ya pagada y mantiene pendiente el cambio solicitado.

- **RN-SUS-005** — El nivel base y los módulos extra contratados por un tenant comparten periodicidad de facturación y fecha de renovación.

- **RN-SUS-006** — El impago de una renovación inicia un periodo de gracia de siete días naturales desde la fecha y hora de renovación originalmente programadas.

- **RN-SUS-007** — Durante el periodo de gracia por renovación impagada el tenant conserva las operaciones autorizadas conforme a su contratación vigente.

- **RN-SUS-008** — Al agotarse los siete días de gracia sin regularización, el tenant queda suspendido y sus usuarios únicamente pueden consultar y descargar información dentro de sus permisos vigentes.

- **RN-SUS-009** — Mientras el tenant esté suspendido por impago quedan prohibidas las acciones que modifiquen inventario, operaciones, usuarios o configuración operativa.

- **RN-SUS-010** — Una suscripción suspendida por impago termina cuando llega la siguiente fecha de renovación del calendario original y continúa sin regularizarse el adeudo exigible.

- **RN-SUS-011** — La regularización de una suscripción suspendida reactiva automáticamente las funcionalidades contratadas cuando se confirma el pago exigible conforme a la política de regularización vigente.

- **RN-SUS-012** — El pago tardío de una renovación de una suscripción todavía recuperable conserva la fecha original de las renovaciones siguientes.

- **RN-SUS-013** — La cancelación voluntaria de la renovación automática conserva las funcionalidades pagadas hasta finalizar su periodo vigente, sin interrumpirlas en el momento de cancelar.

- **RN-SUS-014** — El administrador principal puede revertir la cancelación de la renovación automática antes de finalizar el periodo pagado sin generar por ese acto un cobro inmediato.

- **RN-SUS-015** — Al terminar una suscripción se bloquea el acceso directo a los módulos y datos operativos, sin impedir las funciones de cuenta, contratación y documentación expresamente permitidas.

- **RN-SUS-016** — Los datos operativos de un tenant cuya suscripción ha terminado permanecen conservados durante 180 días naturales contados desde la terminación, sin perjuicio de los plazos legales aplicables a información específica.

- **RN-SUS-017** — Al completar los 180 días posteriores a la terminación sin recontratación se eliminan o anonimizan los datos operativos mediante un procedimiento controlado, salvo información sujeta a conservación legal.

- **RN-SUS-018** — La recontratación confirmada dentro del periodo de conservación recupera el mismo tenant y sus datos conservados e inicia un nuevo periodo de facturación desde el pago confirmado.

- **RN-SUS-019** — Tras recuperar un tenant terminado solo el administrador principal obtiene acceso inicialmente, mientras las demás cuentas y sus roles se conservan inactivos hasta su reactivación expresa conforme a la nueva contratación.

- **RN-SUS-020** — Los permisos granulares eliminados por descontratación o pérdida de capacidades no reaparecen automáticamente al reactivar usuarios o contratar de nuevo un módulo.

- **RN-SUS-021** — Durante los 180 días de conservación el administrador principal puede solicitar al operador del SaaS una exportación controlada de la información conservada sin reactivar el acceso operativo.

- **RN-SUS-022** — La exportación posterior a la terminación exige verificación de identidad e incluye catálogos, movimientos, históricos, relaciones y documentos operativos disponibles sin exponer datos de otros tenants ni secretos internos de la plataforma.

- **RN-SUS-023** — Únicamente el administrador principal recibe las notificaciones comerciales de pago, renovación, suspensión, reactivación, precios y conservación del tenant.

- **RN-SUS-024** — Los comprobantes y documentos fiscales de la suscripción permanecen consultables y descargables por el administrador principal desde la sección de cuenta durante los plazos de conservación aplicables aunque el servicio operativo haya terminado.

- **RN-SUS-025** — Los pagos y la facturación del SaaS corresponden a su propia relación de suscripción y no convierten a la plataforma en un emisor de CFDI por las ventas realizadas por los tenants.

- **RN-SUS-026** — Los cambios de nivel y de módulos extra solo pueden solicitarse y autorizarse comercialmente por el administrador principal del tenant.

- **RN-SUS-027** — Los cierres excepcionales de obligaciones iniciadas con módulos extra posteriormente descontratados solo pueden ejecutarse por el administrador principal mientras el tenant tenga acceso operativo válido, sin habilitar operaciones ordinarias nuevas.

## Requisitos funcionales (RF)

- **RF-SUS-001** — El sistema conserva los datos de una contratación inicial no pagada y permite al cliente retomar la selección y repetir el intento de pago sin otorgarle acceso operativo previo.

- **RF-SUS-002** — El sistema presenta en el proceso de pago los conceptos del nivel base y módulos extra seleccionados, su periodicidad, los precios con impuestos incluidos y el desglose de los impuestos aplicables.

- **RF-SUS-003** — El sistema crea una referencia única para cada obligación de pago y conserva su estado y los intentos relacionados, sin tratar una solicitud enviada como confirmación definitiva.

- **RF-SUS-004** — El sistema recibe y verifica la confirmación del cobro de la pasarela seleccionada antes de activar una contratación, ampliación, renovación o reactivación.

- **RF-SUS-005** — El sistema evita procesar dos veces una misma obligación de pago cuando coinciden respuestas de la pasarela y reintentos automáticos o manuales.

- **RF-SUS-006** — El sistema genera los intentos de cobro recurrente conforme al calendario de la suscripción y a la política de reintentos configurada por el operador.

- **RF-SUS-007** — El sistema permite al administrador principal solicitar un nuevo intento manual de un cobro fallido cuando el estado de la obligación lo permita y sin duplicar cargos.

- **RF-SUS-008** — El sistema conserva pendiente una ampliación o cambio de nivel cuyo cobro no se confirme y mantiene habilitados los conceptos que ya estaban pagados.

- **RF-SUS-009** — El sistema calcula y presenta el importe proporcional de los aumentos de nivel y módulos adicionales a partir de los días naturales restantes del periodo compartido de renovación.

- **RF-SUS-010** — El sistema permite al administrador principal programar para el final del periodo pagado una reducción de nivel o retirada de módulos extra y muestra cuándo se aplicará cada modificación.

- **RF-SUS-011** — El sistema permite al administrador principal cancelar la renovación automática y volver a habilitarla antes de finalizar el periodo pagado sin emitir un cargo inmediato por esa reversión.

- **RF-SUS-012** — El sistema identifica la fecha y hora programadas de cada renovación impagada y aplica los siete días naturales de gracia con acceso operativo conservado.

- **RF-SUS-013** — El sistema suspende las modificaciones operativas cuando vence la gracia sin pago confirmado y conserva únicamente consultas y descargas autorizadas.

- **RF-SUS-014** — El sistema identifica la siguiente fecha de renovación del calendario original para terminar una suscripción que siga impagada y que ya haya superado su gracia.

- **RF-SUS-015** — El sistema reactiva automáticamente los módulos y operaciones contratadas tras la confirmación válida de los importes exigibles de una suscripción suspendida, sin alterar su calendario original.

- **RF-SUS-016** — El sistema permite recontratar dentro de los 180 días de conservación sobre el tenant anterior, iniciar un nuevo ciclo de cobro y habilitar inicialmente solo al administrador principal para reactivar las demás cuentas válidas.

- **RF-SUS-017** — El sistema registra la fecha efectiva de terminación y controla los 180 días de conservación de datos operativos y su posterior eliminación o anonimización conforme a las excepciones legales.

- **RF-SUS-018** — El sistema envía al administrador principal avisos por correo electrónico a los 30 y 7 días anteriores al fin del plazo de conservación y presenta notificaciones internas cuando exista acceso a la cuenta.

- **RF-SUS-019** — El sistema comunica al administrador principal por correo electrónico y notificación interna los pagos confirmados o fallidos, renovaciones próximas, suspensiones, reactivaciones y cambios de contratación o precio.

- **RF-SUS-020** — El sistema emite automáticamente un comprobante no fiscal por cada pago confirmado y lo vincula con la obligación y la suscripción correspondientes.

- **RF-SUS-021** — El sistema conserva para consulta o descarga del administrador principal las referencias y los archivos de CFDI de las suscripciones emitidos fuera de la aplicación por el operador del SaaS.

- **RF-SUS-022** — El sistema mantiene disponible la sección de cuenta y documentos comerciales autorizados para el administrador principal después de terminar la suscripción, sin abrir módulos ni datos operativos.

- **RF-SUS-023** — El sistema registra y permite gestionar por parte del operador una solicitud verificada de exportación de datos conservados de un tenant terminado sin conceder acceso operativo al solicitante.

- **RF-SUS-024** — El sistema registra el historial de cobros, intentos, correcciones y reembolsos de importes indebidamente cobrados sin borrar las transacciones originales.

- **RF-SUS-025** — El sistema presenta al administrador principal los avisos de cambios de precio antes de su aplicación y los incorpora únicamente en la renovación afectada conforme a la regla comercial vigente.

## Requisitos no funcionales (RNF)

- **RNF-SUS-001** — La aplicación verifica de forma segura la procedencia y validez de los eventos de confirmación de la pasarela antes de modificar estados de pago o derechos de acceso.

- **RNF-SUS-002** — El procesamiento de confirmaciones, notificaciones repetidas y reintentos de cobro es idempotente y no genera activaciones ni cargos duplicados por la misma obligación.

- **RNF-SUS-003** — Las transiciones de suscripción, pago y habilitación de módulos mantienen integridad transaccional y no dejan derechos de acceso incoherentes ante un fallo parcial.

- **RNF-SUS-004** — Los usuarios de un tenant no pueden consultar pagos, comprobantes, documentos fiscales ni estados comerciales de otro tenant.

- **RNF-SUS-005** — Las operaciones sobre pagos, regularización, cancelaciones, cambios de precios y reembolsos conservan un historial auditable que identifica al responsable y al evento relacionado.

- **RNF-SUS-006** — Los cálculos de importes, descuentos, prorrateos e impuestos utilizan reglas numéricas coherentes que evitan diferencias injustificadas entre el importe presentado y el importe cobrado.

- **RNF-SUS-007** — Las confirmaciones de pago recibidas con retraso o repetidas se concilian contra el estado persistido de la obligación sin producir activaciones improcedentes.

## Reglas comerciales (RC)

- **RC-SUS-001** — Las suscripciones del SaaS están destinadas exclusivamente a negocios establecidos en México.

- **RC-SUS-002** — Los precios, cobros y comprobantes de suscripción del SaaS se expresan en pesos mexicanos (MXN).

- **RC-SUS-003** — Los precios anunciados del SaaS incluyen los impuestos aplicables y su desglose se presenta en el proceso de compra.

- **RC-SUS-004** — La contratación del SaaS admite periodicidad mensual o anual y utiliza renovaciones automáticas mientras el administrador principal no las cancele.

- **RC-SUS-005** — El nivel base y todos los módulos extra contratados se cobran como conceptos de una suscripción unificada con la misma periodicidad y fecha de renovación.

- **RC-SUS-006** — La modalidad anual aplica un descuento porcentual uniforme respecto de doce mensualidades a los niveles base y módulos extra de todos los giros.

- **RC-SUS-007** — Las tarifas del nivel base pueden variar por giro y nivel, y las de los módulos extra pueden variar por giro pero no por el nivel base contratado.

- **RC-SUS-008** — La tarifa de Multisucursal es fija por tenant dentro de cada giro y no depende de cuántas sucursales se registren.

- **RC-SUS-009** — Las ampliaciones de módulos extra y los aumentos de nivel solicitados durante el periodo pagado se cobran proporcionalmente según los días naturales pendientes hasta la renovación compartida.

- **RC-SUS-010** — Las reducciones de nivel y retiradas de módulos extra se hacen efectivas al terminar el periodo ya pagado, sin reembolso voluntario automático por el tiempo restante.

- **RC-SUS-011** — Los cambios de precios comunicados a un tenant se aplican a los conceptos afectados a partir de su siguiente renovación correspondiente.

- **RC-SUS-012** — La cancelación voluntaria detiene las renovaciones automáticas al terminar el periodo pagado y no genera por sí misma derecho a reembolso de ese periodo.

- **RC-SUS-013** — Los cobros duplicados o efectuados indebidamente se revisan y, una vez confirmados, se corrigen o reembolsan mediante el procedimiento aplicable, conservando el historial.

- **RC-SUS-014** — El cobro de suscripciones se realiza exclusivamente mediante una pasarela externa, seleccionándose una única integración entre Mercado Pago y Stripe tras evaluar su compatibilidad y condiciones.

- **RC-SUS-015** — La renovación impagada tiene una gracia comercial de siete días naturales durante la cual se conserva acceso operativo antes de la suspensión.

- **RC-SUS-016** — Una suscripción impagada y suspendida termina en la siguiente fecha de renovación originalmente establecida si no se ha regularizado el adeudo exigible.

- **RC-SUS-017** — El operador del SaaS establece la política de reintentos automáticos y la política de regularización de importes exigibles por impagos, de forma previa y comunicada al cliente.

- **RC-SUS-018** — La recuperación de un tenant dentro de los 180 días siguientes a la terminación requiere una nueva contratación pagada que inicia un nuevo ciclo de facturación.

- **RC-SUS-019** — El operador del SaaS genera los CFDI correspondientes a las suscripciones mediante un procedimiento externo a la aplicación y conserva dentro de esta las referencias y documentos resultantes.

- **RC-SUS-020** — Cuando corresponda legalmente y no se solicite un CFDI individual de la suscripción, el operador incluye la operación en el mecanismo de facturación global aplicable.

- **RC-SUS-021** — El SaaS no emite CFDI de las ventas propias de los tenants, quienes gestionan sus obligaciones fiscales de venta mediante procesos externos a la plataforma.

- **RC-SUS-022** — La plataforma entrega automáticamente un comprobante de pago no fiscal cuando se confirma cada cobro, sin sustituir por ello la emisión del CFDI que corresponda.

## Pendientes de definición (PT)

- **PT-SUS-001** — Está pendiente seleccionar definitivamente Mercado Pago o Stripe como única pasarela del SaaS después de verificar sus condiciones comerciales y compatibilidad con el flujo de suscripciones.

- **PT-SUS-002** — Está pendiente definir los medios de pago que se habilitarán dentro de la pasarela elegida y comprobar cuáles admiten renovaciones automáticas y cobros extraordinarios.

- **PT-SUS-003** — Está pendiente fijar la cantidad, frecuencia e intervalos de reintentos automáticos y las condiciones operativas de los reintentos manuales durante el periodo de gracia.

- **PT-SUS-004** — Está pendiente establecer y comunicar la política concreta que determina qué importes vencidos son exigibles para reactivar una suscripción suspendida.

- **PT-SUS-005** — Está pendiente definir el tratamiento de días parciales, el denominador de cada periodo, la precisión y el redondeo de los cobros proporcionales.

- **PT-SUS-006** — Está pendiente establecer el porcentaje uniforme de descuento anual y los importes de planes y módulos extra por giro, conservando su definición comercial en el área Planes.

- **PT-SUS-007** — Está pendiente definir la anticipación de los avisos preventivos de renovación, fin de gracia y aumento de precios, sin alterar los avisos ya fijados a 30 y 7 días del fin de la conservación.

- **PT-SUS-008** — Está pendiente concretar qué datos fiscales se solicitarán, qué documentos se conservarán y cómo se vincularán los CFDI emitidos externamente y las operaciones sujetas a facturación global.

- **PT-SUS-009** — Está pendiente determinar los periodos de conservación de comprobantes, CFDI, referencias de cobro y registros de transacciones conforme a las obligaciones que correspondan.

- **PT-SUS-010** — Está pendiente especificar el formato, el procedimiento de autorización y entrega, y las medidas de protección de datos de la exportación solicitada después de terminar la suscripción.

- **PT-SUS-011** — Está pendiente determinar el manejo operativo de devoluciones, aclaraciones y disputas de cobro que no sean errores confirmados, sin introducir una política de reembolso voluntario contraria a lo aprobado.

- **PT-SUS-012** — Está pendiente definir el tratamiento de una confirmación de pago tardía recibida después de la terminación por impago, evitando activar sin una regularización o recontratación válida.
