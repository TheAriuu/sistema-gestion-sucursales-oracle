# Sistema de Gestión de Sucursales - Dali

**Proyecto 1 - Bases de Datos 2**

Sistema full-stack para la gestión de una cadena de supermercados/tiendas ("Dali") con múltiples sucursales en Costa Rica. Incluye control de inventario, facturación, empleados, proveedores, clientes y reportes, con una base de datos Oracle robusta que implementa **triggers**, **packages PL/SQL** y un diseño relacional normalizado.

---

## Descripción del Proyecto

Este proyecto simula el sistema de información de una cadena comercial con presencia en las 7 provincias de Costa Rica. Permite:

- Gestión de sucursales geolocalizadas (Provincia → Cantón → Sucursal)
- Control de empleados y clientes
- Inventario de productos y relación con proveedores
- Facturación de ventas
- Reportes de ventas por sucursal y por empleado
- Auditoría de cambios de precios (bitácora)
- Autenticación de usuarios

El enfoque principal del proyecto fue el **diseño e implementación de la base de datos en Oracle**, incluyendo lógica de negocio a nivel de base de datos mediante **triggers y packages**.

---

## Tecnologías Utilizadas

| Capa              | Tecnología                          |
|-------------------|-------------------------------------|
| **Base de Datos** | Oracle Database (PL/SQL)            |
| **Backend**       | Node.js + Express + oracledb        |
| **Frontend**      | React (Create React App)            |
| **Otros**         | CORS, Oracle Wallet                 |

---

## Modelo de Base de Datos

### Tablas principales

| Tabla                  | Descripción                                      |
|------------------------|--------------------------------------------------|
| `Provincias`           | Catálogo de provincias de Costa Rica             |
| `Cantones`             | Cantones asociados a provincias                  |
| `Sucursal`             | Sucursales de la cadena (nombre de facturación)  |
| `Empleado`             | Empleados asignados a una sucursal               |
| `Cliente`              | Clientes del sistema                             |
| `Proveedor`            | Proveedores geolocalizados                       |
| `Producto`             | Catálogo de productos con stock y precio         |
| `Factura_venta`        | Cabecera de facturas de venta                    |
| `Fact_producto`        | Detalle de productos vendidos por factura        |
| `Proveedor_producto`   | Relación muchos a muchos proveedor ↔ producto    |
| `Usuarios`             | Usuarios del sistema (login)                     |
| `Bitacora`             | Auditoría de cambios de precio                   |


## Cómo ejecutar el proyecto
1. Base de datos (Oracle)
Crear un usuario/schema en Oracle.
Ejecutar el contenido del archivo tablas.
Ejecutar el contenido del archivo datos.
Ejecutar el contenido de otros requerimientos (trigger + packages).

2. Backend
cd Back
npm install
Configurar la conexión a Oracle en el archivo de configuración
node app.js
El servidor corre en http://localhost:5000

3. Frontend
cd Front
npm install
npm start
La aplicación corre en http://localhost:3000

## Funcionalidades destacadas (SQL / PL-SQL)

Diseño relacional con integridad referencial completa
Uso de IDENTITY columns
Trigger BEFORE INSERT con lógica condicional y auditoría
Packages con funciones y procedimientos
Manejo de excepciones (NO_DATA_FOUND, OTHERS)
Consultas con LEFT JOIN y agregaciones
Lógica de stock disponible (cantidad actual - cantidad vendida)
