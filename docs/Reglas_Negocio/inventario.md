# Inventario general — Catálogo de requisitos

**Versión:** 1.2 (formato simplificado; contenido de v1.1)  
**Estado:** Aprobada; pendientes de definición conservados.

Cada entrada contiene solo su identificador y descripción.

## Reglas de negocio (RN)

- **RN-INV-001** — Cada producto mantiene un código de catálogo único dentro de su tenant.

- **RN-INV-002** — El seguimiento del inventario se establece por cantidad o por unidad física individual según el tipo o la categoría del producto.

- **RN-INV-003** — La modalidad de seguimiento de un producto permanece invariable después de registrar su primer movimiento de inventario.

- **RN-INV-004** — Las existencias iniciales de un producto se incorporan mediante un movimiento de entrada registrado en su historial.

- **RN-INV-005** — Ninguna operación confirmada de inventario produce existencias negativas en el ámbito de stock que afecta.

- **RN-INV-006** — El sistema no inmoviliza existencias mediante reservas o apartados de inventario.

- **RN-INV-007** — Un movimiento de inventario confirmado conserva sus datos originales sin edición ni eliminación directa.

- **RN-INV-008** — Cada rectificación de un movimiento confirmado se representa mediante otro movimiento relacionado explícitamente con el original.

- **RN-INV-009** — Un producto con movimientos registrados admite cambios descriptivos pero no cambios que alteren su identidad o significado operativo.

- **RN-INV-010** — Un producto con movimientos históricos no puede eliminarse permanentemente de los registros operativos.

- **RN-INV-011** — Un producto puede desactivarse aunque conserve existencias físicas registradas.

- **RN-INV-012** — Un producto desactivado queda excluido de las operaciones ordinarias nuevas y solo admite ajustes autorizados y excepciones específicas del giro.

- **RN-INV-013** — La reactivación autorizada de un producto conserva su identificador y su historial previo.

- **RN-INV-014** — Cada unidad física con seguimiento individual posee un identificador único dentro de su tenant.

- **RN-INV-015** — Una existencia o unidad solo se considera disponible para una operación si satisface todas las restricciones vigentes aplicables.

- **RN-INV-016** — Toda operación que compromete existencias vuelve a validar las cantidades y restricciones aplicables en el momento de su confirmación.

## Requisitos funcionales (RF)

- **RF-INV-001** — El sistema permite registrar productos con códigos de catálogo únicos dentro del tenant y asignar a cada producto el seguimiento por cantidad o por unidad física individual según su tipo o categoría.

- **RF-INV-002** — El sistema permite registrar y consultar unidades físicas con seguimiento individual, asignando a cada una un identificador único dentro del tenant.

- **RF-INV-003** — El sistema registra las existencias iniciales de cada producto mediante movimientos de entrada trazables, tanto en altas manuales como en las importaciones autorizadas.

- **RF-INV-004** — El sistema permite modificar campos descriptivos de productos con historial e impide cambiar campos que alteren su identidad o significado operativo o su modalidad de seguimiento tras el primer movimiento.

- **RF-INV-005** — El sistema permite a usuarios con permiso especial registrar ajustes de inventario con justificación obligatoria e impide confirmar ajustes que produzcan existencias negativas.

- **RF-INV-006** — El sistema permite a usuarios con un permiso especial de corrección distinto del permiso de ajuste rectificar movimientos confirmados mediante nuevos movimientos vinculados, preservando los originales e impidiendo existencias negativas.

- **RF-INV-007** — El sistema permite desactivar productos aunque conserven existencias y reactivarlos mediante autorización, preservando su identidad e historial y bloqueando operaciones ordinarias nuevas mientras estén desactivados.

- **RF-INV-008** — El sistema evalúa y mantiene simultáneamente las causas aplicables de indisponibilidad de cada producto o unidad, y solo lo ofrece en operaciones para las que cumple todas las restricciones vigentes.

- **RF-INV-009** — El sistema registra para cada modificación relevante del inventario el usuario responsable, la fecha y hora, el tenant, la sucursal cuando aplique y las referencias de los registros afectados.

- **RF-INV-010** — El sistema permite consultar el resultado de una operación de inventario mediante su identificador después de una interrupción de conexión y evita repetir efectos ya confirmados.

- **RF-INV-011** — El sistema detecta que un registro de catálogo fue modificado por otro usuario durante su edición y solicita resolver el conflicto antes de sobrescribir información actualizada.

## Requisitos no funcionales (RNF)

- **RNF-INV-001** — Cada etapa confirmable de inventario aplica de forma atómica todas las modificaciones relacionadas, de modo que un fallo no deje entradas, movimientos o rectificaciones confirmados parcialmente salvo etapas independientes expresamente admitidas.

- **RNF-INV-002** — La ejecución concurrente de operaciones sobre las mismas existencias mantiene stock no negativo, respeta todas las restricciones de disponibilidad y vuelve a verificar cantidades al confirmar.

- **RNF-INV-003** — La repetición de una operación de inventario con el mismo identificador produce como máximo un efecto y permite recuperar de forma consistente su resultado original.

- **RNF-INV-004** — El sistema protege los movimientos confirmados y los registros de auditoría contra alteración o eliminación ordinaria, y conserva las correcciones mediante registros vinculados al original.

- **RNF-INV-005** — Las operaciones que modifican inventario requieren comunicación con el servidor y solo se confirman tras la validación vigente de cantidades y restricciones.

## Pendientes de definición (PT)

- **PT-INV-001** — Está pendiente de definición de negocio la clasificación de campos descriptivos modificables y campos que alteran la identidad o el significado operativo de productos con historial.

- **PT-INV-002** — Está pendiente de definición de negocio el mapeo de tipos o categorías de cada giro a seguimiento por cantidad o individual y sus atributos obligatorios.

- **PT-INV-003** — El diseño técnico documentará el mecanismo de transacciones, control de concurrencia, identificadores idempotentes y verificación de resultados de operaciones de inventario.

- **PT-INV-004** — Está pendiente de definición de negocio el tratamiento de la eliminación permanente de productos que todavía no tienen movimientos registrados.
