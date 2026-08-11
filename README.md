# Práctica: Outer JOINs en MiniStore

## Respuestas al Cuestionario

### 1. ¿Por qué usaste LEFT JOIN para la Consulta 1 y no INNER JOIN?
Usé `LEFT JOIN` con la tabla `productos` a la izquierda para asegurar que se muestren **todos** los productos del catálogo. Si hubiese usado `INNER JOIN`, los productos que no tienen ventas (IDs 108 y 109) habrían quedado ocultos en el resultado.

### 2. ¿Por qué usaste RIGHT JOIN para la Consulta 2? ¿Qué tabla está a la izquierda y cuál a la derecha?
Usé `RIGHT JOIN` para traer la totalidad de las ventas registradas. 
* **Tabla a la izquierda:** `productos`
* **Tabla a la derecha:** `ventas`
De esta forma, si hay una venta registrada sin un producto válido en el catálogo, igual aparecerá en el reporte.

### 3. ¿Qué representan los valores NULL en cada resultado?
* **En la Consulta 1:** Que `venta_id` sea `NULL` significa que el producto existe en el catálogo pero nunca nadie lo compró (por ejemplo, el *Hub USB-C* o el *Parlante Bluetooth*).
* **En la Consulta 2:** Que el `producto_id` de la tabla productos sea `NULL` significa que hay un error de carga de datos: se registró una venta (ID 10) con un producto que no existe (ID 999).

### 4. ¿Cuándo usarías FULL OUTER JOIN en un caso real de negocio?
Lo usaría para **auditorías integrales** cuando necesito comparar dos listas y detectar inconsistencias en ambos lados a la vez. Por ejemplo, al cruzar la lista de stock del depósito físico con la lista de productos publicados en una tienda online para ver qué falta en cada lado.
