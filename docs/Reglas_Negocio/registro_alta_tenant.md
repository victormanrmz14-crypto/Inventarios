# Registro, alta y activación del tenant — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene únicamente su identificador y una descripción autónoma; las entradas PT indican asuntos aún no confirmados y no constituyen reglas vigentes.

## Reglas de negocio (RN)

- **RN-ALT-001** — El registro de un nuevo tenant queda asociado a un único giro de los cinco disponibles y, una vez activado, ese giro no puede modificarse.

- **RN-ALT-002** — La cuenta que origina una nueva contratación pertenece exclusivamente al tenant correspondiente y asume la responsabilidad de administrador principal cuando se activa la contratación.

- **RN-ALT-003** — Cada tenant activo cuenta con un único administrador principal responsable de las decisiones comerciales reservadas a ese rol.

- **RN-ALT-004** — Un registro inicial cuyo pago no ha sido confirmado no autoriza el uso operativo del inventario ni de los módulos del tenant.

- **RN-ALT-005** — Una contratación inicial no pagada conserva la información de registro y selección necesaria para retomarla y volver a intentar el pago sin activar el servicio.

- **RN-ALT-006** — La activación inicial requiere una confirmación válida del pago exigible antes de conceder acceso a las funcionalidades seleccionadas.

- **RN-ALT-007** — El acceso inicial del tenant se limita a las funcionalidades incluidas en su giro y nivel base y a los módulos adicionales efectivamente contratados y pagados.

- **RN-ALT-008** — La personalización efectuada antes del pago constituye información preparatoria y no habilita la administración operativa de la configuración del tenant.

- **RN-ALT-009** — Las combinaciones de módulos adicionales seleccionadas durante el alta deben pertenecer al giro elegido y respetar las dependencias funcionales indispensables que lleguen a definirse.

- **RN-ALT-010** — Una dirección de correo ya vinculada a una cuenta existente de la plataforma no puede vincularse a una segunda cuenta durante el registro.

- **RN-ALT-011** — La cuenta de un tenant no puede utilizar sus credenciales para acceder a las operaciones o datos de otro tenant.

- **RN-ALT-012** — Una contratación inicial no activada se distingue de la terminación de una suscripción previamente activa y no adquiere por ese hecho el periodo de conservación previsto para tenants terminados.


## Requisitos funcionales (RF)

- **RF-ALT-001** — La aplicación muestra una landing page pública que presenta el producto y permite acceder a las rutas de registro e inicio de sesión.

- **RF-ALT-002** — La aplicación ofrece un flujo de registro de nuevo tenant y un flujo separado de inicio de sesión para cuentas ya existentes.

- **RF-ALT-003** — El flujo de registro presenta los cinco giros admitidos: abarrotes, farmacia, ferretería, biblioteca y productos electrónicos.

- **RF-ALT-004** — El flujo de registro permite seleccionar el giro del tenant antes de configurar el nivel base y los módulos adicionales de su contratación.

- **RF-ALT-005** — El sistema presenta para el giro seleccionado los niveles Básico, Intermedio y Superior, sus capacidades incluidas y sus límites de usuarios activos.

- **RF-ALT-006** — El sistema distingue durante la selección las funcionalidades incluidas sin costo adicional de los módulos extra que pueden contratarse para el giro elegido.

- **RF-ALT-007** — El sistema permite seleccionar un nivel base y los módulos extra disponibles para el giro y rechaza combinaciones que incumplan las dependencias funcionales que se definan.

- **RF-ALT-008** — El sistema permite capturar la información de personalización inicial del negocio antes del pago sin ofrecer funciones operativas de configuración.

- **RF-ALT-009** — El sistema muestra antes del pago los conceptos seleccionados, la periodicidad de la suscripción, el importe expresado en MXN y el desglose de los impuestos aplicables dentro del precio mostrado.

- **RF-ALT-010** — El sistema dirige la contratación inicial a la única pasarela externa de pagos que resulte seleccionada entre Mercado Pago y Stripe.

- **RF-ALT-011** — El sistema conserva el estado de una contratación inicial pendiente de pago y permite retomar sus selecciones para solicitar otro intento de pago.

- **RF-ALT-012** — El sistema comprueba la confirmación válida del pago de alta antes de habilitar el nivel base y los módulos extra de la contratación inicial.

- **RF-ALT-013** — El sistema impide acceder a las operaciones de inventario y de módulos mientras el alta no cuente con pago confirmado, aunque el registro y sus datos preparatorios permanezcan guardados.

- **RF-ALT-014** — El sistema habilita tras el primer pago confirmado la cuenta del administrador principal y las funcionalidades contratadas que corresponden al giro elegido.

- **RF-ALT-015** — El sistema dirige al administrador principal de una contratación inicial activada al dashboard desde el que puede utilizar la carga CSV incluida y completar la configuración autorizada del tenant.

- **RF-ALT-016** — El inicio de sesión de una cuenta existente dirige su acceso conforme al estado actual de la contratación, sin presentar módulos operativos a cuentas cuyo tenant no los tenga habilitados.

- **RF-ALT-017** — El registro comprueba que el correo electrónico de la nueva cuenta no se encuentre ya asociado a otra cuenta de la plataforma.

- **RF-ALT-018** — El sistema conserva el giro elegido como dato no editable del tenant después de la activación de su primera contratación.

- **RF-ALT-019** — El sistema impide que una misma cuenta se utilice para operar varios tenants, de acuerdo con su asociación única.


## Requisitos no funcionales (RNF)

- **RNF-ALT-001** — La landing page, el registro, la selección comercial, la personalización inicial y el primer dashboard ofrecen una interfaz responsive que puede utilizarse en pantallas de escritorio y dispositivos móviles.

- **RNF-ALT-002** — Las sesiones y solicitudes del proceso de alta impiden consultar o modificar información operativa perteneciente a otro tenant.

- **RNF-ALT-003** — Las notificaciones repetidas o tardías de confirmación de pago no producen activaciones duplicadas de un mismo tenant o de sus módulos contratados.

- **RNF-ALT-004** — El alta mantiene coherentes el estado del pago, la habilitación de la contratación y los derechos de acceso aunque alguna etapa de confirmación falle parcialmente.

- **RNF-ALT-005** — Las áreas operativas están protegidas mediante comprobaciones de autorización basadas en el estado vigente de la contratación y no solo en la existencia de una cuenta registrada.

- **RNF-ALT-006** — Los eventos relevantes de registro, selección comercial, confirmación del primer pago y activación quedan auditados con referencia al tenant y al resultado correspondiente.


## Reglas comerciales (RC)

- **RC-ALT-001** — La contratación inicial comprende obligatoriamente un nivel base del giro seleccionado y permite incorporar los módulos adicionales disponibles que el cliente decida contratar.

- **RC-ALT-002** — El alta del servicio admite una suscripción mensual o anual con precios en pesos mexicanos e impuestos aplicables incluidos, conforme a la oferta comercial vigente.

- **RC-ALT-003** — El alta utiliza exclusivamente una pasarela externa de pago y la elección definitiva entre Mercado Pago y Stripe permanece pendiente.

- **RC-ALT-004** — El servicio se comercializa exclusivamente para negocios establecidos en México, sin que esta restricción defina todavía el mecanismo de verificación.


## Pendientes de definición (PT)

- **PT-ALT-001** — Está pendiente decidir en qué etapa se crea materialmente el registro del tenant frente a una contratación provisional todavía no pagada, sin conceder acceso operativo previo.

- **PT-ALT-002** — Está pendiente delimitar los campos obligatorios y opcionales de los formularios de alta y de la personalización inicial anterior al pago.

- **PT-ALT-003** — Está pendiente definir cómo se entregan y habilitan las credenciales iniciales del administrador principal y qué verificaciones de identidad o correo se exigen específicamente a esa cuenta.

- **PT-ALT-004** — Está pendiente definir el procedimiento con el que se comprobará que el solicitante representa un negocio establecido en México, sin asumir documentos obligatorios no aprobados.

- **PT-ALT-005** — Está pendiente fijar el plazo de conservación y la eliminación de registros de alta que nunca se pagaron, diferenciándolos de los 180 días aplicables tras la terminación de un tenant activo.

- **PT-ALT-006** — Está pendiente confirmar si el solicitante puede cambiar libremente el giro, el nivel o los módulos seleccionados mientras el registro sigue sin activarse y cómo se tratan intentos de pago anteriores.

- **PT-ALT-007** — Está pendiente detallar el contenido informativo de la landing page y los campos visibles de las comparaciones comerciales sin introducir ofertas o promociones no confirmadas.

- **PT-ALT-008** — Está pendiente definir cómo se retoma de forma segura una contratación inconclusa y cómo se identifica al solicitante cuando el correo usado ya pertenece a una cuenta provisional.

- **PT-ALT-009** — Está pendiente delimitar las pantallas de cuenta y contratación disponibles antes del primer pago y la presentación de estados intermedios de confirmación o rechazo del cobro.

- **PT-ALT-010** — Está pendiente determinar si el alta requiere aceptación explícita de condiciones contractuales, aviso de privacidad u otros documentos específicos y cómo se almacena evidencia de dicha aceptación.
