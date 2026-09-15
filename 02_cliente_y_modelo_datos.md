# Entregable Día 11 de Septiembre — Cliente y Modelo de Datos

## 1. Ficha Completa del Cliente
* **Nombre de la Empresa Cliente**: Supermercados FreshMarket S.A.
* **Sector**: Gran Distribución Minorista / Supermercados de Proximidad.
* **Actividad**: Comercialización de productos de alimentación, con especial foco en productos frescos de alta calidad (carnicería, pescadería, platos preparados, lácteos, frutas/verduras y panadería).
* **Tamaño**: Cadena mediana regional.
* **Número de Empleados**: 650 empleados.
* **Número de Tiendas / Clientes**: 45 tiendas físicas (superficie media de 900 m2) y más de 120.000 clientes activos mensuales.
* **Productos / Servicios**: Más de 8.000 referencias SKU; sección destacada de Platos Preparados para llevar y Pescadería fresca del día.
* **Modelo de Negocio**: B2C venta minorista en tienda física y canal online de proximidad. Margen bruto promedio del 28% en secos y 38% en frescos.
* **Procesos Principales**:
  1. Aprovisionamiento diario y recepción de lotes en tienda.
  2. Reposición en lineal y etiquetado.
  3. Control manual diario de fechas de caducidad por el personal de tienda.
  4. Venta en TPV.
  5. Retirada manual de producto vencido a contenedor de merma.
* **Situación Actual**: Crecimiento sostenido en ventas, pero con un deterioro preocupante del beneficio neto debido al aumento de costes operativos y mermas en secciones de corta vida útil.
* **Problemas Identificados**:
  - Pérdida anual estimada de 1,8 M€ en alimentos descartados.
  - Gestión de caducidades 100% manual e intuitiva según el criterio del encargado de cada tienda.
  - Aplicación de descuentos tardía (solo el mismo día de caducidad), lo que resulta ineficaz para dar salida al stock.
  - Inexistencia de un registro digital estructurado de motivos de merma.
* **Necesidades**:
  - Un sistema inteligente que anticipe los productos que se van a caducar con 48h–72h de margen.
  - Automatización del cálculo de descuentos óptimos sin destruir la percepción de marca.
  - Trazabilidad digital del desperdicio y simplificación de las donaciones a ONGs.

---

## 2. Identificación de Datos Disponibles
La empresa genera de forma natural en sus operaciones los siguientes datos:
1. **Tiendas**: `tienda_id`, nombre, ciudad, superficie_m2, tipo_ubicacion.
2. **Productos (Catálogo SKU)**: `producto_id`, nombre, categoría, días_vida_útil, precio_venta_base, coste_unitario, temperatura_conservación.
3. **Lotes de Entradas**: `lote_id`, `producto_id`, `tienda_id`, unidades_recibidas, unidades_disponibles, fecha_recepción, fecha_caducidad.
4. **Ventas (Transacciones TPV)**: `venta_id`, `lote_id`, `tienda_id`, unidades_vendidas, precio_unidades_real, descuento_aplicado_pct, fecha_hora_venta.
5. **Mermas (Retiradas a vertedero)**: `merma_id`, `lote_id`, `tienda_id`, unidades_mermadas, coste_total_merma, motivo_merma, fecha_merma.
6. **Donaciones (Impacto Social)**: `donacion_id`, `lote_id`, `tienda_id`, unidades_donadas, ong_beneficiaria, valor_donacion, fecha_donacion.

---

## 3. Diseño de la Base de Datos Relacional (SQLite / PostgreSQL)

### Esquema DDL (Data Definition Language)

```sql
CREATE TABLE tiendas (
    tienda_id INTEGER PRIMARY KEY AUTOINCREMENT,
    nombre TEXT NOT NULL,
    ciudad TEXT NOT NULL,
    superficie_m2 INTEGER NOT NULL,
    tipo_ubicacion TEXT NOT NULL
);

CREATE TABLE productos (
    producto_id INTEGER PRIMARY KEY AUTOINCREMENT,
    nombre TEXT NOT NULL,
    categoria TEXT NOT NULL,
    dias_vida_util INTEGER NOT NULL,
    precio_venta_base REAL NOT NULL,
    coste_unitario REAL NOT NULL,
    temperatura_conservacion TEXT NOT NULL
);

CREATE TABLE lotes (
    lote_id INTEGER PRIMARY KEY AUTOINCREMENT,
    producto_id INTEGER NOT NULL,
    tienda_id INTEGER NOT NULL,
    unidades_recibidas INTEGER NOT NULL,
    unidades_disponibles INTEGER NOT NULL,
    fecha_recepcion DATE NOT NULL,
    fecha_caducidad DATE NOT NULL,
    FOREIGN KEY (producto_id) REFERENCES productos(producto_id),
    FOREIGN KEY (tienda_id) REFERENCES tiendas(tienda_id)
);

CREATE TABLE ventas (
    venta_id INTEGER PRIMARY KEY AUTOINCREMENT,
    lote_id INTEGER NOT NULL,
    tienda_id INTEGER NOT NULL,
    unidades_vendidas INTEGER NOT NULL,
    precio_unidades_real REAL NOT NULL,
    descuento_aplicado_pct REAL NOT NULL,
    fecha_hora_venta DATETIME NOT NULL,
    FOREIGN KEY (lote_id) REFERENCES lotes(lote_id),
    FOREIGN KEY (tienda_id) REFERENCES tiendas(tienda_id)
);

CREATE TABLE mermas (
    merma_id INTEGER PRIMARY KEY AUTOINCREMENT,
    lote_id INTEGER NOT NULL,
    tienda_id INTEGER NOT NULL,
    unidades_mermadas INTEGER NOT NULL,
    coste_total_merma REAL NOT NULL,
    motivo_merma TEXT NOT NULL,
    fecha_merma DATE NOT NULL,
    FOREIGN KEY (lote_id) REFERENCES lotes(lote_id),
    FOREIGN KEY (tienda_id) REFERENCES tiendas(tienda_id)
);

CREATE TABLE donaciones (
    donacion_id INTEGER PRIMARY KEY AUTOINCREMENT,
    lote_id INTEGER NOT NULL,
    tienda_id INTEGER NOT NULL,
    unidades_donadas INTEGER NOT NULL,
    ong_beneficiaria TEXT NOT NULL,
    valor_donacion REAL NOT NULL,
    fecha_donacion DATE NOT NULL,
    FOREIGN KEY (lote_id) REFERENCES lotes(lote_id),
    FOREIGN KEY (tienda_id) REFERENCES tiendas(tienda_id)
);
```

---

## 4. Diagrama Entidad-Relación (ERD)

```
 [ TIENDAS ] (1) <------- (N) [ LOTES ] (N) -------> (1) [ PRODUCTOS ]
     |                          |                          |
     | (1)                      | (1)                      |
     |                          |                          |
     v (N)                      v (N)                      |
 [ VENTAS ]                [ MERMAS ]                      |
     ^                          ^                          |
     |                          |                          |
     +--------------------------+--------------------------+
                                |
                                v (N)
                          [ DONACIONES ]
```
