# Área 23 — Seguridad, privacidad y protección de datos

**Versión:** 1.0  
**Estado:** Pendiente de aprobación.  
**Formato:** identificador y descripción autónoma por entrada; los PT no constituyen decisiones aprobadas.

Esta área agrupa únicamente obligaciones transversales adicionales y señala requisitos ya aprobados que se aplican también a seguridad y privacidad. Los identificadores reutilizados se muestran sin crear requisitos duplicados y no se suman nuevamente al catálogo global.

## Reglas de negocio (RN)

- **RN-SEG-001** — Los lectores de biblioteca, los destinatarios de préstamos de electrónicos y los técnicos de mantenimiento son personas registradas para operaciones del negocio y no adquieren cuentas de acceso al SaaS por el solo hecho de estar registrados.

## Requisitos funcionales (RF)

- **RF-SEG-001** — El sistema mantiene diferenciados los registros operativos de lectores, destinatarios de préstamos y técnicos de mantenimiento respecto de las cuentas de usuarios del tenant y no les concede credenciales de inicio de sesión al registrar sus datos operativos.

## Requisitos no funcionales (RNF)

- **RNF-SEG-001** — El aislamiento entre tenants se aplica también al acceso a archivos, documentos asociados, descargas y resultados de exportación, de manera que la información de un negocio no pueda obtenerse mediante solicitudes de otro.

- **RNF-SEG-002** — La entrega de archivos y documentos sujetos a permisos verifica las autorizaciones y el estado de acceso vigentes en el momento de la solicitud, incluso cuando el documento o la exportación se hayan preparado previamente.

## Reglas comerciales (RC)

No se identifican reglas comerciales nuevas exclusivas de esta área; las condiciones de suscripción, conservación y entrega siguen vigentes en las áreas ya aprobadas.

## Pendientes de definición (PT)

- **PT-SEG-001** — Está pendiente identificar el conjunto mínimo de datos personales que cada giro necesita almacenar sobre lectores, destinatarios de préstamos, técnicos y otras personas externas, así como cuáles campos son opcionales.

- **PT-SEG-002** — Está pendiente determinar las responsabilidades relativas al tratamiento de datos personales entre el operador del SaaS, cada tenant y los prestadores externos que intervengan, sin presuponer una distribución jurídica específica.

- **PT-SEG-003** — Está pendiente definir el aviso de privacidad, los mecanismos de información o aceptación que correspondan y las evidencias que deban conservarse durante el alta y uso del SaaS.

- **PT-SEG-004** — Está pendiente establecer el procedimiento para atender solicitudes relacionadas con los derechos de los titulares de datos personales, identificando responsables, verificaciones y límites frente a historiales que deben conservarse.

- **PT-SEG-005** — Está pendiente definir los plazos de conservación y supresión de datos personales de lectores, destinatarios de préstamos, técnicos y otras personas externas durante la vida del tenant y después de su terminación, respetando los 180 días de datos operativos y las excepciones aplicables.

- **PT-SEG-006** — Está pendiente establecer cómo se aplicará la eliminación o anonimización controlada de información cuando existan respaldos, copias o archivos asociados y qué excepciones de conservación correspondan.

- **PT-SEG-007** — Está pendiente seleccionar las medidas técnicas de protección del tráfico y los datos almacenados, incluidos los mecanismos de cifrado que correspondan y la administración de secretos y claves, sin dar por aprobada una tecnología concreta.

- **PT-SEG-008** — Está pendiente definir la política técnica de respaldos y recuperación ante fallos, incluidos frecuencia, retención, pruebas de restauración, separación entre tenants y responsabilidades de operación.

- **PT-SEG-009** — Está pendiente establecer el procedimiento de respuesta ante incidentes de seguridad y exposición de datos, incluidas responsabilidades de investigación, escalamiento, conservación de evidencias y comunicaciones que resulten aplicables.

- **PT-SEG-010** — Está pendiente determinar qué personas y roles podrán acceder a información personal identificada en las pantallas operativas, aparte de los permisos especiales ya establecidos para la consulta detallada de personas en reportes.

- **PT-SEG-011** — Está pendiente definir las restricciones de acceso, conservación y entrega de archivos adjuntos u otros documentos que puedan contener datos personales, sin presuponer que todos los módulos permiten adjuntar documentos.

- **PT-SEG-012** — Está pendiente evaluar los flujos de información personal hacia la pasarela de pagos, servicios de correo, alojamiento y otros proveedores externos antes de establecer integraciones y condiciones de tratamiento.

## Requisitos vigentes de otras áreas (sin nuevo identificador ni duplicación en el catálogo final)

Las siguientes entradas reproducen el contenido ya aprobado para dejar claro su alcance transversal; no introducen decisiones adicionales.

### Reglas de negocio (RN)

- **RN-USU-001** — Cada cuenta de usuario creada para operar un tenant pertenece a un solo tenant, sin permitir que sus credenciales den acceso a los datos operativos de otro tenant.

- **RN-USU-012** — Los permisos efectivos de un usuario limitado se restringen a las funcionalidades contratadas y vigentes, las acciones expresamente autorizadas y el ámbito de sucursal que le corresponda.

- **RN-USU-037** — Las sesiones de todos los usuarios expiran después de 15 minutos de inactividad y no se emplea autenticación multifactor.

- **RN-USU-040** — Únicamente el administrador principal puede consultar la auditoría de cambios de roles y permisos del tenant, sin facultad de alterar los registros confirmados.

- **RN-REP-011** — La información personal de lectores o destinatarios de préstamos se presenta de forma agregada cuando el reporte no requiere identificar individualmente a las personas.

- **RN-REP-012** — La consulta de detalles personales de lectores o destinatarios de préstamos mediante reportes exige un permiso específico y una finalidad justificada.

- **RN-SUS-016** — Los datos operativos de un tenant cuya suscripción ha terminado permanecen conservados durante 180 días naturales contados desde la terminación, sin perjuicio de los plazos legales aplicables a información específica.

- **RN-SUS-017** — Al completar los 180 días posteriores a la terminación sin recontratación se eliminan o anonimizan los datos operativos mediante un procedimiento controlado, salvo información sujeta a conservación legal.

- **RN-SUS-022** — La exportación posterior a la terminación exige verificación de identidad e incluye catálogos, movimientos, históricos, relaciones y documentos operativos disponibles sin exponer datos de otros tenants ni secretos internos de la plataforma.

- **RN-AUD-003** — Los registros de auditoría confirmados son inalterables para los usuarios del tenant, incluidos el administrador principal y los administradores completos.

- **RN-SAD-002** — Toda intervención del superadmin que afecte a un tenant debe ser extraordinaria, legítima, verificada y auditada, sin constituir una autorización general para utilizar los datos operativos de otros tenants.

### Requisitos funcionales (RF)

- **RF-USU-009** — El sistema comprueba en cada función y exportación el alcance autorizado de los usuarios y oculta costos e indicadores derivados cuando el usuario carece del permiso específico para consultarlos.

- **RF-USU-019** — El sistema cierra las sesiones tras 15 minutos de inactividad, invalida sesiones al desactivar cuentas o cambiar el rol de administrador completo y aplica las revocaciones de permisos inmediatamente.

- **RF-REP-010** — El sistema ofrece vistas de información agregada de lectores o destinatarios de préstamos y solo muestra detalles personales cuando el usuario dispone de la autorización específica correspondiente.

- **RF-SUS-023** — El sistema registra y permite gestionar por parte del operador una solicitud verificada de exportación de datos conservados de un tenant terminado sin conceder acceso operativo al solicitante.

### Requisitos no funcionales (RNF)

- **RNF-USU-001** — La autenticación y autorización impiden que una sesión, cuenta o perfil de un tenant permita consultar o modificar recursos de otro tenant, excepto las intervenciones extraordinarias del superadmin autorizadas y auditadas.

- **RNF-USU-003** — Las contraseñas definitivas y temporales se protegen mediante mecanismos seguros que impiden su recuperación en texto claro por administradores y usuarios de la plataforma.

- **RNF-REP-002** — Los controles de acceso y de visibilidad de costos se aplican también a cálculos intermedios, totales, columnas y archivos exportados, sin exponer información restringida por vías indirectas.

- **RNF-SUS-004** — Los usuarios de un tenant no pueden consultar pagos, comprobantes, documentos fiscales ni estados comerciales de otro tenant.

- **RNF-AUD-002** — Los registros de auditoría y su acceso respetan el aislamiento entre tenants y las restricciones de consulta específicas de cada tipo de evento.

## Revisión de consistencia

- **Usuarios y roles:** se conserva el acceso por credenciales sin MFA, la revocación inmediata, la caducidad de sesiones después de 15 minutos de inactividad y el permiso específico para ver costos; esta área no modifica el alcance de esos controles.
- **Préstamos, Mantenimiento y Biblioteca:** lectores, destinatarios de préstamos y técnicos son registros de personas, no usuarios del SaaS; su información personal operativa no concede permisos de acceso.
- **Prescripciones médicas:** la plataforma registra un indicador y la confirmación del aviso de venta, sin almacenar el contenido de las recetas ni efectuar validaciones clínicas.
- **Suscripciones:** los datos operativos se conservan 180 días naturales después de la terminación, salvo información con plazos aplicables distintos; la exportación extraordinaria se gestiona con verificación de identidad y sin reactivar el servicio.
- **Reportes:** la presentación agregada de datos de lectores y prestatarios y la consulta identificada con permiso y finalidad justificada permanecen vigentes.
- **Auditoría:** no se habilita la edición o eliminación ordinaria de bitácoras y su retención específica permanece por definir.
- **Resultado funcional:** no se detectan contradicciones nuevas en el comportamiento del sistema respecto de las áreas aprobadas; los aspectos técnicos, de privacidad y de retención no decididos permanecen como PT.

## Hallazgo de integridad del catálogo global

Los archivos aprobados de **Préstamos** y **Prescripciones médicas** comparten el prefijo `PRE` y contienen identificadores idénticos con descripciones diferentes, por ejemplo `RN-PRE-001` y `RF-PRE-001`; esta colisión no es una contradicción funcional, pero debe resolverse mediante una renumeración trazable antes de generar el catálogo consolidado y su matriz de trazabilidad.

**Control de cambios:** esta área no modifica las reglas de ninguna sección aprobada ni renumera identificadores previos; la corrección de colisiones se deja identificada para la fase de consolidación.
