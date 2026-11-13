# Configuración del tenant — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Cada entrada contiene exclusivamente su identificador y una descripción autónoma; los PT registran decisiones todavía no confirmadas.

## Reglas de negocio (RN)

- **RN-CFG-001** — Cada tenant puede modificar su nombre comercial, logotipo, domicilio y datos de contacto sin alterar la identidad de los registros históricos asociados a su organización.

- **RN-CFG-002** — El giro seleccionado al activar un tenant no puede modificarse mediante la configuración posterior del negocio.

- **RN-CFG-003** — El identificador interno del tenant permanece invariable aunque se modifiquen sus datos descriptivos o de contacto.

- **RN-CFG-004** — Solo el administrador principal y los administradores completos pueden consultar y modificar la configuración del tenant; los usuarios limitados no tienen acceso a esta sección.

- **RN-CFG-005** — Las configuraciones de un tenant no pueden anular las restricciones obligatorias de seguridad, inventario, permisos, contratación y operación impuestas por la plataforma.

- **RN-CFG-006** — Los cambios de políticas operativas configurables se aplican a las operaciones iniciadas después de su entrada en vigor y no modifican retroactivamente las condiciones de operaciones anteriores.

- **RN-CFG-007** — Toda modificación confirmada de configuración conserva el valor anterior, el valor nuevo, el responsable y la fecha y hora del cambio.

- **RN-CFG-008** — La configuración del tenant distingue parámetros generales de la organización y parámetros específicos de cada sucursal cuando Multisucursal está contratado y el parámetro admite ese ámbito.

- **RN-CFG-009** — Los parámetros definidos para una sucursal solo afectan a esa sucursal dentro del alcance permitido y no convierten sus existencias o permisos en información compartida con otras sucursales.

- **RN-CFG-010** — Los parámetros regionales del SaaS se determinan conforme a la ubicación del negocio establecido en México, sin habilitar mediante la configuración un mercado de contratación fuera del país.

- **RN-CFG-011** — Cada sucursal utiliza la zona horaria correspondiente a su ubicación y los eventos generales del tenant utilizan la zona de su sede principal, conservándose una referencia temporal común.

- **RN-CFG-012** — Al habilitar un módulo adicional se aplican las configuraciones iniciales predeterminadas por la plataforma para ese módulo, sin sustituir los ajustes que deban completar los administradores autorizados.

- **RN-CFG-013** — La ausencia de una configuración obligatoria impide únicamente las operaciones que dependen de ella y no bloquea por sí misma el resto de las funciones válidamente disponibles del tenant.

- **RN-CFG-014** — Cuando un módulo adicional deja de estar contratado, sus configuraciones se conservan como información inactiva y no pueden utilizarse para ejecutar operaciones ordinarias del módulo.

- **RN-CFG-015** — La recuperación de un módulo adicional no restaura los permisos de usuario eliminados por su descontratación, aunque sus configuraciones históricas sigan conservadas.

- **RN-CFG-016** — Durante una suspensión por impago no se permiten modificaciones de configuración operativa, mientras que la terminación de la suscripción elimina el acceso directo a dicha configuración hasta una recuperación autorizada del servicio.

- **RN-CFG-017** — La captura de información para la personalización inicial durante el registro previo al pago no concede acceso a la configuración operativa del tenant antes de confirmarse la contratación.

## Requisitos funcionales (RF)

- **RF-CFG-001** — El sistema permite al administrador principal y a los administradores completos visualizar y actualizar el nombre comercial, logotipo, domicilio y datos de contacto de su propio tenant.

- **RF-CFG-002** — El sistema muestra el giro y la identidad interna del tenant sin ofrecer acciones para modificarlos después de su activación.

- **RF-CFG-003** — El sistema restringe la entrada a la sección de configuración del tenant y la ejecución de sus cambios al administrador principal y a los administradores completos.

- **RF-CFG-004** — El sistema presenta únicamente los parámetros configurables que correspondan al giro, a las funciones generales y a los módulos adicionales efectivamente habilitados para el tenant.

- **RF-CFG-005** — El sistema permite establecer las políticas operativas que ya hayan sido definidas como configurables para el giro o módulo del tenant y conserva su aplicación exclusiva a las operaciones posteriores.

- **RF-CFG-006** — El sistema registra para cada cambio de configuración confirmado el tenant, el parámetro y ámbito afectados, el valor previo, el valor resultante, la persona responsable y la fecha y hora.

- **RF-CFG-007** — El sistema permite consultar y editar configuraciones generales del tenant y, cuando Multisucursal esté activo, configuraciones específicas de sucursales para los parámetros que admitan ese alcance.

- **RF-CFG-008** — El sistema conserva asociadas a su sucursal las configuraciones locales y evita aplicarlas a otra sucursal por el solo hecho de compartir el catálogo de productos.

- **RF-CFG-009** — El sistema determina los parámetros regionales aplicables al tenant a partir de su ubicación en México y establece la zona horaria de cada sucursal según su región.

- **RF-CFG-010** — El sistema presenta fechas y horas de eventos de sucursal conforme a su zona horaria y utiliza la zona de la sede principal para los eventos generales del tenant.

- **RF-CFG-011** — El sistema inicializa las opciones de configuración de un módulo adicional con los valores predeterminados definidos para ese módulo cuando se habilita su contratación.

- **RF-CFG-012** — El sistema detecta las configuraciones obligatorias faltantes y bloquea las acciones que las requieren sin impedir el uso de otras funcionalidades autorizadas.

- **RF-CFG-013** — El sistema preserva las configuraciones de módulos descontratados y las mantiene fuera del uso operativo hasta que el módulo vuelva a estar contratado.

- **RF-CFG-014** — El sistema impide que la conservación o recuperación de configuraciones de un módulo restituya automáticamente permisos granulares previamente eliminados.

- **RF-CFG-015** — El sistema permite visualizar la configuración operativa autorizada en estado de suspensión conforme a los permisos vigentes, pero bloquea sus modificaciones y retira el acceso directo después de la terminación de la suscripción.

- **RF-CFG-016** — El sistema recoge la información inicial de personalización del negocio durante el proceso de registro y contratación y reserva la administración operativa de esa configuración para después de confirmarse el pago.

## Requisitos no funcionales (RNF)

- **RNF-CFG-001** — La lectura y modificación de parámetros de configuración aplican aislamiento entre tenants y verifican el rol del usuario en cada solicitud.

- **RNF-CFG-002** — Los cambios confirmados de configuración conservan una auditoría íntegra que no puede modificarse ni eliminarse mediante operaciones ordinarias de los usuarios del tenant.

- **RNF-CFG-003** — La aplicación de políticas modificadas preserva la interpretación histórica de operaciones anteriores y evita que las operaciones existentes cambien de reglas de manera retroactiva.

- **RNF-CFG-004** — Los cambios de configuración que afecten varios registros relacionados se confirman de manera atómica o se revierten si ocurre un fallo.

- **RNF-CFG-005** — La edición simultánea de un mismo parámetro detecta cambios concurrentes y evita sobrescribir silenciosamente la modificación confirmada por otro administrador.

- **RNF-CFG-006** — El almacenamiento y la presentación de marcas temporales de configuración conservan una referencia temporal consistente aun cuando las sucursales tengan zonas horarias diferentes.

## Reglas comerciales (RC)

- **RC-CFG-001** — El módulo general de Configuración del tenant está incluido en los cinco giros y en los tres niveles de plan sin contratación ni cobro independientes.

- **RC-CFG-002** — Las opciones de configuración propias de un módulo adicional solo quedan operativamente disponibles mientras ese módulo esté contratado, sin que su conservación histórica equivalga a una contratación activa.

## Pendientes de definición (PT)

- **PT-CFG-001** — Está pendiente especificar el catálogo completo de parámetros configurables por giro, módulo y nivel de ámbito, distinguiendo las políticas ya confirmadas de los valores que no se han definido.

- **PT-CFG-002** — Está pendiente determinar los campos obligatorios, validaciones y límites para nombre comercial, logotipo, domicilio y datos de contacto del tenant.

- **PT-CFG-003** — Está pendiente definir cómo se heredan, priorizan o resuelven los valores generales y los específicos de sucursal cuando ambos existen para un mismo parámetro.

- **PT-CFG-004** — Está pendiente concretar los valores predeterminados de cada módulo adicional y qué configuraciones indispensables debe completar el administrador antes de iniciar determinadas operaciones.

- **PT-CFG-005** — Está pendiente precisar el tratamiento de las operaciones iniciadas pero no confirmadas cuando cambia una política configurable y el instante exacto a partir del cual se considera vigente ese cambio.

- **PT-CFG-006** — Está pendiente determinar qué cambios de domicilio o región requieren recalcular la zona horaria de una sucursal y cómo se presentan los eventos históricos anteriores a esa modificación.

- **PT-CFG-007** — Está pendiente definir los formatos, dimensiones y tamaños admitidos para el logotipo y otros posibles archivos asociados a la identidad del tenant.

- **PT-CFG-008** — Está pendiente especificar qué administradores pueden consultar el historial de auditoría de configuración y qué filtros y periodos estarán disponibles, sin modificar la exclusividad del administrador principal sobre la auditoría de roles y permisos.

- **PT-CFG-009** — Está pendiente definir cómo se validan y reutilizan las configuraciones conservadas al recontratar un módulo adicional si sus opciones o reglas predeterminadas han cambiado desde la última contratación.

- **PT-CFG-010** — Está pendiente precisar qué configuraciones y documentos asociados se incluyen en la exportación controlada posterior a la terminación y cómo se aplican a estos datos la conservación y eliminación ya aprobadas.

- **PT-CFG-011** — Está pendiente delimitar qué datos y opciones concretas integran la personalización inicial anterior al pago y cuáles requieren completarse después de activar el tenant.
