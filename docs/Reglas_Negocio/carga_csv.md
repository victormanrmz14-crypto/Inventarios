# Carga masiva mediante CSV — Catálogo de requisitos

**Versión:** 1.0  
**Estado:** Propuesta; pendiente de aprobación.

Las entradas contienen únicamente su identificador y una descripción autónoma; los PT no representan decisiones aprobadas.

## Reglas de negocio (RN)

- **RN-CSV-001** — La carga masiva por CSV se limita a crear productos, actualizar sus datos permitidos y registrar existencias iniciales mediante movimientos de entrada, sin importar ventas, préstamos, devoluciones, mantenimientos ni movimientos históricos como operaciones previamente realizadas.

- **RN-CSV-002** — Cada importación CSV corresponde a un único tenant y solo puede crear o modificar registros pertenecientes a ese tenant.

- **RN-CSV-003** — Los datos admitidos por una importación deben cumplir las reglas y los atributos exigibles para el giro del tenant, incluidos lotes, caducidades o identificación individual cuando correspondan.

- **RN-CSV-004** — La correspondencia entre las filas del CSV y el catálogo del tenant se determina mediante el código de producto único dentro de ese tenant.

- **RN-CSV-005** — Una importación puede configurarse para crear productos, actualizar productos existentes o realizar ambas acciones en una misma ejecución.

- **RN-CSV-006** — La actualización de un producto mediante CSV respeta las restricciones de identidad, significado operativo y modalidad de seguimiento aplicables a productos con movimientos previos.

- **RN-CSV-007** — La importación de existencias iniciales de un producto solo está permitida cuando ese producto no tiene movimientos de inventario registrados previamente.

- **RN-CSV-008** — Un mismo código de producto puede aparecer en varias filas de un CSV cuando las filas representan lotes o unidades físicas individuales diferentes y cumplen las reglas de identificación del giro.

- **RN-CSV-009** — La importación de existencias iniciales genera movimientos de entrada trazables y no incorpora cantidades directamente al stock sin su movimiento correspondiente.

- **RN-CSV-010** — El usuario puede ejecutar únicamente las filas identificadas como válidas en la previsualización o cancelar la importación, sin ejecutar las filas señaladas como inválidas.

- **RN-CSV-011** — Para importar datos, el usuario necesita tanto el permiso de importación como los permisos de las operaciones subyacentes que se realizarán mediante las filas seleccionadas.

- **RN-CSV-012** — Las filas válidas seleccionadas para una ejecución se aplican de manera íntegra o no se aplica ninguna de ellas si surge un fallo al confirmar la importación.

- **RN-CSV-013** — La carga CSV debe respetar las restricciones vigentes sobre productos desactivados, existencias no negativas, sucursales autorizadas y disponibilidad de funcionalidades del tenant.

- **RN-CSV-014** — Reenviar una misma ejecución confirmada de importación no puede volver a crear los mismos registros ni duplicar sus movimientos de entrada.

## Requisitos funcionales (RF)

- **RF-CSV-001** — El sistema ofrece a los usuarios autorizados una función de carga masiva de archivos CSV para crear productos, actualizar sus datos permitidos y registrar existencias iniciales, sin incluir importaciones de operaciones comerciales o historiales operativos.

- **RF-CSV-002** — El sistema proporciona plantillas CSV diferenciadas por giro, con los campos correspondientes a los tipos de producto y modalidades de seguimiento que se admitan en cada caso.

- **RF-CSV-003** — El sistema permite seleccionar, antes de validar el archivo, si la carga se utilizará para crear productos, actualizar productos existentes o ejecutar ambas acciones.

- **RF-CSV-004** — El sistema identifica los productos existentes mediante su código de catálogo dentro del tenant y determina para cada fila si corresponde a un alta o a una actualización compatible con el modo elegido.

- **RF-CSV-005** — El sistema analiza el archivo antes de ejecutarlo y presenta una previsualización que permite distinguir las filas válidas de las inválidas e identificar los errores detectados.

- **RF-CSV-006** — El sistema permite al usuario ejecutar el conjunto de filas válidas presentado en la previsualización o cancelar la carga sin efectuar modificaciones.

- **RF-CSV-007** — El sistema valida en cada fila los datos obligatorios del giro y del seguimiento del producto, incluidos los atributos de lote, caducidad o unidad individual que resulten aplicables.

- **RF-CSV-008** — El sistema procesa varias filas asociadas al mismo código de producto cuando corresponden a lotes o unidades físicas distintos y no crea por ello productos duplicados en el catálogo.

- **RF-CSV-009** — El sistema aplica las modificaciones de productos exclusivamente sobre los campos permitidos y rechaza los cambios que alteren indebidamente su identidad o su modalidad de seguimiento después del primer movimiento.

- **RF-CSV-010** — El sistema registra las existencias iniciales importadas mediante movimientos de entrada y rechaza esa operación cuando el producto ya dispone de movimientos anteriores.

- **RF-CSV-011** — El sistema comprueba que el usuario dispone del permiso para importar y de las autorizaciones específicas para crear o modificar productos y registrar entradas iniciales, según las operaciones solicitadas.

- **RF-CSV-012** — El sistema verifica que los productos y movimientos importados correspondan al tenant y, cuando exista Multisucursal, al ámbito de sucursal que el usuario puede operar.

- **RF-CSV-013** — El sistema aplica todas las filas válidas elegidas como una ejecución íntegra y comunica si la importación se confirmó o fue revertida sin cambios por un fallo de validación o de ejecución.

- **RF-CSV-014** — El sistema conserva un registro de cada importación con tenant, usuario responsable, fecha y hora, productos y movimientos afectados, modificaciones realizadas y resultado de la ejecución.

- **RF-CSV-015** — El sistema permite consultar el resultado de una importación por su identificador después de una interrupción de conexión, sin volver a aplicar los efectos de una ejecución ya confirmada.

## Requisitos no funcionales (RNF)

- **RNF-CSV-001** — Cada ejecución de importación confirma atómicamente todas las filas válidas seleccionadas y revierte el conjunto completo ante un error que impida confirmarlo.

- **RNF-CSV-002** — La carga masiva aplica aislamiento multitenant y restricciones de permisos y sucursales tanto durante la previsualización como al confirmar la ejecución.

- **RNF-CSV-003** — Las importaciones simultáneas o repetidas mantienen la unicidad de los códigos de producto y de los identificadores individuales, evitan duplicar movimientos iniciales y respetan las restricciones de inventario al confirmar.

- **RNF-CSV-004** — Los registros de importaciones y de sus movimientos confirmados conservan trazabilidad e integridad y no pueden modificarse o eliminarse por operaciones ordinarias del tenant.

- **RNF-CSV-005** — La confirmación de importaciones requiere comunicación con el servidor y permite comprobar de forma segura el resultado de una solicitud cuando la respuesta se interrumpe.

## Reglas comerciales (RC)

- **RC-CSV-001** — La carga masiva por CSV se incluye por defecto para todos los tenants de los cinco giros y en los tres niveles de plan, sin contratarse ni cobrarse como módulo independiente.

## Pendientes de definición (PT)

- **PT-CSV-001** — Está pendiente precisar los campos obligatorios, opcionales y actualizables de cada plantilla por giro y tipo de producto, en coordinación con la definición de campos e identificadores del inventario.

- **PT-CSV-002** — Está pendiente determinar las convenciones concretas de formato CSV, incluidos encabezados, codificación, separadores, representación de fechas y números, y límites de tamaño o cantidad de filas.

- **PT-CSV-003** — Está pendiente definir cómo se interpretan varias filas de existencias iniciales para el mismo producto dentro de una única ejecución cuando corresponden a lotes o unidades distintos, sin vulnerar la prohibición de importar existencias iniciales a productos con movimientos previos.

- **PT-CSV-004** — Está pendiente precisar cómo se resuelven los conflictos entre filas del mismo archivo que intentan actualizar un mismo atributo del producto con valores distintos o crean identificadores individuales repetidos.

- **PT-CSV-005** — Está pendiente definir los detalles de la selección de sucursal y ubicación interna de las existencias iniciales importadas, especialmente cuando el tenant utiliza Multisucursal y existen reglas de asignación física aún no cerradas.

- **PT-CSV-006** — Está pendiente determinar cómo se muestran y exportan, si corresponde, los errores de validación y los resultados de la carga sin convertir en obligatorias opciones de descarga todavía no aprobadas.

- **PT-CSV-007** — Está pendiente precisar el procedimiento de conservación y consulta de los archivos originales cargados, distinto de la conservación obligatoria de la auditoría y de los movimientos confirmados.

- **PT-CSV-008** — Está pendiente especificar el mecanismo técnico de procesamiento, validación transaccional, control de concurrencia e idempotencia de archivos CSV en Laravel y PostgreSQL.
