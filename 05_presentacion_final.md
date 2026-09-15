# Entregable Día 15 de Septiembre — Guión Estructurado para la Presentación Final (Reunión con Cliente)

## Contexto de la Presentación
* **Fecha**: 15 de Septiembre.
* **Escenario**: Reunión ejecutiva en la sede de **Supermercados FreshMarket S.A.**.
* **Ponentes**: Equipo de Consultoría y Ciencia de Datos de **ResQData AI**.
* **Audiencia**: Director General de Operaciones, Director de Compras de Frescos y Responsable de Sostenibilidad/ESG de FreshMarket.
* **Objetivo**: Presentar el diagnóstico de mermas realizado sobre sus datos operativos, demostrar el prototipo en vivo y cerrar el acuerdo de implantación de ResQData AI en las 45 tiendas de la cadena.

---

## Estructura Diapositiva por Diapositiva (10 Bloques Clave)

### Bloque 1: Presentación de la Startup (1 min)
* **Diapositiva 1**: Portada — *ResQData AI: Transformando el desperdicio alimentario en margen operativo*.
* **Guión**: "Buenos días a la directiva de FreshMarket. Somos ResQData AI, una startup especializada en Ciencia de Datos aplicada al FoodTech. Nuestra misión es simple: eliminar el desperdicio alimentario en la distribución minorista mediante modelos predictivos y precios dinámicos inteligentes."

---

### Bloque 2: El Cliente (1 min)
* **Diapositiva 2**: *Supermercados FreshMarket S.A.: Compromiso con la Calidad y la Proximidad*.
* **Guión**: "FreshMarket es un referente con 45 tiendas y 650 empleados, destacando por la frescura de sus productos. Sin embargo, mantener la máxima frescura en lineal conlleva un reto financiero y logístico gigante en productos de corta vida útil."

---

### Bloque 3: El Problema (1.5 min)
* **Diapositiva 3**: *El Agujero Negro en la Sección de Frescos*.
* **Guión**: "Durante los últimos 90 días hemos analizado 3.610 lotes recibidos en sus tiendas. Hemos detectado que FreshMarket está sufriendo una merma equivalente a más de 1,8 millones de euros anuales en producto tirado a la basura. Los encargados de tienda detectan la caducidad tarde y aplican descuentos reactivos el mismo día del vencimiento, cuando el cliente ya no compra."

---

### Bloque 4: Impacto Económico y Social (1.5 min)
* **Diapositiva 4**: *Lo que FreshMarket Perdía Cada Día*.
* **Guión**: "No solo es una pérdida directa de margen bruto del 4,2% en frescos. Es también un coste oculto en gestión de residuos, horas de trabajo perdidas etiquetando a mano y más de 50 toneladas de emisiones de CO2 no neutralizadas que penalizan sus métricas ESG."

---

### Bloque 5: Los Datos y Modelo de Datos (2 min)
* **Diapositiva 5**: *Conectando el Ecosistema de Datos de FreshMarket*.
* **Guión**: "Analizamos sus datos reales de TPV, inventarios por lote, caducidades y mermas. Diseñamos un modelo relacional de 6 tablas conectando productos, tiendas, lotes, ventas, mermas y donaciones. Toda la actividad de sus tiendas ya produce esta información, pero hasta hoy estaba infrautilizada."

---

### Bloque 6: Investigación y Descubrimiento Sorpresa (2 min)
* **Diapositiva 6**: *La Revelación del Análisis Exploratorio (EDA)*.
* **Guión**: "Aquí llegó la gran sorpresa. La dirección de FreshMarket asumía que el desperdicio provenía de Frutas y Verduras. Nuestros datos demostraron que Frutas y Verduras solo representan el 4% del coste. ¡El 85% de sus pérdidas están concentradas en Platos Preparados (destacando el Sushi) y Pescadería! Y más impactante aún: las tiendas de Centro Madrid y Sarrià apenas tenían mermas porque aplicaban rebajas proactivas a 48 horas, mientras que Vallecas, Eixample y Ruzafa tiraban el 90% de sus lotes por etiquetar solo el mismo día de caducidad."

---

### Bloque 7: La Solución Desarrollada (2 min)
* **Diapositiva 7**: *ResQData Engine: De los Datos a la Acción*.
* **Guión**: "Para solucionar esto no entregamos un simple informe PDF. Desarrollamos el ResQData Engine: un algoritmo de Random Forest que predice con 72h de antelación el riesgo de caducidad de cada lote y envía automáticamente al TPV la curva de descuento óptima: -15% a las 72h, -30% a las 48h y donación automatizada a ONGs a las 24h."

---

### Bloque 8: Demo en Vivo (2 min)
* **Diapositiva 8**: *Demostración del Panel de Control FreshMarket*.
* **Guión**: *(Mapeado a `dashboard.html`)* "Les mostramos la pantalla que vería su director de operaciones hoy mismo: de un vistazo detectamos 14 lotes críticos, como 28 unidades de Sushi en la tienda de Vallecas caducando mañana. Con un solo clic en 'Aplicar Rebaja', la caja registradora de Vallecas actualiza el precio a -30%, acelerando la venta antes del cierre."

---

### Bloque 9: Resultados e Implementación (1.5 min)
* **Diapositiva 9**: *Impacto Cuantitativo Proyectado*.
* **Guión**: "Con la implantación de ResQData AI, reduciremos su merma en un 72%, salvando más de 800 kg de comida al mes por tienda y generando un ahorro neto anual de 225.000 € para la cadena."

---

### Bloque 10: Propuesta de Valor y Cierre (1.5 min)
* **Diapositiva 10**: *¿Por qué Contratar a ResQData AI Hoy?*.
* **Guión**: "Por un coste SaaS de 150 €/mes por tienda, el retorno de inversión se alcanza en tan solo 11 días. Además, les proporcionamos el certificado de impacto ambiental e incentivos fiscales por donaciones. Estamos listos para desplegar en sus 45 tiendas a partir del próximo lunes. ¿Empezamos?"
