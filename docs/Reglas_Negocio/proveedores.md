# Proveedores y entidades relacionadas — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

## Reglas de negocio (RN)

- **RN-PRO-001** — Los registros de proveedores y entidades relacionadas pertenecen exclusivamente al tenant que los administra y no son accesibles para otros tenants.

- **RN-PRO-002** — En abarrotes, toda operación de compra de mercancía registrada en el sistema debe identificar al proveedor correspondiente.

- **RN-PRO-003** — En farmacia, los laboratorios pueden identificarse opcionalmente como una categoría de proveedor.

- **RN-PRO-004** — En biblioteca, la asociación de una editorial a un título bibliográfico es opcional.

- **RN-PRO-005** — En farmacia, la devolución de productos al proveedor requiere una autorización específica distinta de los permisos generales de inventario.

- **RN-PRO-006** — En farmacia, una devolución autorizada al proveedor puede tramitarse aunque el producto correspondiente se encuentre desactivado.

- **RN-PRO-007** — En productos electrónicos, una intervención de mantenimiento externo requiere que el proveedor responsable esté identificado antes de iniciarse.

- **RN-PRO-008** — En productos electrónicos, una garantía vigente cuya cobertura ha sido confirmada por el proveedor se atiende mediante dicho proveedor y no mediante mantenimiento propio.

- **RN-PRO-009** — El seguimiento interno de la atención de garantías ante proveedores electrónicos forma parte del módulo adicional de Mantenimiento y no de la gestión básica de proveedores.

## Requisitos funcionales (RF)

- **RF-PRO-001** — El sistema permite a los usuarios autorizados registrar y consultar proveedores asociados exclusivamente a su tenant para utilizarlos en las funcionalidades de los giros correspondientes.

- **RF-PRO-002** — El sistema permite vincular un proveedor identificado a las compras de mercancía de abarrotes y rechaza la confirmación de una compra sin dicha vinculación.

- **RF-PRO-003** — El sistema permite identificar opcionalmente como laboratorios a los proveedores registrados por un tenant de farmacia.

- **RF-PRO-004** — El sistema permite registrar editoriales y asociarlas opcionalmente a títulos bibliográficos dentro de las funcionalidades incluidas del giro de biblioteca.

- **RF-PRO-005** — El sistema permite registrar devoluciones de productos farmacéuticos a proveedores y comprueba que el usuario dispone del permiso específico requerido para esa operación.

- **RF-PRO-006** — El sistema permite tramitar devoluciones farmacéuticas autorizadas a proveedores sobre productos desactivados sin habilitar por ello operaciones ordinarias ni su venta.

- **RF-PRO-007** — El sistema permite identificar al proveedor responsable de un servicio de mantenimiento electrónico externo y bloquea el inicio de la intervención cuando falta dicha identificación.

- **RF-PRO-008** — Cuando el módulo Mantenimiento está contratado, el sistema registra la confirmación de cobertura de una garantía electrónica por parte del proveedor y vincula la atención cubierta con ese proveedor sin permitir sustituirla por mantenimiento propio.

- **RF-PRO-009** — El sistema habilita el seguimiento de la atención de garantías electrónicas ante proveedores dentro de la plataforma únicamente cuando el tenant tiene contratado el módulo adicional de Mantenimiento.

## Requisitos no funcionales (RNF)

- **RNF-PRO-001** — El sistema aplica el aislamiento multitenant a los registros de proveedores, laboratorios y editoriales y a sus relaciones con compras, devoluciones, garantías y mantenimiento.

- **RNF-PRO-002** — El sistema conserva la integridad de las referencias entre proveedores y operaciones relacionadas para evitar vínculos con registros de otro tenant.

- **RNF-PRO-003** — El sistema registra de forma trazable las modificaciones relevantes de proveedores y sus vínculos operativos, incluyendo el responsable, la fecha y hora, el tenant y la operación afectada.

## Reglas comerciales (RC)

- **RC-PRO-001** — La funcionalidad general de proveedores está incluida en los cinco giros y los tres niveles de plan, con laboratorios y editoriales como funcionalidades asociadas de farmacia y biblioteca, respectivamente, sin contratación independiente.

## Pendientes de definición (PT)

- **PT-PRO-001** — Está pendiente definir los campos obligatorios y opcionales del registro de proveedor y los datos adicionales necesarios para laboratorios y editoriales.

- **PT-PRO-002** — Está pendiente definir si cada proveedor tendrá un código único dentro del tenant y cómo se detectarán o gestionarán registros duplicados.

- **PT-PRO-003** — Está pendiente definir si los proveedores pueden editarse, desactivarse, reactivarse o eliminarse y cómo se conservarán las referencias históricas cuando tengan operaciones asociadas.

- **PT-PRO-004** — Está pendiente precisar qué permisos granulares se aplicarán al alta, consulta, modificación y administración de proveedores, laboratorios y editoriales.

- **PT-PRO-005** — Está pendiente determinar el alcance de los procesos de compras y abastecimiento de cada giro, sin asumir que todos dispondrán del mismo flujo de compras por la sola existencia del catálogo de proveedores.

- **PT-PRO-006** — Está pendiente detallar el procedimiento de devolución a proveedores farmacéuticos, incluidos motivos, datos obligatorios, estados y efectos de cada etapa sobre el inventario.

- **PT-PRO-007** — Está pendiente definir el tratamiento funcional de editoriales que identifican una publicación pero no participan como proveedor comercial de ejemplares.

- **PT-PRO-008** — Está pendiente precisar los datos mínimos de identificación del proveedor de servicios externos y del responsable de una garantía electrónica cuando no se utiliza el módulo Mantenimiento.

- **PT-PRO-009** — Está pendiente definir las reglas para utilizar un proveedor desactivado o con datos incompletos en operaciones nuevas, sin impedir la consulta de los vínculos históricos ya registrados.
