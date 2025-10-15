# UOC – PR1: Validación BBDD y Cubo OLAP (Vehicles)

Proyecto académico del Máster en Ciencia de Datos (UOC) para la asignatura de Business Intelligence.  
Incluye la validación de bases de datos en **PostgreSQL** y **SQL Server**, y la construcción de un **cubo OLAP** en **SQL Server Analysis Services (SSAS)** a partir de la tabla `vehicles`.

---

## 🎯 Objetivos
- Validar la carga y estructura de datos en dos motores de bases de datos.
- Ejecutar consultas de comprobación y control de calidad.
- Crear una vista de origen de datos y un cubo OLAP con medidas y dimensiones básicas.

---

## 🧱 Arquitectura
| Componente | Descripción |
|-------------|-------------|
| **PostgreSQL (pgAdmin 4)** | Carga de tablas `dgt_type` y `municipalities`. |
| **SQL Server (SSMS)** | Carga y validación de `dgt_type` y `vehicles`. |
| **SSAS (Visual Studio 2017)** | Construcción del cubo multidimensional basado en `vehicles`. |
| **VDI UOC** | Entorno remoto utilizado para todas las conexiones. |

---

## 📂 Estructura del repositorio
```

PR1/
├── PR1_dgt_type.sql          # Script de creación y carga de tipos DGT
├── PR1_municipalities.sql    # Script de municipios
├── PR1_vehicles.sql          # Script de vehículos
└── DEST_suave/               # Proyecto SSAS (Visual Studio)
├── DEST_suave.database
├── DEST_suave.dwproj
├── SOURCE Suave.cube
├── SOURCE Suave.ds
├── SOURCE Suave.dsv
├── SOURCE Suave.partitions
└── Vehicles.dim

````

---

## 🧩 Consultas de validación

**PostgreSQL**
```sql
SELECT COUNT(*) FROM dbo.dgt_type;
SELECT * FROM dbo.dgt_type LIMIT 5;
SELECT des_subtype_dgt FROM dbo.dgt_type WHERE des_type_dgt='AUTOBUSES';

SELECT COUNT(*) FROM dbo.municipalities;
SELECT * FROM dbo.municipalities
 WHERE province_name='Madrid' AND altitude>1500;
````

**SQL Server**

```sql
SELECT COUNT(*) FROM dbo.dgt_type;
SELECT * FROM dbo.dgt_type WHERE LEN(des_subtype_dgt)<10;

SELECT COUNT(*) FROM dbo.vehicles;
SELECT * FROM dbo.vehicles
 WHERE brand='LAND ROVER' AND YEAR(registration_date)=2021;
```

---

## 🧠 Competencias adquiridas

* **Modelado de datos relacional y multidimensional.**
* **Creación de esquemas SQL** y ejecución de scripts DDL/DML.
* **Validación de integridad y exploración de datos** en PostgreSQL y SQL Server.
* Uso de **pgAdmin 4**, **SSMS** y **Visual Studio 2017 (SSAS)**.
* Comprensión de conceptos **OLAP**: medidas, dimensiones, vistas de datos.
* Manejo de **problemas comunes de autenticación, permisos y tipos de datos** entre sistemas.
* Aplicación práctica de flujos **ETL básicos** (extracción, validación y carga).

---

## 📊 Resultado final

El proyecto genera un cubo OLAP conectado a la base `SOURCE_suave`, con:

* Medida: **Count of Vehicles (id)**
* Dimensión: **Vehicles**
* Posibilidad de exploración por atributos como `brand`, `model` o `registration_date`.

---

## 🔒 Nota sobre el vídeo

El trabajo original incluía una grabación de validación y configuración.
Por privacidad, este repositorio publica únicamente **scripts, estructuras y metadatos** que permiten **reproducir la práctica** sin mostrar imagen ni voz.

---

## 📜 Licencia

Este repositorio se publica bajo licencia **MIT**.

