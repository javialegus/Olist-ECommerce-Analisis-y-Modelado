# Análisis y Modelado Relacional: Caso E-Commerce Olist (Brasil)

## Objetivo Didáctico y de Negocio
Este proyecto centraliza y analiza más de 100,000 registros de transacciones logísticas para identificar áreas de oportunidad en los tiempos de entrega. El enfoque principal del desarrollo fue establecer una arquitectura de datos limpia y escalable que permita explicar conceptos complejos de bases de datos de forma visual e intuitiva.

## Arquitectura de Datos: Esquema en Estrella
Para garantizar la integridad referencial y evitar la redundancia de datos, se implementó un modelo relacional en estrella:
* **Tablas de Hechos (Valles):** Movimientos dinámicos como `Order_Items`, `Payments` y `Reviews`.
* **Tablas Dimensionales (Montañas):** Catálogos estáticos como `Customers`, `Products` y `Sellers`.
* **Solución de Filtrado:** Se establecieron flujos de dirección única (1:N) conectando llaves primarias con llaves foráneas, logrando que los filtros interactivos funcionen sin bloqueos ni errores de circularidad.

## Tratamiento de Datos (ETL)
* Normalización de tipografías y códigos postales a texto estricto para asegurar la precisión en mapas geográficos.
* Integración de tablas de traducción para estandarizar categorías del portugués al inglés.
* Tratamiento de valores nulos (pedidos cancelados) protegiendo la salud de las columnas calculadas.

## Lógica de Cálculo (DAX)
Se desarrollaron métricas temporales precisas para evaluar el rendimiento logístico:
`Tiempo_De_Entrega = DATEDIFF(order_purchase_timestamp, order_delivered_customer_date, DAY)`
* *Adicionalmente, se extrajeron dimensiones temporales (Mes y Año) para el análisis de tendencias sin sobrecargar el modelo.*

## Conclusiones Clave
* **Volumen:** La plataforma procesó un total de 16.01 millones (BRL) en ingresos.
* **Logística:** El promedio de entrega al cliente final se estableció en 12.50 días.
* **Líderes de Mercado:** La categoría "Health & Beauty" demostró ser el principal motor financiero del ecosistema.
