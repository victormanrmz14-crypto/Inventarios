# Planes y contratación de módulos — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene únicamente su identificador y una descripción autónoma; los pendientes identifican asuntos sin decisión confirmada.

## Reglas de negocio (RN)

- **RN-PLA-001** — Cada tenant pertenece a un único giro seleccionado durante el registro y no puede cambiarlo una vez activado.

- **RN-PLA-002** — Cada tenant debe contar con un nivel base contratado para utilizar sus funcionalidades operativas.

- **RN-PLA-003** — Los niveles Básico, Intermedio y Superior conservan las mismas funcionalidades operativas esenciales del giro, sin reservar operaciones esenciales para un nivel superior.

- **RN-PLA-004** — Los cinco giros incluyen inventario, administración del tenant, reportes operativos, configuración y control de stock como funcionalidades generales de todos los niveles.

- **RN-PLA-005** — La carga masiva mediante CSV está incluida por defecto en todos los giros y niveles y no constituye un módulo de contratación independiente.

- **RN-PLA-006** — Los giros de abarrotes, farmacia y ferretería incluyen Ventas en su funcionalidad base, mientras que Biblioteca incluye Préstamos en su funcionalidad base.

- **RN-PLA-007** — Los cinco giros incluyen la gestión de bajas, proveedores o entidades equivalentes y ubicaciones internas como funcionalidades base, con las particularidades ya definidas para cada giro.

- **RN-PLA-008** — Abarrotes y Farmacia incluyen el control de caducidades dentro de sus funcionalidades base y Farmacia incluye el señalamiento de productos sujetos a prescripción.

- **RN-PLA-009** — Todos los niveles permiten registrar una cantidad ilimitada de productos, sin imponer límites por número de registros del catálogo.

- **RN-PLA-010** — El plan Básico admite cinco usuarios activos adicionales al administrador principal, el Intermedio admite quince y el Superior no limita cuantitativamente los usuarios activos.

- **RN-PLA-011** — El administrador principal no consume un cupo de usuarios, mientras que todos los demás usuarios activos, incluidos los administradores completos, sí se contabilizan.

- **RN-PLA-012** — Las cuentas desactivadas y las pendientes de activación no consumen cupo de usuarios del nivel contratado.

- **RN-PLA-013** — Tras una reducción de nivel, los usuarios que ya permanecían activos no se desactivan automáticamente aunque excedan el nuevo límite, pero no se permiten nuevas activaciones hasta que exista capacidad disponible.

- **RN-PLA-014** — La transferencia del rol de administrador principal no desactiva automáticamente ninguna cuenta y somete las activaciones posteriores al límite aplicable después de la transferencia.

- **RN-PLA-015** — Las capacidades que diferencian los niveles se circunscriben a reportes y analítica avanzados, dashboard compartido personalizable y límite de usuarios, sin alterar las operaciones esenciales del giro.

- **RN-PLA-016** — El nivel Intermedio incorpora tendencias, comparaciones e indicadores avanzados sobre las capacidades de informes operativos del nivel Básico.

- **RN-PLA-017** — El nivel Superior incorpora un dashboard compartido personalizable, indicadores configurables y análisis combinados de información de las áreas a las que el tenant tenga derecho de acceso.

- **RN-PLA-018** — Solo el administrador principal y los administradores completos pueden personalizar el dashboard compartido del nivel Superior.

- **RN-PLA-019** — Cuando un tenant reduce de nivel, las configuraciones de dashboard que dejan de estar disponibles se conservan inactivas y no otorgan acceso a las capacidades retiradas.

- **RN-PLA-020** — Los permisos granulares correspondientes a capacidades exclusivas de un nivel que deja de estar contratado se eliminan y no se restauran automáticamente cuando la capacidad vuelve a contratarse.

- **RN-PLA-021** — Las reducciones del nivel base no bloquean ni extinguen operaciones esenciales comunes a los tres niveles, aunque las capacidades analíticas o de dashboard exclusivas del nivel perdido dejan de estar disponibles.

- **RN-PLA-022** — Los módulos adicionales solo pueden contratarse en los giros para los que fueron definidos, sin que su disponibilidad dependa del nivel base seleccionado.

- **RN-PLA-023** — Los módulos adicionales mantienen el mismo alcance funcional en los niveles Básico, Intermedio y Superior, aunque la analítica del nivel contratado puede utilizar datos de los módulos adicionales pagados.

- **RN-PLA-024** — Los módulos adicionales pueden contratarse individualmente, excepto cuando exista una dependencia funcional indispensable y expresamente identificada antes del pago.

- **RN-PLA-025** — No se permite retirar un módulo adicional necesario para otro que continuará contratado sin que el administrador principal autorice expresamente la retirada conjunta de los módulos dependientes.

- **RN-PLA-026** — El acceso operativo ordinario a un módulo adicional cesa al terminar el periodo pagado en que se programa su retirada, sin perjuicio de las excepciones autorizadas para cerrar obligaciones anteriores.

- **RN-PLA-027** — Cuando se recupera una funcionalidad después de una descontratación, los permisos que fueron eliminados requieren asignación expresa y no reaparecen automáticamente.

## Requisitos funcionales (RF)

- **RF-PLA-001** — El sistema presenta durante el registro los cinco giros disponibles y permite seleccionar uno para el nuevo tenant antes de configurar su contratación.

- **RF-PLA-002** — El sistema muestra los niveles Básico, Intermedio y Superior aplicables al giro seleccionado y distingue sus capacidades incluidas, sus límites de usuarios y sus diferencias de analítica.

- **RF-PLA-003** — El sistema identifica en la contratación qué funcionalidades forman parte del nivel base y cuáles son módulos adicionales seleccionables para el giro.

- **RF-PLA-004** — El sistema permite al administrador principal seleccionar un nivel base y los módulos adicionales compatibles antes de calcular el importe de la contratación.

- **RF-PLA-005** — El sistema impide incluir módulos adicionales que no correspondan al giro del tenant y comprueba las dependencias funcionales configuradas antes del pago.

- **RF-PLA-006** — El sistema identifica las dependencias entre módulos adicionales, informa qué módulos requiere cada selección y bloquea las combinaciones funcionalmente inválidas.

- **RF-PLA-007** — El sistema solicita aceptación expresa del administrador principal para retirar conjuntamente los módulos que dependen de otro módulo adicional cuya descontratación se ha solicitado.

- **RF-PLA-008** — El sistema presenta en la cuenta del tenant el nivel base, los módulos adicionales contratados, las capacidades disponibles y los cambios comerciales pendientes de entrar en vigor.

- **RF-PLA-009** — El sistema habilita las operaciones esenciales y la carga CSV de cada giro en los tres niveles sin restricciones derivadas exclusivamente del nivel base.

- **RF-PLA-010** — El sistema contabiliza las cuentas activas excluyendo al administrador principal y aplica el límite de cinco usuarios en Básico, quince en Intermedio y sin límite cuantitativo en Superior.

- **RF-PLA-011** — El sistema impide activar nuevas cuentas cuando se ha alcanzado el cupo, conservando las cuentas que ya estén activas después de una reducción de nivel aunque superen temporalmente el nuevo límite.

- **RF-PLA-012** — El sistema muestra los reportes operativos y sus exportaciones en los tres niveles, habilita tendencias e indicadores avanzados en Intermedio y Superior y habilita el dashboard compartido personalizable y los análisis combinados en Superior.

- **RF-PLA-013** — El sistema permite únicamente al administrador principal y a los administradores completos modificar la personalización compartida del dashboard Superior.

- **RF-PLA-014** — El sistema conserva sin habilitarlas las configuraciones de dashboard que quedan fuera del nivel contratado y elimina de perfiles y usuarios los permisos asociados exclusivamente a capacidades que se pierden.

- **RF-PLA-015** — El sistema permite que los indicadores activos del nivel contratado utilicen datos de módulos adicionales pagados y restringe los datos históricos de módulos retirados a las consultas expresamente autorizadas para administradores.

- **RF-PLA-016** — El sistema permite al administrador principal solicitar un aumento de nivel con efecto después de confirmar el pago proporcional correspondiente y una reducción de nivel programada para el final del periodo pagado.

- **RF-PLA-017** — El sistema permite contratar módulos adicionales durante una suscripción activa, calcula el importe proporcional que corresponda y activa cada módulo solo después de la confirmación válida del pago.

- **RF-PLA-018** — El sistema programa la retirada de módulos adicionales para el final del periodo pagado y, al ejecutarla, bloquea sus operaciones ordinarias sin eliminar su información histórica ni habilitar permisos retirados.

- **RF-PLA-019** — El sistema bloquea los cambios comerciales solicitados por personas distintas del administrador principal, aunque posean el rol de administrador completo.

- **RF-PLA-020** — El sistema conserva el acceso a las operaciones esenciales y a las cuentas activas existentes cuando se aplica una reducción de nivel, sometiendo las nuevas activaciones al límite resultante.

## Requisitos no funcionales (RNF)

- **RNF-PLA-001** — La comprobación de nivel, módulos contratados y capacidades habilitadas se efectúa para cada solicitud sobre el tenant correspondiente, sin permitir accesos a funcionalidades contratadas por otros tenants.

- **RNF-PLA-002** — Los cambios de nivel y de módulos con efecto confirmado o programado se aplican de forma coherente a permisos, accesos, reportes y controles comerciales, sin habilitaciones parciales indebidas.

- **RNF-PLA-003** — Los registros de productos, cuentas, operaciones y configuraciones históricas permanecen íntegros cuando el tenant cambia de nivel o descontrata módulos, con los accesos que correspondan a su estado vigente.

- **RNF-PLA-004** — La aplicación vuelve a comprobar las capacidades de la contratación y los permisos efectivos antes de ejecutar acciones de módulos o dashboards, incluso cuando el usuario conservaba una sesión previa al cambio.

## Reglas comerciales (RC)

- **RC-PLA-001** — La oferta comercial de cada giro se organiza en tres niveles base denominados Básico, Intermedio y Superior.

- **RC-PLA-002** — Las tarifas del nivel base pueden variar según el giro y el nivel elegido.

- **RC-PLA-003** — Los módulos generales, las funciones base del giro y la carga masiva CSV se incluyen en el precio del nivel base sin contratación individual.

- **RC-PLA-004** — Multisucursal es un módulo adicional disponible para los cinco giros y su tarifa es fija por tenant dentro de cada giro, independientemente del número de sucursales y del nivel base.

- **RC-PLA-005** — Biblioteca puede contratar Ventas como módulo adicional, mientras que Préstamos se incluye en su funcionalidad base.

- **RC-PLA-006** — Productos electrónicos puede contratar por separado Ventas, Préstamos y Mantenimiento como módulos adicionales.

- **RC-PLA-007** — Los módulos adicionales pueden tener precios diferentes entre giros, pero el precio de un mismo módulo en un mismo giro no varía por el nivel base del tenant.

- **RC-PLA-008** — Los módulos adicionales se cobran dentro de la misma suscripción del nivel base, con periodicidad y fecha de renovación compartidas.

- **RC-PLA-009** — El tenant puede escoger periodicidad mensual o anual y el porcentaje de descuento anual es uniforme entre giros, niveles base y módulos adicionales.

- **RC-PLA-010** — La incorporación de un módulo adicional durante el periodo vigente genera un cobro proporcional a los días naturales restantes antes de la siguiente renovación.

- **RC-PLA-011** — El aumento de nivel entra en vigor al confirmarse el cobro proporcional correspondiente a los días naturales restantes del periodo vigente.

- **RC-PLA-012** — La reducción de nivel y la retirada de módulos adicionales entran en vigor al finalizar el periodo pagado y no generan automáticamente una devolución voluntaria de importes.

- **RC-PLA-013** — La contratación, ampliación, reducción y cancelación de los conceptos comerciales del tenant requiere autorización de su administrador principal.

- **RC-PLA-014** — No se venden paquetes adicionales de capacidad de usuarios y el aumento del cupo disponible se realiza mediante un cambio de nivel.

- **RC-PLA-015** — Un módulo adicional no modifica las capacidades operativas propias de su función por contratarse desde un nivel superior, aunque los reportes avanzados del nivel pueden utilizar sus datos autorizados.

- **RC-PLA-016** — El acceso a las funcionalidades del nivel base y los módulos adicionales se habilita tras confirmar el pago correspondiente y no por el mero registro o selección de conceptos durante la compra.

## Pendientes de definición (PT)

- **PT-PLA-001** — Está pendiente definir los importes en MXN de los tres niveles base para cada uno de los cinco giros.

- **PT-PLA-002** — Está pendiente establecer las tarifas en MXN de cada módulo adicional para los giros en que esté disponible.

- **PT-PLA-003** — Está pendiente fijar el porcentaje común del descuento aplicable a la periodicidad anual de los niveles base y módulos adicionales.

- **PT-PLA-004** — Está pendiente determinar si existe alguna dependencia funcional indispensable entre módulos adicionales y, de existir, enumerar expresamente las combinaciones requeridas por giro.

- **PT-PLA-005** — Está pendiente definir el catálogo exacto de tendencias, comparaciones e indicadores avanzados del nivel Intermedio, sin atribuirle operaciones esenciales exclusivas.

- **PT-PLA-006** — Está pendiente especificar las opciones, indicadores configurables y límites de personalización del dashboard compartido del nivel Superior.

- **PT-PLA-007** — Está pendiente precisar el alcance de la consulta histórica reservada a administradores sobre capacidades analíticas retiradas por reducción de nivel, evitando que esa consulta equivalga a reactivar permanentemente prestaciones del nivel anterior.

- **PT-PLA-008** — Está pendiente definir el tratamiento de solicitudes comerciales sucesivas o incompatibles que se efectúen antes de que entre en vigor un cambio de nivel o de módulos ya programado.

- **PT-PLA-009** — Está pendiente especificar el tratamiento de configuraciones históricas de módulos adicionales cuando estos se vuelven a contratar, sin dar por aprobada la restauración automática de permisos eliminados.

- **PT-PLA-010** — Está pendiente definir la precisión, el redondeo y el tratamiento de fracciones de día para los cobros proporcionales, manteniendo el criterio de días naturales acordado.
