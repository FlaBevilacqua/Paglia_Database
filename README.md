# Pagila

**Pagila** es una base de datos de ejemplo para **PostgreSQL** que simula una tienda de alquiler de DVDs 📀. Sirve como material didáctico para tutoriales, artículos y demostraciones, ya que está específicamente diseñada para mostrar las características de PostgreSQL. 

---

## Artículos

Los siguientes artículos utilizan **Pagila** para mostrar diversas funcionalidades de PostgreSQL:

* **Sample Applications - Pagila (PostgreSQL)**
    * [https://codeontime.com/learn/sample-applications/pagila-postgresql](https://codeontime.com/learn/sample-applications/pagila-postgresql)
* **Showcasing REST in PostgreSQL - The PreQuel**
    * [http://www.postgresonline.com/journal/archives/32-Showcasing-REST-in-PostgreSQL-The-PreQuel.html](http://www.postgresonline.com/journal/archives/32-Showcasing-REST-in-PostgreSQL-The-PreQuel.html)
* **DataEdo**     
    * https://dataedo.com/samples/html/Pagila/doc/Pagila_10/home.html

---

## Información del 'Port'

**Pagila** es una adaptación (`port`) de la base de datos de ejemplo **Sakila**, creada originalmente para **MySQL**. Al igual que otras bases de datos de ejemplo, proporciona un esquema y datos de una hipotética "tienda de alquiler de DVDs" para usar en libros, tutoriales y artículos.

Para quienes estén interesados en los detalles técnicos de la adaptación, se migraron todas las tablas, datos, vistas y funciones, lo que implicó algunos cambios en el esquema:

* Se cambiaron los campos `char(1)` de `true/false` a campos **booleanos** reales.
* Se configuraron **disparadores** (`triggers`) para actualizar automáticamente las columnas `last_update`.
* Se agregaron **claves foráneas** (`foreign keys`).
* Se eliminó `DEFAULT 0` en las claves foráneas, ya que es innecesario con claves foráneas reales.
* Se utilizó la funcionalidad de **búsqueda de texto completo** (`fulltext searching`) integrada en PostgreSQL, lo que eliminó la necesidad de la tabla `film_text`.
* La función `rewards_report` se adaptó a un procedimiento almacenado que devuelve múltiples referencias de cursor.

El esquema y los datos de la base de datos **Sakila** original están disponibles bajo la **licencia BSD**.

---

## Licencia

* Partes con copyright (c) 2006-2025 Robert Treat
* Partes con copyright (c) 2006 MySQL AB

**Pagila** está disponible bajo la **Licencia de PostgreSQL**. Ten en cuenta que las versiones de **Pagila** anteriores a la 0.10.1 (inclusive) también se publicaron bajo la misma licencia BSD que **Sakila**.

---

## Historial de Versiones

* **Versión 16.a**
    * Reemplazada la constante `create_date` por defecto en la tabla `customer` con el estándar SQL `current_date`.
    * Agregado un ejemplo de `tsrange` por defecto para `rental.rental_period`.
    * Agregada la vista `sales_by_store`.
    * Corregida la vista "film list" para incluir películas sin actores.
* **Versión 15.a**
    * Agregada la vista `sales_by_film_category` junto con `COMMENT ON view`.
    * Agregada la vista `sales_top5_by_film_category` que muestra la función de ventana `topN` por categoría.
    * Agregado el procedimiento de utilidad `make_payment_data_current()` que actualiza las fechas de pago a valores recientes.
* **Versión 14.a**
    * Convertida la vista `nicer_but_slower_film_list` a una vista materializada.
    * Reemplazadas las columnas `rental_date/rental_return` por una única columna `tsrange` llamada `rental_period`.
    * Creado un esquema no público de ejemplo, también conocido como "legacy".
    * Creada una vista en el esquema "legacy" que coincide con el esquema original de la tabla `rental`.
* **Versión 13.a**
    * Agregado un ejemplo complejo de **JSONB** a través de la vista `rental_report`.
    * Agregado un ejemplo de columna generada no `IDENTITY` en `film.revenue_projection`.
* **Versión 12.a**
    * Uso de `:=` para la asignación en la función `last_updated`.
    * Mejoras menores en la vista `nicer_but_slower_film_list`.
    * Agregadas las particiones `DEFAULT` y `MAXVALUE` para la tabla `payment`.
    * Reconstruidos los datos para la tabla `payment`.
* **Versión 11.a**
    * Nueva descarga del esquema y datos con una versión más reciente de `pg_dump`. Esto fuerza la calificación del esquema para todos los objetos de la base de datos.
    * Convertida la función `reward_report` a un procedimiento almacenado basado en `refcusor`.
    * Eliminados el manejador de fechas de pago obsoleto y los `triggers` de apoyo.
    * Agregadas columnas de cobertura al índice de la clave primaria de `actor`.
    * Reescrita la vista `staff_list` usando la sintaxis `JOIN...USING`.
* **Versión 10.a**
    * Reconstruida la tabla `payments` usando particionamiento nativo.
    * Agregada una función, una regla y `triggers` para manejar las actualizaciones de la tabla de pagos particionada.
    * Corregidos numerosos errores en el archivo de inserción de datos.
* **Versión 9.6.a**
    * Cambiada la versión para seguir las versiones principales de **Postgres**.
    * Actualizados los enlaces en la sección de artículos (donde estaban disponibles).
    * Revisado el texto del archivo **README**.
* **Versión 0.10.1**
    * Agregado el archivo `pagila-data-insert.sql` y la sección de artículos.
* **Versión 0.10**
    * Soporte para **fulltext** integrado. Agregado un ejemplo de `enum`.
* **Versión 0.9**
    * Agregado un ejemplo de particionamiento de tablas.
* **Versión 0.8**
    * Primera versión de **Pagila**.
