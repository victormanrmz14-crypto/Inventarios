# Superadministración de la plataforma — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Las entradas RN, RF y RNF recogen únicamente comportamientos confirmados o derivados directamente de las decisiones aprobadas; las entradas PT identifican asuntos sin definición y no autorizan funcionalidades nuevas.

## Reglas de negocio (RN)

- **RN-SAD-001** — El superadmin administra el ámbito general del SaaS mediante un rol distinto del administrador principal, de los administradores completos y de los usuarios limitados de cada tenant.

- **RN-SAD-002** — Toda intervención del superadmin que afecte a un tenant debe ser extraordinaria, legítima, verificada y auditada, sin constituir una autorización general para utilizar los datos operativos de otros tenants.

- **RN-SAD-003** — El superadmin puede designar excepcionalmente como nuevo administrador principal a cualquier usuario activo del tenant afectado, aunque ese usuario no tenga previamente el rol de administrador completo.

- **RN-SAD-004** — La designación excepcional de un administrador principal no modifica la pertenencia de las cuentas a su tenant ni permite que los usuarios de ese tenant accedan a información de otros tenants.

- **RN-SAD-005** — Los cambios extraordinarios de titularidad realizados por el superadmin deben quedar vinculados al tenant afectado, a la cuenta designada, al responsable de la intervención y al historial auditable del cambio de rol.

## Requisitos funcionales (RF)

- **RF-SAD-001** — El sistema identifica y autoriza las acciones del superadmin mediante un rol de alcance general diferenciado de los roles internos de cada tenant.

- **RF-SAD-002** — El sistema permite al superadmin sustituir excepcionalmente al administrador principal de un tenant mediante una intervención verificada y auditada.

- **RF-SAD-003** — El sistema comprueba que la cuenta elegida para una sustitución extraordinaria del administrador principal esté activa y pertenezca al mismo tenant afectado antes de ejecutar el cambio.

- **RF-SAD-004** — El sistema permite ejecutar una sustitución extraordinaria del administrador principal con un usuario activo que no sea administrador completo, sin aplicar la condición prevista para una transferencia ordinaria.

- **RF-SAD-005** — El sistema registra cada sustitución extraordinaria con identificación del superadmin responsable, tenant afectado, cuentas y roles involucrados, momento de ejecución y justificación de la intervención.

- **RF-SAD-006** — El sistema aplica de forma inmediata el resultado de un cambio extraordinario de titularidad a la autorización de las cuentas afectadas y evita mantener sesiones con privilegios anteriores incompatibles con el nuevo rol.

## Requisitos no funcionales (RNF)

- **RNF-SAD-001** — Las solicitudes del superadmin que afecten a un tenant están sujetas a controles de autorización y verificación de la intervención extraordinaria sin suprimir el aislamiento de información entre tenants.

- **RNF-SAD-002** — Las intervenciones extraordinarias del superadmin conservan una trazabilidad íntegra y resistente a modificaciones no autorizadas por usuarios del tenant, incluidos sus administradores.

- **RNF-SAD-003** — Los cambios extraordinarios de titularidad se aplican coherentemente a los privilegios efectivos y a las sesiones de las cuentas afectadas, evitando accesos con roles obsoletos.

## Reglas comerciales (RC)

No se identificaron reglas comerciales exclusivas del rol superadmin ya confirmadas; las políticas de precios, cobros y regularización aprobadas corresponden al área de suscripciones y al operador del SaaS, sin que se haya determinado que sean facultades de esta cuenta.

## Pendientes de definición (PT)

- **PT-SAD-001** — Está pendiente delimitar las funciones ordinarias de superadministración de la plataforma, como la consulta de tenants y la gestión de sus estados, sin asumir que se pueden modificar, suspender o eliminar tenants desde este rol.

- **PT-SAD-002** — Está pendiente definir si el superadmin y el operador del SaaS son el mismo actor operativo y qué facultades del operador corresponden realmente al rol superadmin.

- **PT-SAD-003** — Está pendiente establecer las evidencias, verificaciones de identidad y controles requeridos para autorizar una sustitución extraordinaria del administrador principal.

- **PT-SAD-004** — Está pendiente definir las circunstancias legítimas que habilitan una intervención extraordinaria y el procedimiento para documentar su justificación y eventual autorización adicional.

- **PT-SAD-005** — Está pendiente determinar quién puede consultar la bitácora de actuaciones del superadmin y qué parte de esos eventos debe ser visible al administrador principal del tenant afectado.

- **PT-SAD-006** — Está pendiente precisar el procedimiento de recuperación del administrador principal cuando no puede acceder a su correo o a su cuenta y cómo se solicita la intervención extraordinaria del operador.

- **PT-SAD-007** — Está pendiente determinar cómo se crean, asignan, recuperan, desactivan y protegen las cuentas con rol superadmin, sin extenderles automáticamente los procedimientos de usuarios de tenants.

- **PT-SAD-008** — Está pendiente decidir si el superadmin contará con indicadores o reportes globales de la plataforma y, de ser así, cuáles podrán utilizar datos agregados sin exponer información individual de tenants.

- **PT-SAD-009** — Está pendiente definir si el superadmin dispondrá de herramientas para configurar precios, catálogo comercial, pasarela y políticas de cobro del operador del SaaS o si esos procesos se administrarán fuera de su interfaz.

- **PT-SAD-010** — Está pendiente establecer el tratamiento de una intervención extraordinaria fallida, disputada o solicitada por error, incluidas las medidas de reversión y sus restricciones.

- **PT-SAD-011** — Está pendiente precisar las condiciones de sustitución de titularidad cuando un tenant está suspendido, terminado o carece de usuarios activos, sin dar por posible nombrar a una cuenta que no cumple la condición de actividad ya aprobada.

- **PT-SAD-012** — Está pendiente definir la conservación y eliminación de las bitácoras de actuaciones del superadmin conforme a las obligaciones aplicables y al ciclo de vida de los tenants.
