# Área 20 — Control de prescripciones médicas (Farmacia)

**Versión:** 1.0  
**Estado:** Pendiente de aprobación.  
**Formato:** identificador y descripción autónoma por entrada; los pendientes no constituyen decisiones aprobadas.

## Reglas de negocio (RN)

- **RN-PRE-001** — Los medicamentos del giro farmacia pueden identificarse mediante un indicador que distingue los que requieren prescripción médica de los que no la requieren.

- **RN-PRE-002** — La venta de un medicamento marcado como sujeto a prescripción médica exige que el cajero confirme el aviso correspondiente antes de continuar la operación.

- **RN-PRE-003** — La confirmación del aviso de prescripción no requiere registrar el contenido de la receta médica ni constituye una validación clínica automatizada de dicho documento.

- **RN-PRE-004** — La confirmación del aviso de prescripción no exime de cumplir las restricciones vigentes de existencias, lote, caducidad y disponibilidad del medicamento.

## Requisitos funcionales (RF)

- **RF-PRE-001** — El sistema permite registrar y consultar el indicador de prescripción de cada medicamento de farmacia, y modificarlo únicamente cuando los permisos y las restricciones de edición del producto lo permitan.

- **RF-PRE-002** — El sistema muestra a los usuarios autorizados el indicador de prescripción asociado a cada medicamento de farmacia.

- **RF-PRE-003** — Al procesar una venta de farmacia que incluye un medicamento marcado como sujeto a prescripción, el sistema muestra al cajero un aviso identificando la exigencia correspondiente.

- **RF-PRE-004** — El sistema solicita una confirmación explícita del aviso al cajero antes de permitir que continúe la venta de un medicamento marcado como sujeto a prescripción médica.

- **RF-PRE-005** — El sistema ejecuta la confirmación del aviso sin capturar ni conservar el contenido de la receta médica.

## Requisitos no funcionales (RNF)

- **RNF-PRE-001** — El sistema protege el indicador de prescripción y las operaciones asociadas mediante el aislamiento de datos entre tenants y los permisos vigentes del usuario.

- **RNF-PRE-002** — El sistema aplica la comprobación del indicador y la confirmación correspondiente en el flujo de venta autorizado, sin permitir que el usuario continúe una operación sujeta a prescripción sin la confirmación requerida.

- **RNF-PRE-003** — El sistema conserva trazabilidad de las modificaciones relevantes del indicador de prescripción, sin incorporar el contenido clínico de recetas médicas.

## Reglas comerciales (RC)

- **RC-PRE-001** — El control mediante indicador de prescripción y confirmación del aviso forma parte de las funcionalidades base del giro farmacia en los planes Básico, Intermedio y Superior, sin contratar un módulo adicional de prescripciones.

## Pendientes de definición (PT)

- **PT-PRE-001** — Está pendiente definir los permisos granulares específicos para crear o modificar el indicador de prescripción, sin presuponer un permiso independiente de la edición autorizada del medicamento.

- **PT-PRE-002** — Está pendiente decidir si se conserva una evidencia específica de cada confirmación del cajero y, en su caso, sus campos, sin almacenar el contenido de la receta.

- **PT-PRE-003** — Está pendiente establecer el texto y la presentación exactos del aviso de prescripción mostrado durante la venta.

- **PT-PRE-004** — Está pendiente definir si el indicador de prescripción podrá establecerse o actualizarse mediante la carga masiva por CSV y las validaciones que corresponderían.

- **PT-PRE-005** — Está pendiente definir el tratamiento de ventas pendientes cuando cambia el indicador de prescripción de un medicamento, respetando que los cambios de políticas no modifican retroactivamente operaciones ya confirmadas.

- **PT-PRE-006** — Está pendiente determinar el alcance exacto de la clasificación de productos del giro farmacia para distinguir medicamentos de otros artículos y aplicar el control de prescripción solo donde corresponda.
