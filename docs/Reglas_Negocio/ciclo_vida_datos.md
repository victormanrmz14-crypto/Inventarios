# Área 26 — Conservación, recuperación y eliminación de datos

**Versión:** 1.0  
**Estado:** Pendiente de aprobación.  
**Formato:** identificador y descripción completa por entrada.

Esta área organiza requisitos vigentes de áreas anteriormente aprobadas; los identificadores reutilizados conservan su definición original y **no se contabilizan nuevamente** en el catálogo consolidado.
Las únicas entradas nuevas son `PT-DAT-001` y `PT-DAT-002`, que representan cuestiones **no resueltas**, no requisitos aprobados.

## Reglas de negocio (RN)

- **RN-SUS-015** — Al terminar una suscripción se bloquea el acceso directo a los módulos y datos operativos, sin impedir las funciones de cuenta, contratación y documentación expresamente permitidas.

- **RN-SUS-016** — Los datos operativos de un tenant cuya suscripción ha terminado permanecen conservados durante 180 días naturales contados desde la terminación, sin perjuicio de los plazos legales aplicables a información específica.

- **RN-SUS-017** — Al completar los 180 días posteriores a la terminación sin recontratación se eliminan o anonimizan los datos operativos mediante un procedimiento controlado, salvo información sujeta a conservación legal.

- **RN-SUS-018** — La recontratación confirmada dentro del periodo de conservación recupera el mismo tenant y sus datos conservados e inicia un nuevo periodo de facturación desde el pago confirmado.

- **RN-SUS-019** — Tras recuperar un tenant terminado solo el administrador principal obtiene acceso inicialmente, mientras las demás cuentas y sus roles se conservan inactivos hasta su reactivación expresa conforme a la nueva contratación.

- **RN-SUS-021** — Durante los 180 días de conservación el administrador principal puede solicitar al operador del SaaS una exportación controlada de la información conservada sin reactivar el acceso operativo.

- **RN-SUS-022** — La exportación posterior a la terminación exige verificación de identidad e incluye catálogos, movimientos, históricos, relaciones y documentos operativos disponibles sin exponer datos de otros tenants ni secretos internos de la plataforma.

- **RN-SUS-024** — Los comprobantes y documentos fiscales de la suscripción permanecen consultables y descargables por el administrador principal desde la sección de cuenta durante los plazos de conservación aplicables aunque el servicio operativo haya terminado.

- **RN-AUD-004** — La conservación, anonimización o eliminación legalmente procedente de registros auditables solo puede ejecutarse mediante un procedimiento controlado, sin autorizar su manipulación ordinaria por los usuarios del tenant.

- **RN-USU-042** — El correo de una cuenta desactivada permanece reservado mientras esa cuenta exista, y los correos de cuentas pertenecientes a un tenant terminado permanecen reservados durante el periodo de conservación aplicable.

- **RN-PLA-026** — El acceso operativo ordinario a un módulo adicional cesa al terminar el periodo pagado en que se programa su retirada, sin perjuicio de las excepciones autorizadas para cerrar obligaciones anteriores.

- **RN-REP-015** — Los historiales de funcionalidades perdidas por una reducción de nivel o por la descontratación de un módulo extra solo pueden consultarlos el administrador principal y los administradores completos, sin reactivar operaciones ordinarias de esas funcionalidades.

- **RN-MSU-018** — La retirada de Multisucursal conserva el historial y las existencias identificadas de las sucursales secundarias, sin trasladarlas automáticamente a la sucursal principal ni habilitarlas para operaciones ordinarias.

## Requisitos funcionales (RF)

- **RF-SUS-016** — El sistema permite recontratar dentro de los 180 días de conservación sobre el tenant anterior, iniciar un nuevo ciclo de cobro y habilitar inicialmente solo al administrador principal para reactivar las demás cuentas válidas.

- **RF-SUS-017** — El sistema registra la fecha efectiva de terminación y controla los 180 días de conservación de datos operativos y su posterior eliminación o anonimización conforme a las excepciones legales.

- **RF-SUS-018** — El sistema envía al administrador principal avisos por correo electrónico a los 30 y 7 días anteriores al fin del plazo de conservación y presenta notificaciones internas cuando exista acceso a la cuenta.

- **RF-SUS-021** — El sistema conserva para consulta o descarga del administrador principal las referencias y los archivos de CFDI de las suscripciones emitidos fuera de la aplicación por el operador del SaaS.

- **RF-SUS-022** — El sistema mantiene disponible la sección de cuenta y documentos comerciales autorizados para el administrador principal después de terminar la suscripción, sin abrir módulos ni datos operativos.

- **RF-SUS-023** — El sistema registra y permite gestionar por parte del operador una solicitud verificada de exportación de datos conservados de un tenant terminado sin conceder acceso operativo al solicitante.

- **RF-USU-024** — El sistema conserva cuentas, roles e historiales cuando termina una suscripción y, al confirmarse una nueva contratación recuperable, habilita inicialmente solo al administrador principal para reactivar de manera expresa otras cuentas dentro de las restricciones vigentes.

- **RF-REP-014** — El sistema mantiene la visualización y exportación autorizadas de reportes durante la suspensión por impago e impide el acceso directo a los reportes operativos cuando la suscripción está terminada.

- **RF-PLA-018** — El sistema programa la retirada de módulos adicionales para el final del periodo pagado y, al ejecutarla, bloquea sus operaciones ordinarias sin eliminar su información histórica ni habilitar permisos retirados.

- **RF-MSU-012** — El sistema deshabilita las operaciones ordinarias de las sucursales secundarias al terminar la contratación de Multisucursal y conserva sus existencias, sus ubicaciones internas y sus historiales para los accesos autorizados.

## Requisitos no funcionales (RNF)

- **RNF-SEG-001** — El aislamiento entre tenants se aplica también al acceso a archivos, documentos asociados, descargas y resultados de exportación, de manera que la información de un negocio no pueda obtenerse mediante solicitudes de otro.

- **RNF-SEG-002** — La entrega de archivos y documentos sujetos a permisos verifica las autorizaciones y el estado de acceso vigentes en el momento de la solicitud, incluso cuando el documento o la exportación se hayan preparado previamente.

- **RNF-PLA-003** — Los registros de productos, cuentas, operaciones y configuraciones históricas permanecen íntegros cuando el tenant cambia de nivel o descontrata módulos, con los accesos que correspondan a su estado vigente.

- **RNF-SUS-004** — Los usuarios de un tenant no pueden consultar pagos, comprobantes, documentos fiscales ni estados comerciales de otro tenant.

- **RNF-AUD-001** — Los registros de auditoría confirmados se mantienen protegidos frente a modificaciones o eliminaciones ordinarias de los usuarios del tenant y preservan la integridad de su historial.

- **RNF-REP-004** — El sistema vuelve a verificar los permisos y el estado de la suscripción antes de entregar un reporte o una exportación, incluso cuando la consulta se preparó antes de un cambio de autorización.

## Reglas comerciales (RC)

- **RC-SUS-018** — La recuperación de un tenant dentro de los 180 días siguientes a la terminación requiere una nueva contratación pagada que inicia un nuevo ciclo de facturación.

- **RC-SUS-019** — El operador del SaaS genera los CFDI correspondientes a las suscripciones mediante un procedimiento externo a la aplicación y conserva dentro de esta las referencias y documentos resultantes.

## Pendientes de definición (PT)

- **PT-SUS-009** — Está pendiente determinar los periodos de conservación de comprobantes, CFDI, referencias de cobro y registros de transacciones conforme a las obligaciones que correspondan.

- **PT-SUS-010** — Está pendiente especificar el formato, el procedimiento de autorización y entrega, y las medidas de protección de datos de la exportación solicitada después de terminar la suscripción.

- **PT-SEG-005** — Está pendiente definir los plazos de conservación y supresión de datos personales de lectores, destinatarios de préstamos, técnicos y otras personas externas durante la vida del tenant y después de su terminación, respetando los 180 días de datos operativos y las excepciones aplicables.

- **PT-SEG-006** — Está pendiente establecer cómo se aplicará la eliminación o anonimización controlada de información cuando existan respaldos, copias o archivos asociados y qué excepciones de conservación correspondan.

- **PT-SEG-008** — Está pendiente definir la política técnica de respaldos y recuperación ante fallos, incluidos frecuencia, retención, pruebas de restauración, separación entre tenants y responsabilidades de operación.

- **PT-SEG-011** — Está pendiente definir las restricciones de acceso, conservación y entrega de archivos adjuntos u otros documentos que puedan contener datos personales, sin presuponer que todos los módulos permiten adjuntar documentos.

- **PT-AUD-004** — Está pendiente definir los periodos de retención y la eliminación o anonimización de registros de auditoría, incluyendo las excepciones legales y su relación con los 180 días de conservación operativa de los tenants terminados.

- **PT-ALT-005** — Está pendiente fijar el plazo de conservación y la eliminación de registros de alta que nunca se pagaron, diferenciándolos de los 180 días aplicables tras la terminación de un tenant activo.

- **PT-REP-009** — Está pendiente establecer las modalidades de entrega o conservación temporal de archivos exportados y las restricciones aplicables a descargas diferidas, sin asumir programación recurrente de reportes.

- **PT-USU-007** — Está pendiente delimitar la conservación y eliminación de eventos de seguridad y auditorías de roles y permisos, considerando la conservación legal y el ciclo de vida de los tenants terminados.

- **PT-PLA-009** — Está pendiente especificar el tratamiento de configuraciones históricas de módulos adicionales cuando estos se vuelven a contratar, sin dar por aprobada la restauración automática de permisos eliminados.

- **PT-DAT-001** — Está pendiente definir cómo se autorizará y acreditará la ejecución de la eliminación o anonimización al cumplirse el plazo de conservación, así como la evidencia mínima de cumplimiento que podrá retenerse sin conservar innecesariamente los datos suprimidos.

- **PT-DAT-002** — Está pendiente definir el tratamiento de una solicitud de exportación verificada y recibida dentro de los 180 días cuando la entrega de la información no se complete antes de vencer ese plazo, sin presumir una prórroga automática de conservación.

## Revisión de consistencia con áreas previamente aprobadas

- **Suscripciones y Planes:** el plazo de 180 días se aplica a los datos operativos desde la terminación efectiva de una suscripción; no se atribuye automáticamente a registros iniciales nunca activados ni a documentos con conservación legal propia.
- **Usuarios y Permisos:** la recontratación dentro del plazo recupera el mismo tenant, pero habilita inicialmente solo al administrador principal y no restaura permisos eliminados ni módulos no contratados.
- **Reportes:** durante la suspensión por impago sigue permitida la consulta o descarga autorizada; tras la terminación no se abre acceso directo a reportes operativos y la entrega de datos conservados se tramita mediante solicitud verificada al operador.
- **Seguridad y Auditoría:** la eliminación controlada no autoriza manipular bitácoras; las excepciones de conservación, los datos personales, los respaldos y la supresión técnica conservan sus pendientes específicos.
- **Multisucursal:** retirar el módulo conserva existencias e historiales de sucursales secundarias, lo que no debe confundirse con la eliminación de datos posterior a la terminación completa del tenant.
- **Resultado:** no se detectaron contradicciones críticas nuevas; los procedimientos y plazos no confirmados se mantienen como pendientes.

## Control de duplicaciones y asuntos abiertos

- **Referencias vigentes:** 42 entradas preexistentes en otras áreas, reproducidas sin nuevos identificadores.
- **Nuevos pendientes:** `PT-DAT-001` y `PT-DAT-002`.
- **Sin nuevas reglas normativas:** no se han definido nuevas RN, RF, RNF o RC en esta área.
- **Colisión histórica pendiente del catálogo completo:** los IDs `PRE` se reutilizaron en Préstamos y Prescripciones médicas; esta área no los renumera y conserva la necesidad de corregirlos con trazabilidad antes de la consolidación final.
