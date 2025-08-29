# Examen-II
ll Examen Administracion de Bases de Datos SQL Server – Consultas Operativas y Analíticas
Descripción

Este examen contiene consultas SQL y procedimientos relacionados con la gestión de envíos y logística de la empresa Delta Carrier S.A., una startup de mensajería y última milla.
Se trabajó con las siguientes áreas principales:

Clientes (B2B, B2C y MiPyME)

Órdenes de envío y detalle de órdenes

Paquetes

Conductores y vehículos

Rutas y hubs (almacenes)

Eventos de tracking

Tarifas de envío

El objetivo principal es realizar análisis operativos, reportes y validaciones mediante consultas SQL avanzadas.

Contenido del Proyecto
C1. Consultas Operativas

Top 10 clientes por monto total enviado en los últimos 45 días

Uso de JOIN, GROUP BY y ORDER BY

Permite identificar clientes más activos y con mayor gasto.

Porcentaje de entregas a tiempo por hub y por semana

Agregación de datos por almacén y semana

Evalúa cumplimiento de tiempos de entrega.

Paquetes con retraso mayor a 24 horas

Cálculo de diferencias de tiempo (DATEDIFF) entre eventos 'En reparto' y 'Entregado'

Detecta posibles incidencias en la entrega.

Órdenes sin evento 'pick‑up' pero con 'En tránsito'

Uso de NOT EXISTS

Identifica inconsistencias en el flujo de tracking de paquetes.

C2. Funciones de Ventana (Window Functions)

RANK / ROW_NUMBER para clientes por gasto mensual

Clasifica clientes según el gasto total mensual.

LAG / LEAD para medir tiempo entre eventos consecutivos de un paquete

Permite calcular tiempo de tránsito entre eventos como 'Pick-up', 'En reparto', 'Entregado'.

Percentiles para tiempos de entrega por zona

Uso de PERCENTILE_CONT para analizar distribución y mediana de tiempos de entrega por hub.

C3. Operaciones de Conjuntos

Clientes que usaron promociones en enero y febrero

Uso de INTERSECT para identificar clientes recurrentes con promoción.

Órdenes de clientes corporativos que no usaron promoción

Uso de EXCEPT para filtrar clientes B2B sin descuentos aplicados.

C4. Consultas Parametrizadas

Reporte de carga estimada por hub para las próximas 48 horas

Permite parametrizar la zona (hub) y ventana de fechas.

Facilita la planificación logística y asignación de recursos.

C6. Planes de Ejecución

Se incluyeron planes de ejecución (Actual Execution Plan) para 2 consultas antes y después de crear índices.

Se evidenció costo, tiempo y operadores involucrados.

Este análisis permite validar mejoras en performance al optimizar consultas críticas.

Estructura de Tablas

almacenes: Información de hubs (nombre, dirección, capacidad, encargado)

clientes: Datos de clientes (tipo, contacto, dirección, cédula)

ordenes: Órdenes de envío, fecha y estado

detalle_orden: Items de cada orden, cantidad, total y descuento

paquetes: Paquetes asociados a órdenes y almacenes, estado y tiempo estimado

conductores: Datos de repartidores y tipo de licencia

vehiculos: Vehículos asignados a conductores

rutas: Rutas con origen, destino y distancia

eventos: Tracking de paquetes ('Pick-up', 'En tránsito', 'En reparto', 'Entregado', etc.)

tarifas: Información de tarifas según peso, dimensiones y distancia

Notas y Recomendaciones

Se recomienda mantener datos consistentes de fechas y descuentos para que las consultas funcionen correctamente.

Los cálculos de tiempo y porcentaje consideran la columna tiempo_entrega como número entero de días.

Para análisis avanzados, se aplicaron índices en columnas clave (id_cliente, id_orden, id_paquete) mejorando el rendimiento de consultas con JOIN y WHERE.

Capturas y Scripts

Todos los scripts SQL se encuentran en la carpeta scripts/

Capturas de resultados y planes de ejecución están en la carpeta docs/

