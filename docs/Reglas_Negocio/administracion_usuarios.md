# Administración de usuarios, roles y permisos — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene únicamente su identificador y su descripción autónoma; los PT documentan aspectos sin decisión confirmada.

## Reglas de negocio (RN)

- **RN-USU-001** — Cada cuenta de usuario creada para operar un tenant pertenece a un solo tenant, sin permitir que sus credenciales den acceso a los datos operativos de otro tenant.

- **RN-USU-002** — Cada dirección de correo electrónico está asociada como máximo a una cuenta de usuario en toda la plataforma.

- **RN-USU-003** — Cada tenant tiene exactamente un administrador principal y puede contar con administradores completos adicionales y usuarios limitados.

- **RN-USU-004** — El administrador principal conserva todas las facultades administrativas del tenant y las facultades comerciales o extraordinarias reservadas exclusivamente a ese rol.

- **RN-USU-005** — Los administradores completos tienen acceso administrativo y operativo a todas las sucursales y funcionalidades contratadas del tenant, salvo atribuciones exclusivas del administrador principal.

- **RN-USU-006** — Únicamente el administrador principal puede conceder o retirar a otro usuario el rol de administrador completo.

- **RN-USU-007** — La transferencia ordinaria del rol principal se efectúa a una cuenta activa que ya tenga el rol de administrador completo, y el anterior titular conserva el rol de administrador completo.

- **RN-USU-008** — La cuenta del administrador principal no puede desactivarse antes de efectuar la transferencia válida de su responsabilidad.

- **RN-USU-009** — El superadmin puede designar excepcionalmente como administrador principal a cualquier usuario activo del tenant únicamente mediante una intervención legítima, verificada y auditada.

- **RN-USU-010** — El administrador principal y los administradores completos pueden crear, administrar y asignar permisos a usuarios limitados dentro de las funcionalidades disponibles para el tenant.

- **RN-USU-011** — Un usuario limitado recién creado no recibe permisos operativos hasta que un administrador autorizado los asigne expresamente.

- **RN-USU-012** — Los permisos efectivos de un usuario limitado se restringen a las funcionalidades contratadas y vigentes, las acciones expresamente autorizadas y el ámbito de sucursal que le corresponda.

- **RN-USU-013** — El permiso de edición de una función comprende su consulta necesaria, pero no concede por sí mismo acceso a los costos.

- **RN-USU-014** — Los usuarios sin autorización para consultar costos tampoco pueden obtener importes de costo ni indicadores derivados por pantallas, reportes o exportaciones.

- **RN-USU-015** — Los permisos para ajustes de inventario y para correcciones de movimientos confirmados son autorizaciones especiales diferenciadas de los permisos operativos ordinarios y entre sí.

- **RN-USU-016** — Cada usuario limitado puede recibir un perfil reutilizable de permisos y excepciones individuales que conceden o deniegan acciones específicas.

- **RN-USU-017** — Las excepciones individuales prevalecen sobre los permisos heredados de un perfil, sin anular las restricciones obligatorias del sistema.

- **RN-USU-018** — Los cambios de un perfil reutilizable afectan inmediatamente a todos sus usuarios asociados, salvo los permisos gobernados por excepciones individuales vigentes.

- **RN-USU-019** — Cuando se descontrata un módulo extra o se pierde una capacidad exclusiva de nivel, sus permisos se eliminan de perfiles y asignaciones individuales y no se restauran automáticamente si la función vuelve a estar disponible.

- **RN-USU-020** — Una reducción del nivel base no elimina permisos relativos a operaciones esenciales comunes a los tres planes y solamente afecta las capacidades diferenciadas por nivel y los límites de usuarios acordados.

- **RN-USU-021** — Cada usuario limitado puede tener asignada una sola sucursal cuando está contratado Multisucursal, mientras que los administradores completos mantienen alcance sobre todas las sucursales.

- **RN-USU-022** — Cambiar la sucursal asignada a un usuario limitado modifica inmediatamente su ámbito de acceso sin trasladar ni reasignar las operaciones históricas de la sucursal anterior.

- **RN-USU-023** — Cuando se descontrata Multisucursal, un usuario limitado asociado a una sucursal secundaria mantiene su cuenta activa y su consumo de cupo, pero no puede operar hasta ser reasignado expresamente a la sucursal principal.

- **RN-USU-024** — Al retirar el rol de administrador completo, la cuenta pasa a ser de usuario limitado sin permisos operativos y las sesiones anteriores quedan invalidadas.

- **RN-USU-025** — La revocación de permisos tiene efecto inmediato incluso en sesiones ya iniciadas, y el cambio entre usuario limitado y administrador completo requiere una nueva autenticación.

- **RN-USU-026** — La desactivación de una cuenta impide su acceso, invalida todas sus sesiones y credenciales temporales pendientes y conserva su identidad e historial.

- **RN-USU-027** — La reactivación de una cuenta conserva su rol anterior y restaura únicamente permisos todavía vigentes que no hayan sido revocados ni eliminados.

- **RN-USU-028** — Cuando un tenant terminado vuelve a contratar dentro del periodo de conservación, solo el administrador principal recupera inicialmente el acceso y decide qué otras cuentas reactivar conforme al plan y las funcionalidades vigentes.

- **RN-USU-029** — Los límites de usuarios de los planes contabilizan cuentas activas distintas del administrador principal y excluyen las cuentas pendientes de activación.

- **RN-USU-030** — Si una reducción de nivel o una transferencia del administrador principal deja un número de cuentas activas superior al cupo contratado, estas se conservan activas y se impiden nuevas activaciones hasta recuperar capacidad.

- **RN-USU-031** — Un usuario creado por un administrador debe verificar su correo electrónico y sustituir su contraseña temporal antes de que su cuenta se active, comprobándose en ese momento la disponibilidad de cupo.

- **RN-USU-032** — La contraseña temporal se muestra una sola vez al administrador que la genera, caduca a las 24 horas y pierde validez al utilizarse, vencer o desactivarse la cuenta.

- **RN-USU-033** — La recuperación de contraseña definitiva admite un enlace de un solo uso enviado al correo verificado con vigencia de 30 minutos o el restablecimiento por un administrador autorizado.

- **RN-USU-034** — Los administradores completos pueden restablecer contraseñas de usuarios limitados, mientras que solo el administrador principal puede restablecer credenciales de otros administradores completos.

- **RN-USU-035** — La cuenta del administrador principal solo puede recuperarse mediante el procedimiento autónomo autorizado o mediante intervención extraordinaria verificada del operador del SaaS.

- **RN-USU-036** — Al cambiar la contraseña desde una sesión autenticada se invalidan las sesiones de otros dispositivos y puede conservarse la sesión actual, mientras que una recuperación por correo o intervención administrativa invalida todas las sesiones anteriores.

- **RN-USU-037** — Las sesiones de todos los usuarios expiran después de 15 minutos de inactividad y no se emplea autenticación multifactor.

- **RN-USU-038** — Las operaciones administrativas sensibles requieren reconfirmar la contraseña, incluidos los cambios de rol administrativo, el restablecimiento de contraseñas administrativas, los cambios comerciales, la modificación de datos de recuperación y cualquier alta, cambio o retirada de permisos de usuarios limitados.

- **RN-USU-039** — Toda modificación de roles, permisos, perfiles o asignaciones de sucursal conserva auditoría del responsable, usuario afectado, fecha y hora, valores anteriores y nuevos y sucursales involucradas cuando correspondan.

- **RN-USU-040** — Únicamente el administrador principal puede consultar la auditoría de cambios de roles y permisos del tenant, sin facultad de alterar los registros confirmados.

- **RN-USU-041** — El administrador principal puede consultar los eventos de seguridad de las cuentas del tenant y cada usuario puede consultar los eventos de acceso asociados a su propia cuenta.

- **RN-USU-042** — El correo de una cuenta desactivada permanece reservado mientras esa cuenta exista, y los correos de cuentas pertenecientes a un tenant terminado permanecen reservados durante el periodo de conservación aplicable.

- **RN-USU-043** — El usuario puede cambiar el correo asociado a su cuenta tras confirmar su contraseña y verificar la nueva dirección, manteniéndose el correo anterior hasta que concluya la verificación y comprobándose la unicidad global del nuevo correo.

- **RN-USU-044** — Durante una suspensión por impago los usuarios conservan únicamente la consulta y descarga autorizadas, mientras que la terminación de la suscripción retira su acceso operativo directo sin impedir los accesos excepcionales de cuenta y documentación expresamente previstos.

## Requisitos funcionales (RF)

- **RF-USU-001** — El sistema permite al administrador principal consultar y administrar las cuentas de su tenant y permite a los administradores completos crear, modificar, desactivar y reactivar usuarios limitados según sus facultades autorizadas.

- **RF-USU-002** — El sistema ofrece al administrador principal las acciones exclusivas para conceder y retirar el rol de administrador completo y transferir su responsabilidad a otro administrador completo activo.

- **RF-USU-003** — El sistema impide desactivar al administrador principal sin una transferencia previa válida y permite al superadmin ejecutar una sustitución extraordinaria de titularidad mediante un procedimiento verificado y auditado.

- **RF-USU-004** — El sistema permite configurar para usuarios limitados permisos granulares por módulo y por acción, incluidos ver, consultar costos, crear, editar, descargar, importar, ajustar y corregir cuando esas funciones existan y estén contratadas.

- **RF-USU-005** — El sistema crea los usuarios limitados sin facultades operativas y permite a los administradores autorizados otorgarlas expresamente dentro de los módulos y capacidades disponibles del tenant.

- **RF-USU-006** — El sistema permite crear y actualizar perfiles reutilizables de permisos, asociar un perfil base a cada usuario limitado y conceder o denegar permisos mediante excepciones individuales.

- **RF-USU-007** — El sistema aplica inmediatamente a los usuarios asociados las modificaciones de un perfil, respetando la precedencia de sus excepciones individuales y las restricciones de contratación y de seguridad.

- **RF-USU-008** — El sistema elimina de perfiles y asignaciones individuales los permisos de módulos extra descontratados o capacidades exclusivas perdidas, sin restaurarlos automáticamente al recuperarlos y sin retirar por un cambio de nivel los permisos de operaciones esenciales comunes.

- **RF-USU-009** — El sistema comprueba en cada función y exportación el alcance autorizado de los usuarios y oculta costos e indicadores derivados cuando el usuario carece del permiso específico para consultarlos.

- **RF-USU-010** — El sistema impide a usuarios limitados acceder a la configuración exclusiva de administradores o a las facultades comerciales y extraordinarias reservadas al administrador principal.

- **RF-USU-011** — El sistema permite asignar a cada usuario limitado una única sucursal cuando Multisucursal está habilitado y restringe sus consultas y operaciones al ámbito autorizado.

- **RF-USU-012** — El sistema actualiza inmediatamente la sucursal asignada a un usuario limitado sin alterar las operaciones históricas de la anterior y mantiene a los usuarios de sucursales secundarias sin acceso operativo ordinario cuando Multisucursal se descontrata hasta que sean reasignados.

- **RF-USU-013** — El sistema contabiliza los usuarios activos contra el límite de cinco cuentas en el plan Básico, quince en el Intermedio e ilimitadas en Superior, siempre excluyendo al administrador principal.

- **RF-USU-014** — El sistema impide nuevas activaciones cuando no existen cupos disponibles, sin desactivar automáticamente las cuentas que permanecen activas por una reducción de nivel o transferencia de titularidad.

- **RF-USU-015** — El sistema permite generar una contraseña temporal mostrada una sola vez y válida por 24 horas y exige cambiarla y verificar el correo antes de activar la cuenta de un nuevo usuario.

- **RF-USU-016** — El sistema permite a un administrador autorizado regenerar una contraseña temporal vencida y deshabilita las credenciales temporales anteriores o invalidadas por la desactivación de la cuenta.

- **RF-USU-017** — El sistema permite recuperar una contraseña mediante un enlace de un solo uso al correo verificado, con caducidad de 30 minutos, y mediante el restablecimiento administrativo permitido por la jerarquía de roles.

- **RF-USU-018** — El sistema invalida todas las sesiones anteriores después de una recuperación externa de contraseña y permite conservar únicamente la sesión desde la que se hizo un cambio autenticado de contraseña, cerrando las demás.

- **RF-USU-019** — El sistema cierra las sesiones tras 15 minutos de inactividad, invalida sesiones al desactivar cuentas o cambiar el rol de administrador completo y aplica las revocaciones de permisos inmediatamente.

- **RF-USU-020** — El sistema limita intentos fallidos de inicio de sesión mediante retardos o bloqueos temporales y registra los eventos relevantes de autenticación y recuperación de acceso.

- **RF-USU-021** — El sistema solicita reconfirmar la contraseña antes de transferir la titularidad, cambiar roles administrativos, restablecer credenciales administrativas, modificar contrataciones o datos de recuperación y gestionar cualquier permiso de un usuario limitado.

- **RF-USU-022** — El sistema permite a cada usuario modificar el correo de su propia cuenta tras confirmar la contraseña y verificar la nueva dirección y rechaza direcciones que ya estén asociadas a otra cuenta de la plataforma.

- **RF-USU-023** — El sistema registra el historial de modificaciones de roles, permisos, perfiles y sucursales y permite consultar la auditoría de roles y permisos solo al administrador principal, mientras cada usuario puede consultar sus propios eventos de seguridad de acceso.

- **RF-USU-024** — El sistema conserva cuentas, roles e historiales cuando termina una suscripción y, al confirmarse una nueva contratación recuperable, habilita inicialmente solo al administrador principal para reactivar de manera expresa otras cuentas dentro de las restricciones vigentes.

- **RF-USU-025** — El sistema limita las acciones de los usuarios a consulta y descarga autorizadas durante una suspensión por impago y retira el acceso directo a funciones operativas tras la terminación, manteniendo únicamente las excepciones expresamente autorizadas.

## Requisitos no funcionales (RNF)

- **RNF-USU-001** — La autenticación y autorización impiden que una sesión, cuenta o perfil de un tenant permita consultar o modificar recursos de otro tenant, excepto las intervenciones extraordinarias del superadmin autorizadas y auditadas.

- **RNF-USU-002** — La evaluación de permisos se efectúa sobre el estado vigente de cada cuenta, rol, perfil, excepción individual, contratación y sucursal, sin depender únicamente de privilegios almacenados al inicio de sesión.

- **RNF-USU-003** — Las contraseñas definitivas y temporales se protegen mediante mecanismos seguros que impiden su recuperación en texto claro por administradores y usuarios de la plataforma.

- **RNF-USU-004** — Los enlaces de recuperación y las contraseñas temporales se invalidan conforme a su plazo, uso único o revocación y no pueden volver a utilizarse después de su consumo o caducidad.

- **RNF-USU-005** — Las sesiones afectadas por desactivaciones, restablecimientos externos o cambios del rol administrativo se invalidan efectivamente en las solicitudes posteriores, sin esperar al vencimiento habitual de la sesión.

- **RNF-USU-006** — La plataforma registra y protege contra alteración o eliminación ordinaria los cambios confirmados de roles, permisos y accesos, preservando quién efectuó cada cambio, cuándo ocurrió y cuál fue su efecto.

- **RNF-USU-007** — La consulta de auditorías y eventos de seguridad aplica las restricciones particulares de acceso del administrador principal y de cada usuario sin exponer la actividad privada de otras cuentas.

- **RNF-USU-008** — Los intentos fallidos de autenticación se someten a mecanismos de limitación temporal que reducen los ataques automatizados sin imponer bloqueos permanentes por fallos sucesivos.

## Reglas comerciales (RC)

- **RC-USU-001** — El plan Básico permite cinco usuarios activos adicionales al administrador principal, el Intermedio permite quince y el Superior no establece un límite cuantitativo de usuarios activos.

- **RC-USU-002** — El administrador principal no consume cupo de usuarios activos en ningún plan y todos los demás usuarios activos, incluidos los administradores completos, sí lo consumen.

- **RC-USU-003** — La ampliación de capacidad de usuarios se obtiene mediante un cambio de nivel de plan y no mediante paquetes adicionales de cuentas.

## Pendientes de definición (PT)

- **PT-USU-001** — Está pendiente definir el catálogo definitivo de permisos granulares por módulo y tipo de acción, incluidos los permisos para consultas, ajustes, correcciones, auditorías y operaciones especiales que requieran una autorización diferenciada.

- **PT-USU-002** — Está pendiente decidir si un usuario limitado debe tener una sucursal explícita antes de operar cuando Multisucursal no está contratado y cómo se trata la asignación inicial a la sucursal principal.

- **PT-USU-003** — Está pendiente establecer el método seguro de entrega al usuario de la contraseña temporal que el administrador visualiza una sola vez, sin añadir un canal no aprobado.

- **PT-USU-004** — Está pendiente precisar el procedimiento extraordinario para recuperar la cuenta del administrador principal o la de usuarios que perdieron el control de su correo verificado, incluido el alcance de la verificación de identidad.

- **PT-USU-005** — Está pendiente especificar los requisitos de robustez de contraseñas definitivas, su validación y el tratamiento de claves comprometidas, sin incorporar autenticación multifactor.

- **PT-USU-006** — Está pendiente definir el mecanismo concreto y los parámetros de los retardos y bloqueos temporales por intentos fallidos de autenticación.

- **PT-USU-007** — Está pendiente delimitar la conservación y eliminación de eventos de seguridad y auditorías de roles y permisos, considerando la conservación legal y el ciclo de vida de los tenants terminados.

- **PT-USU-008** — Está pendiente definir el tratamiento de los perfiles reutilizables que se eliminan o desactivan mientras continúan asignados a usuarios, sin asumir una reasignación automática de permisos.

- **PT-USU-009** — Está pendiente definir las reglas de entrega, consulta y protección de los códigos o mensajes vinculados a verificación de correo, cambio de correo y recuperación de acceso, sin dar por aprobados canales alternativos.

- **PT-USU-010** — Está pendiente determinar cómo se presentan, sin otorgar permisos adicionales, las cuentas activas que se encuentran sin acceso operativo por una sucursal deshabilitada o por una suspensión comercial.

- **PT-USU-011** — Está pendiente precisar el procedimiento de verificación del correo y establecimiento de credenciales del administrador principal durante el registro inicial, dado que la obligación de contraseña temporal se definió para los usuarios creados por un administrador del tenant.
