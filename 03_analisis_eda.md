# Entregable Día 13 de Septiembre — Análisis Exploratorio (EDA) y Descubrimiento

## 1. Resumen Ejecutivo del Análisis de Datos

Tras procesar una muestra representativa de 90 días de operaciones (3.610 lotes recibidos, 16.300 operaciones de venta y más de 1.200 registros de merma/donación en la base de datos `food_waste.db`), el equipo de **ResQData AI** extrajo patrones clave sobre el comportamiento del desperdicio en Supermercados FreshMarket.

---

## 2. Hallazgos Principales de la Exploración

### A. Concentración de la Merma por Tienda
| Tienda | Ciudad | Mermas Registradas | Unidades Mermadas | Coste Merma Acumulado (€) | Política de Descuentos Observada |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **FreshMarket Eixample** | Barcelona | 307 | 2.592 | **5.843,10 €** | Reactiva / Tardía (mismo día 10-20%) |
| **FreshMarket Vallecas** | Madrid | 301 | 2.587 | **5.310,85 €** | Reactiva / Tardía (mismo día 10-20%) |
| **FreshMarket Ruzafa** | Valencia | 305 | 2.506 | **5.042,65 €** | Reactiva / Tardía (mismo día 10-20%) |
| **FreshMarket Sarrià** | Barcelona | 124 | 387 | **662,90 €** | Proactiva (48h antes al 30-50%) |
| **FreshMarket Centro Madrid** | Madrid | 112 | 322 | **562,60 €** | Proactiva (48h antes al 30-50%) |

---

### B. Mermas por Categoría de Producto
| Categoría | Unidades Mermadas | Coste Merma (€) | % del Coste Total |
| :--- | :---: | :---: | :---: |
| **Platos Preparados** | 2.125 | **8.397,10 €** | **48,2%** |
| **Panadería y Pastelería** | 4.453 | **4.286,60 €** | **24,6%** |
| **Pescadería Fresca** | 809 | **2.771,90 €** | **15,9%** |
| **Bebidas Frescas** | 671 | **1.274,90 €** | **7,3%** |
| **Carnicería y Frutas/Verduras** | 336 | **691,60 €** | **4,0%** |

---

### C. Top SKU con Mayor Impacto Económico en Desperdicio
1. **Sushi Pack Variado 12 piezas** (Platos Preparados): 1.408 unidades tiradas → **7.321,60 € de coste**.
2. **Dorada Limpia Ración 300g** (Pescadería): 677 unidades tiradas → **2.098,70 € de coste**.
3. **Empanada de Atún Artesana** (Panadería): 1.566 unidades tiradas → **2.035,80 € de coste**.
4. **Zumo de Naranja Recién Exprimido 1L** (Bebidas): 671 unidades tiradas → **1.274,90 € de coste**.

---

## 3. El Descubrimiento Insospechado ("La Sorpresa de los Datos")

* **Lo que la directiva de FreshMarket Creía**:
  "Nuestras mayores pérdidas de desperdicio se deben al deterioro de Frutas y Verduras en los mostradores y al sobrestock general generado durante los fines de semana por falta de compradores."

* **Lo que los Datos Demostraron**:
  1. Frutas, Verduras y Carnicería solo representan el **4% del coste de merma**.
  2. El **85% de las pérdidas económicas** se concentran en **Platos Preparados y Pescadería Fresca** debido a su cortísima vida útil (3 a 5 días) combinada con una **pésima política de etiquetado de descuento**.
  3. Las tiendas de Sarrià y Centro Madrid recortan las mermas un **90%** respecto a Vallecas, Ruzafa y Eixample simplemente porque el encargado aplica de forma intuitiva un descuento del 30% a 48h de caducar, mientras que las otras tiendas esperan al mismo día de vencimiento, cuando el cliente ya rechaza el producto aunque tenga un 20% de rebaja.

---

## 4. Oportunidades Identificadas y Selección

### Oportunidades Detectadas:
1. **Oportunidad 1**: Optimización del pedido inicial de reabastecimiento en Platos Preparados según día de la semana.
2. **Oportunidad 2**: Automatización de la política de precios dinámicos según días de vida útil restantes por lote.
3. **Oportunidad 3**: Protocolo automatizado de donación a ONGs para lotes a < 24h de caducidad no vendidos.

### Oportunidad Seleccionada: **Motor de Precios Dinámicos e Identificación Predictiva de Riesgo por Lote (Oportunidad 2)**.

### Traducción a Ciencia de Datos:
* **Problema de Negocio**: "Perdemos más de 16.000 € al trimestre tirando platos preparados y pescadería fresca por no venderlos antes de caducar."
* **Problema de Ciencia de Datos**: "Construir un modelo de **Clasificación Predictiva y Scoring de Riesgo por Lote** que, combinando los días restantes para el vencimiento y la tasa de rotación histórica de la tienda, determine automáticamente la curva de descuento óptima (0% → 15% → 30% → 50% → Donación) para maximizar el margen recuperado antes de la caducidad."
