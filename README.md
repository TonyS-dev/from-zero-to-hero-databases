# Guía Exhaustiva de Bases de Datos: Estructuras, Operaciones y Consultas

Esta guía es una referencia detallada sobre los conceptos, atributos, métodos y consultas que definen las bases de datos relacionales (SQL) y no relacionales (NoSQL). Se enfoca en la funcionalidad y la aplicación práctica, utilizando ejemplos consistentes para ilustrar cada tema a fondo.

---

## Tabla de Contenidos
1.  [Conceptos Fundamentales](#1-conceptos-fundamentales) <br>
    1.1. [¿Qué es un Dato?](#11-qué-es-un-dato) <br>
    1.2. [¿Qué es una Base de Datos?](#12-qué-es-una-base-de-datos) <br>
    1.3. [¿Qué es un Sistema de Gestión de Bases de Datos (DBMS)?](#13-qué-es-un-sistema-de-gestión-de-bases-de-datos-dbms) <br>
    1.4. [Importancia de las Bases de Datos en la Industria del Software](#importancia-de-las-bases-de-datos-en-la-industria-del-software) <br>
    1.5. [Paradigmas de Bases de Datos: SQL vs. NoSQL](#14-paradigmas-de-bases-de-datos-sql-vs-nosql) <br>
2.  [El Mundo Relacional (SQL)](#2-el-mundo-relacional-sql) <br>
    2.1. [Motores de Bases Relacionales Populares](#21-motores-de-bases-relacionales-populares) <br>
    2.2. [Atributos y Estructura de Datos](#22-atributos-y-estructura-de-datos) <br>
        2.2.1. [Componentes Clave de una Base de Datos Relacional](#221-componentes-clave-de-una-base-de-datos-relacional) <br>
        2.2.2. [Claves: Los Pilares de las Relaciones](#222-claves-los-pilares-de-las-relaciones) <br>
        2.2.3. [Tipos de Datos (Definición de Atributos)](#223-tipos-de-datos-definición-de-atributos) <br>
    2.3. [Normalización: Diseño de Bases de Datos Óptimas (Ejemplo Hospital)](#23-normalización-diseño-de-bases-de-datos-óptimas-ejemplo-hospital) <br>
    2.4. [Lenguaje de Consultas SQL: Comandos y Métodos](#24-lenguaje-de-consultas-sql-comandos-y-métodos) <br>
        2.4.1. [DDL (Data Definition Language)](#241-ddl-data-definition-language---para-definir-la-estructura) <br>
        2.4.2. [DML (Data Manipulation Language)](#242-dml-data-manipulation-language---para-manipular-los-datos) <br>
        2.4.3. [DCL (Data Control Language)](#243-dcl-data-control-language---para-gestionar-permisos) <br>
        2.4.4. [TCL (Transaction Control Language)](#244-tcl-transaction-control-language---para-gestionar-transacciones) <br>
        2.4.5. [DQL (Data Query Language)](#245-dql-data-query-language---para-consultar-datos) <br>
        2.4.6. [JOINs: Combinando Tablas](#246-joins-combinando-tablas) <br>
    2.5. [Vistas (VIEW)](#25-vistas-view) <br>
3.  [El Mundo No Relacional (NoSQL - MongoDB)](#3-el-mundo-no-relacional-nosql---mongodb) <br>
    3.1. [Estructura y Atributos](#31-estructura-y-atributos) <br>
    3.2. [Operaciones y Consultas (Métodos)](#32-operaciones-y-consultas-métodos) <br>

---

## 1. Conceptos Fundamentales

### 1.1. ¿Qué es un Dato?
Un dato es la unidad de información más elemental. Es una representación simbólica (numérica, alfabética, algorítmica) de un atributo o característica de una entidad del mundo real. Por sí solos, los datos pueden carecer de contexto, pero son la materia prima para construir información útil.
*   **Ejemplo:** `Juan Pérez` (nombre), `35` (edad), `199.99` (precio).

### 1.2. ¿Qué es una Base de Datos?
Una base de datos es un sistema organizado y estructurado diseñado para almacenar, gestionar y recuperar grandes volúmenes de datos de manera eficiente, segura y consistente. Actúa como un repositorio centralizado que permite que la información fluya de manera precisa y controlada, siendo el corazón de la mayoría de las aplicaciones y sistemas de software.

### 1.3. ¿Qué es un Sistema de Gestión de Bases de Datos (DBMS)?
Un DBMS es el software que sirve como intermediario entre los usuarios/aplicaciones y la base de datos física. Simplifica la manipulación de datos al proporcionar una interfaz para realizar operaciones complejas.
*   **Función:** Gestiona la creación, consulta, actualización y eliminación de datos (CRUD), además de controlar el acceso, la seguridad, las copias de seguridad y la integridad de los datos.
*   **Analogía:** Si la base de datos es el motor de un coche, el DBMS es el conjunto de pedales, volante y palanca de cambios que te permite controlarlo.

### Importancia de las Bases de Datos en la Industria del Software
*   **Eficiencia en el Manejo de Datos:** Permiten gestionar grandes volúmenes de información de forma rápida.
*   **Seguridad y Consistencia:** Aseguran que los datos estén protegidos y sean coherentes.
*   **Independencia de los Datos:** El sistema de almacenamiento puede cambiar sin afectar a las aplicaciones.
*   **Menor Espacio de Almacenamiento:** Reducen la redundancia de datos.
*   **Escalabilidad:** Permiten que las aplicaciones crezcan y manejen más datos.
*   **Toma de Decisiones:** Facilitan el análisis de datos para tomar decisiones informadas.

### 1.4. Paradigmas de Bases de Datos: SQL vs. NoSQL
La decisión más importante al trabajar con datos es elegir el tipo de base de datos.
*   **Relacionales (SQL):** Organizan los datos en tablas con filas y columnas, siguiendo un esquema estricto predefinido. Son ideales para datos estructurados con relaciones claras y donde la consistencia es primordial.
*   **No Relacionales (NoSQL):** Ofrecen modelos de datos flexibles que no requieren un esquema fijo. Son especialmente útiles para grandes volúmenes de datos no estructurados, aplicaciones que cambian rápidamente y sistemas que necesitan escalar horizontalmente.


---

## 2. El Mundo Relacional (SQL)

### 2.1. Motores de Bases Relacionales Populares
Aunque todos usan SQL, existen diferentes "motores" o sistemas que gestionan la base de datos. Aquí algunos de los más populares:

| Motor | DBMS (Herramienta Gráfica) | Descripción |
| --- | --- | --- |
| **MySQL** | MySQL Workbench | De código abierto, muy popular en aplicaciones web, especialmente con PHP. Conocido por su rendimiento y facilidad de uso. |
| **PostgreSQL** | pgAdmin | De código abierto, conocido por su robustez, soporte para tipos de datos avanzados y cumplimiento de los estándares SQL. |
| **Microsoft SQL Server** | SQL Server Management Studio (SSMS) | Sistema de gestión de bases de datos relacional ampliamente utilizado en entornos empresariales. |
| **Oracle** | Oracle SQL Developer | Uno de los motores más potentes y populares en el ámbito empresarial, con ediciones gratuitas para desarrolladores. |
| **MariaDB** | phpMyAdmin | Un "fork" (derivado) de código abierto de MySQL, manteniendo una alta compatibilidad. |

No necesitas dominar todos los motores. Lo fundamental es aprender **SQL**, ya que es el lenguaje estándar que todos entienden.

### 2.2. Atributos y Estructura de Datos

#### 2.2.1. Componentes Clave de una Base de Datos Relacional
*   **Tabla (o Entidad):** Es la estructura principal, un conjunto de datos organizados en un formato de filas y columnas. Cada tabla almacena datos sobre un tipo específico de entidad. Ejemplo: una tabla `pacientes` para almacenar información de los pacientes.
*   **Columna (o Atributo):** Representa una característica o propiedad de la entidad. Cada columna tiene un nombre y un tipo de dato específico. Ejemplo: las columnas `nombre`, `fecha_nacimiento` y `direccion` en la tabla `pacientes`.
*   **Fila (o Registro / Tupla):** Es una instancia única de la entidad dentro de una tabla. Contiene un valor para cada columna. Ejemplo: la fila que contiene `('Ana Torres', '1990-05-12', 'Calle 123')`.
*   **Relaciones y Cardinalidad:** Son los vínculos lógicos entre dos o más tablas, establecidos mediante claves foráneas y, en el caso de relaciones muchos a muchos, mediante tablas pivote.
    *   **Uno a Uno (1:1):** Cada fila en una tabla A está relacionada con una única fila en una tabla B. Ejemplo: un paciente tiene un único historial médico.
        ```sql
        -- Ejemplo de FK para 1:1
        CREATE TABLE historiales_medicos (
            id_historial INT PRIMARY KEY AUTO_INCREMENT,
            id_paciente INT UNIQUE,
            -- ...otros campos...
            FOREIGN KEY (id_paciente) REFERENCES pacientes(id_paciente)
        );
        ```

    *   **Uno a Muchos (1:N):** Un paciente puede tener *muchas* citas, pero cada cita pertenece a *un* solo paciente. Se implementa agregando una clave foránea en la tabla `citas` que referencia a la tabla `pacientes`.
        ```sql
        -- Ejemplo de FK para 1:N
        CREATE TABLE citas (
            id_cita INT PRIMARY KEY AUTO_INCREMENT,
            id_paciente INT,
            -- ...otros campos...
            FOREIGN KEY (id_paciente) REFERENCES pacientes(id_paciente)
        );
        ```
    *   **Muchos a Muchos (M:N):** Un médico puede atender *muchos* pacientes y un paciente puede ser atendido por *muchos* médicos (en diferentes citas). Se implementa mediante una tabla pivote (por ejemplo, `citas`) que contiene las claves foráneas de ambas entidades.
        ```sql
        -- Tabla pivote para M:N
        CREATE TABLE citas (
            id_cita INT PRIMARY KEY AUTO_INCREMENT,
            id_paciente INT,
            id_medico INT,
            -- ...otros campos...
            FOREIGN KEY (id_paciente) REFERENCES pacientes(id_paciente),
            FOREIGN KEY (id_medico) REFERENCES medicos(id_medico)
        );
        ```


> **Nota Importante:** En el diseño de bases de datos relacionales, se recomienda nombrar las tablas, columnas y otros elementos utilizando el formato **snake_case** (por ejemplo, `tipos_de_documento`) para mejorar la legibilidad y evitar problemas de compatibilidad.

#### 2.2.2. Claves: Los Pilares de las Relaciones
*   **Clave Primaria (Primary Key - PK):** Es un atributo (o conjunto de atributos) que identifica de forma **única** a cada registro en una tabla. No puede contener valores nulos (`NULL`) y sus valores no se pueden repetir.
*   **Clave Foránea (Foreign Key - FK):** Es un atributo en una tabla que se corresponde con la clave primaria de otra tabla. Su propósito es **enlazar las tablas** y mantener la integridad referencial (asegurar que un valor de FK siempre apunte a un registro existente en la otra tabla).

#### 2.2.3. Tipos de Datos (Definición de Atributos)
Elegir el tipo de dato correcto es crucial para la integridad y la optimización del almacenamiento.

*   **Tipos Numéricos:**
    *   `TINYINT`: Entero muy pequeño (1 byte). Ideal para flags o estados.
    *   `INT` / `INTEGER`: Entero estándar (4 bytes). El más común para IDs y contadores.
    *   `BIGINT`: Entero grande (8 bytes). Para IDs en tablas masivas.
    *   `DECIMAL(precision, escala)`: Número de punto fijo con precisión exacta. **Esencial para datos monetarios** (ej. `DECIMAL(10, 2)`).
    *   `FLOAT` / `DOUBLE`: Números de punto flotante. Para cálculos científicos donde una ligera imprecisión es aceptable.

*   **Tipos de Cadena de Texto:**
    *   `VARCHAR(n)`: Almacena texto de longitud variable hasta `n` caracteres. Eficiente en espacio si la longitud de los datos varía.
    *   `CHAR(n)`: Almacena texto de longitud fija de `n` caracteres. Rellena con espacios si el texto es más corto. Útil para datos de longitud constante como códigos postales o abreviaturas.
    *   `TEXT`: Para almacenar grandes cantidades de texto (descripciones, artículos, comentarios).

*   **Tipos de Fecha y Hora:**
    *   `DATE`: Almacena solo la fecha (`YYYY-MM-DD`).
    *   `TIME`: Almacena solo la hora (`HH:MM:SS`).
    *   `DATETIME` / `TIMESTAMP`: Almacena fecha y hora completas. `TIMESTAMP` es útil para registrar la creación (`created_at`) y última modificación (`updated_at`) de un registro.

### 2.3. Normalización: Diseño de Bases de Datos Óptimas (Ejemplo Hospital)

La normalización es un proceso de diseño que organiza las tablas y sus relaciones para minimizar la **redundancia de datos** y evitar anomalías de manipulación (inserción, actualización, borrado).

#### **Primera Forma Normal (1NF): Atomicidad**

1.  **Regla:** Todos los valores en las celdas de una tabla deben ser atómicos (indivisibles). No se permiten listas, conjuntos ni valores múltiples en una sola celda.
2.  **Regla:** Cada fila debe ser única y no debe haber grupos de datos repetidos.

*   **Ejemplo NO normalizado:**
    | id_paciente | nombre | citas | fechas |
    | :--- | :--- | :--- | :--- |
    | 1 | Ana Torres | consulta, revisión | 2025-06-10, 2025-06-15 |

*   **Ejemplo Normalizado a 1NF:**
    | id_paciente | nombre | tipo_cita | fecha |
    | :--- | :--- | :--- | :--- |
    | 1 | Ana Torres | consulta | 2025-06-10 |
    | 1 | Ana Torres | revisión | 2025-06-15 |

#### **Segunda Forma Normal (2NF): Sin Dependencias Parciales**
1.  **Requisito:** La tabla debe estar en 1NF.
2.  **Regla:** Todos los atributos no clave deben depender completamente de la clave primaria compuesta.

*   **Ejemplo NO normalizado (Clave Primaria: `id_paciente` + `id_medico`):**
    | id_paciente | id_medico | nombre_paciente | nombre_medico | especialidad |
    | :--- | :--- | :--- | :--- | :--- |
    | 1 | 1 | Ana Torres | Dr. Juan Pérez | Cardiología |
    | 1 | 2 | Ana Torres | Dra. Marta Ruiz | Pediatría |

    *Análisis:* `nombre_paciente` depende solo de `id_paciente`, `nombre_medico` y `especialidad` dependen solo de `id_medico`.

*   **Solución Normalizada a 2NF:** Separar en tres tablas.
    *   **Tabla `Pacientes`:** `(id_paciente, nombre_paciente)`
    *   **Tabla `Medicos`:** `(id_medico, nombre_medico, especialidad)`
    *   **Tabla `Citas`:** `(id_paciente, id_medico, fecha)`

#### **Tercera Forma Normal (3NF): Sin Dependencias Transitivas**
1.  **Requisito:** La tabla debe estar en 2NF.
2.  **Regla:** Ningún atributo no clave depende de otro atributo no clave.

*   **Ejemplo NO normalizado (Clave Primaria: `id_cita`):**
    | id_cita | id_paciente | nombre_paciente | direccion_paciente |
    | :--- | :--- | :--- | :--- |
    | 1 | 1 | Ana Torres | Calle 123 |
    | 2 | 2 | Luis Gómez | Av. Central 45 |

    *Análisis:* `direccion_paciente` depende de `id_paciente`, no de la clave primaria `id_cita`.

*   **Solución Normalizada a 3NF:** Separar en dos tablas.
    *   **Tabla `Pacientes`:** `(id_paciente, nombre_paciente, direccion)`
    *   **Tabla `Citas`:** `(id_cita, id_paciente, fecha)`

### 2.4. Lenguaje de Consultas SQL: Comandos y Métodos

#### 2.4.1. DDL (Data Definition Language) - Para definir la estructura
*   **`CREATE`**: Crea objetos. Por ejemplo, una base de datos y tablas para un hospital.
    ```sql
    -- Crear la base de datos del hospital
    DROP DATABASE IF EXISTS hospital_db;
    CREATE DATABASE IF NOT EXISTS hospital_db;
    USE hospital_db;

    -- Crear la tabla de pacientes
    CREATE TABLE pacientes (
        id_paciente INT PRIMARY KEY AUTO_INCREMENT, -- Identificador único, autoincremental
        nombre VARCHAR(100) NOT NULL,               -- No puede estar vacío
        fecha_nacimiento DATE NOT NULL,             -- Fecha obligatoria
        genero ENUM('Masculino', 'Femenino', 'Otro') NOT NULL, -- Valor restringido
        direccion VARCHAR(255),                     -- Puede estar vacío
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, -- Fecha de creación automática
        updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP -- Fecha de última actualización
    );
    -- Usamos PRIMARY KEY para identificar cada paciente de forma única.
    -- AUTO_INCREMENT facilita la generación automática de IDs.
    -- NOT NULL obliga a que ciertos datos sean obligatorios.
    -- UNIQUE se usaría si queremos evitar duplicados (ejemplo en médicos).

    -- Crear la tabla de médicos
    CREATE TABLE medicos (
        id_medico INT PRIMARY KEY AUTO_INCREMENT,
        nombre VARCHAR(100) NOT NULL,
        especialidad VARCHAR(50) NOT NULL,
        correo VARCHAR(100) UNIQUE NOT NULL, -- No puede haber dos médicos con el mismo correo
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
        CHECK (especialidad <> '') -- La especialidad no puede estar vacía
    );

    -- Crear la tabla de citas
    CREATE TABLE citas (
        id_cita INT PRIMARY KEY AUTO_INCREMENT,
        id_paciente INT NOT NULL, -- Relación con pacientes
        id_medico INT NOT NULL,   -- Relación con médicos
        fecha DATETIME NOT NULL,
        motivo TEXT,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
        FOREIGN KEY (id_paciente) REFERENCES pacientes(id_paciente) ON DELETE CASCADE, -- Integridad referencial
        FOREIGN KEY (id_medico) REFERENCES medicos(id_medico) ON DELETE CASCADE,
        CHECK (fecha >= '2025-01-01') -- Solo permitir citas a partir de 2025
    );
    ```
*   **`ALTER`**: Modifica la estructura de una tabla.
    ```sql
    -- Agregar una columna para teléfono en pacientes
    ALTER TABLE pacientes ADD COLUMN telefono VARCHAR(20);
    -- Modificar la longitud de la columna especialidad en médicos
    ALTER TABLE medicos MODIFY COLUMN especialidad VARCHAR(100) NOT NULL;
    -- Eliminar la columna motivo en citas
    ALTER TABLE citas DROP COLUMN motivo;
    ```
*   **`DROP`**: Elimina un objeto de la base de datos.
    ```sql
    -- Eliminar la tabla de citas si ya no se necesita
    CREATE TABLE testeo_citas (
        id_cita INT PRIMARY KEY AUTO_INCREMENT,
        id_paciente INT NOT NULL,
        id_medico INT NOT NULL,
        fecha DATETIME NOT NULL,
        motivo TEXT,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
        FOREIGN KEY (id_paciente) REFERENCES pacientes(id_paciente) ON DELETE CASCADE,
        FOREIGN KEY (id_medico) REFERENCES medicos(id_medico) ON DELETE CASCADE,
        CHECK (fecha >= '2025-01-01')
    );
    DROP TABLE testeo_citas;
    ```
*   **`TRUNCATE`**: Elimina **todos** los datos de una tabla de forma rápida.
    ```sql
    -- Borrar todos los pacientes (pero la tabla sigue existiendo)
    CREATE TABLE pacientes_test (
        id_paciente INT PRIMARY KEY AUTO_INCREMENT,
        nombre VARCHAR(100) NOT NULL,
        fecha_nacimiento DATE NOT NULL,
        genero ENUM('Masculino', 'Femenino') NOT NULL,
        direccion VARCHAR(255) NOT NULL,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
    );
    INSERT INTO pacientes_test (nombre, fecha_nacimiento, genero, direccion) VALUES
        ('Ana Torres', '1990-05-12', 'Femenino', 'Calle 123'),
        ('Luis Gómez', '1985-11-30', 'Masculino', 'Av. Central 45'),
        ('María López', '1978-03-22', 'Femenino', 'Calle 456'),
        ('Carlos Ruiz', '2000-09-15', 'Masculino', 'Av. Libertad 10'),
        ('Sofía Martínez', '1995-12-01', 'Femenino', 'Calle 789'),
        ('Pedro Sánchez', '1988-07-30', 'Masculino', 'Calle 321'),
        ('Maria Sánchez', '1990-05-24', 'Femenino', 'Calle 321');
    TRUNCATE TABLE pacientes_test;
    ```

#### 2.4.2. DML (Data Manipulation Language) - Para manipular los datos
*   **`INSERT`**: Inserta nuevos registros.
    ```sql
    -- Insertar pacientes (varios registros en una sola instrucción)
    INSERT INTO pacientes (nombre, fecha_nacimiento, genero, direccion) VALUES
        ('Ana Torres', '1990-05-12', 'Femenino', 'Calle 123'),
        ('Luis Gómez', '1985-11-30', 'Masculino', 'Av. Central 45'),
        ('María López', '1978-03-22', 'Femenino', 'Calle 456'),
        ('Carlos Ruiz', '2000-09-15', 'Masculino', 'Av. Libertad 10'),
        ('Sofía Martínez', '1995-12-01', 'Femenino', 'Calle 789'),
        ('Pedro Sánchez', '1988-07-30', 'Masculino', 'Calle 321'),
        ('Maria Sánchez', '1990-05-24', 'Femenino', 'Calle 321');

    -- Insertar médicos (varios registros en una sola instrucción)
    INSERT INTO medicos (nombre, especialidad, correo) VALUES
        ('Dr. Juan Pérez', 'Cardiología', 'juan.perez@hospital.com'),
        ('Dra. Marta Ruiz', 'Pediatría', 'marta.ruiz@hospital.com'),
        ('Dr. Andrés Gómez', 'Neurología', 'andres.gomez@hospital.com'),
        ('Dra. Laura Torres', 'Dermatología', 'laura.torres@hospital.com');

    -- Insertar citas (varios registros en una sola instrucción)
    INSERT INTO citas (id_paciente, id_medico, fecha) VALUES
        (1, 1, '2025-06-10 09:00:00'),
        (2, 2, '2025-06-11 10:30:00'),
        (3, 3, '2025-06-12 11:00:00'),
        (4, 1, '2025-06-13 08:30:00'),
        (5, 4, '2025-06-14 14:00:00'),
        (6, 2, '2025-06-15 15:30:00'),
        (1, 3, '2025-06-16 09:45:00'),
        (2, 1, '2025-06-17 10:00:00'),
        (3, 4, '2025-06-18 11:15:00'),
        (4, 2, '2025-06-19 12:00:00');
    ```
*   **`UPDATE`**: Actualiza registros existentes. **¡Siempre usa `WHERE`!**
    ```sql
    -- Cambiar la dirección de un paciente
    UPDATE pacientes SET direccion = 'Calle Nueva 456' WHERE id_paciente = 1;
    -- Cambiar la especialidad de un médico
    UPDATE medicos SET especialidad = 'Neurología' WHERE id_medico = 1;
    ```
*   **`DELETE`**: Elimina registros. **¡Siempre usa `WHERE`!**
    ```sql
    -- Eliminar una cita específica
    DELETE FROM citas WHERE id_cita = 1;
    -- Eliminar un paciente
    DELETE FROM pacientes WHERE id_paciente = 2;
    ```

#### 2.4.3. DCL (Data Control Language) - Para gestionar permisos
*   **`GRANT`**: Otorga permisos a un usuario.
    ```sql
    DROP USER IF EXISTS 'recepcionista'@'localhost';
    CREATE USER 'recepcionista'@'localhost' IDENTIFIED BY 'clave123';
    GRANT SELECT, INSERT ON pacientes TO 'recepcionista'@'localhost';
    ```
*   **`REVOKE`**: Revoca permisos previamente otorgados.
    ```sql
    REVOKE INSERT ON pacientes FROM 'recepcionista'@'localhost';
    ```
*   **`SHOW`**: Muestra los permisos de un usuario.
    ```sql
    SHOW GRANTS FOR 'recepcionista'@'localhost';
    ```

#### 2.4.4. TCL (Transaction Control Language) - Para gestionar transacciones
*   **`COMMIT`**: Guarda de forma permanente todos los cambios de una transacción.
*   **`ROLLBACK`**: Deshace todos los cambios realizados en una transacción hasta el último `COMMIT`.
*   **`SAVEPOINT`**: Establece un punto de control dentro de una transacción al que se puede revertir.
    ```sql
    START TRANSACTION;
    UPDATE pacientes SET direccion = 'Calle 789' WHERE id_paciente = 1;
    SAVEPOINT direccion_actualizada;
    UPDATE pacientes SET direccion = 'Calle 000' WHERE id_paciente = 1;
    ROLLBACK TO direccion_actualizada;
    COMMIT;
    ```

#### 2.4.5. DQL (Data Query Language) - Para consultar datos
*   **`SELECT` y `FROM`**: La base de cualquier consulta.
    ```sql
    SELECT nombre, fecha_nacimiento FROM pacientes;

    -- * Para obtener los datos de todas las columnas
    SELECT * FROM medicos;
    ```
*   **`WHERE`**: Filtra registros.
    ```sql
    SELECT nombre FROM medicos WHERE especialidad = 'Neurología';
    ```
*   **`ORDER BY`**: Ordena los resultados.
    ```sql
    SELECT nombre, fecha_nacimiento FROM pacientes ORDER BY fecha_nacimiento DESC;
    ```
*   **`BETWEEN`**: Filtra un rango de valores.
    ```sql
    SELECT nombre FROM pacientes WHERE fecha_nacimiento BETWEEN '1980-01-01' AND '1995-12-31';
    ```
*   **`LIKE`**: Busca patrones en texto.
    ```sql
    SELECT nombre FROM pacientes WHERE nombre LIKE 'A%';
    ```
*   **`IS NULL` / `IS NOT NULL`**: Busca registros con valores nulos o no nulos.
    ```sql
    SELECT nombre FROM pacientes WHERE direccion IS NOT NULL;
    ```
*   **Funciones de Agregación**:
    *   `COUNT()`: `SELECT COUNT(*) FROM citas WHERE fecha > '2025-06-01';` (Cuenta citas futuras)
    *   `SUM()`: `SELECT SUM(id_medico) FROM citas;` (Ejemplo de suma, normalmente sumarías cantidades)
    *   `AVG()`: `SELECT AVG(YEAR(CURDATE())-YEAR(fecha_nacimiento)) FROM pacientes;` (Edad promedio)
    *   `MAX()` / `MIN()`: `SELECT MAX(fecha), MIN(fecha) FROM citas;` (Fecha más reciente y más antigua)
*   **`GROUP BY` y `HAVING`**:
    ```sql
    -- Número de citas por médico, solo médicos con más de 2 citas
    SELECT id_medico, COUNT(*) AS total_citas
    FROM citas
    GROUP BY id_medico
    HAVING COUNT(*) > 1;
    ```
*   **Subconsultas**:
    ```sql
    -- Pacientes con más citas que el promedio
    SELECT nombre FROM pacientes WHERE id_paciente IN (
        SELECT id_paciente FROM citas GROUP BY id_paciente HAVING COUNT(*) > (
            SELECT AVG(cantidad) FROM (SELECT COUNT(*) AS cantidad FROM citas GROUP BY id_paciente) AS sub
        )
    );
    ```
*   **Subconsultas avanzadas y análisis con CTE y funciones de ventana**:
    ##### ¿Qué es una CTE (Common Table Expression)?
    Una CTE es una tabla temporal con nombre que se define al inicio de una consulta y puede ser referenciada en el resto de la misma. Permite simplificar consultas complejas, mejorar la legibilidad y reutilizar resultados intermedios.

    ##### ¿Qué es una Función de Ventana?
    Las funciones de ventana permiten realizar cálculos (como sumas, conteos, promedios) sobre un conjunto de filas relacionadas con la fila actual, sin agrupar ni colapsar los resultados como lo hace GROUP BY. Son útiles para obtener totales, rankings y análisis avanzados dentro de la misma consulta.
    ```sql
    -- Consulta para obtener el médico con más citas usando subconsulta en la columna
    SELECT 
        p.nombre AS paciente,
        m.nombre AS medico,
        c.fecha,
        (
            SELECT COUNT(c_sub.id_cita)
            FROM citas c_sub
            WHERE c_sub.id_medico = c.id_medico
        ) AS total_citas_medico
    FROM citas c
    JOIN pacientes p ON c.id_paciente = p.id_paciente
    JOIN medicos m ON c.id_medico = m.id_medico
    ORDER BY total_citas_medico DESC;

    -- Consulta usando función de ventana para contar citas por médico
    SELECT
        p.nombre AS paciente,
        m.nombre AS medico,
        c.fecha,
        COUNT(c.id_cita) OVER (PARTITION BY c.id_medico) AS total_citas_medico
    FROM citas c
    JOIN pacientes p ON c.id_paciente = p.id_paciente
    JOIN medicos m ON c.id_medico = m.id_medico
    ORDER BY total_citas_medico DESC, c.fecha;

    -- Consulta con CTE para contar citas por paciente
    WITH ConteoPorPaciente AS (
        SELECT
            id_paciente,
            COUNT(id_cita) AS total_citas_paciente
        FROM
            citas
        GROUP BY
            id_paciente
    )
    SELECT 
        p.nombre AS paciente,
        m.nombre AS medico,
        c.fecha,
        cte.total_citas_paciente
    FROM 
        citas c
    JOIN 
        pacientes p ON c.id_paciente = p.id_paciente
    JOIN 
        medicos m ON c.id_medico = m.id_medico
    JOIN 
        ConteoPorPaciente cte ON c.id_paciente = cte.id_paciente
    ORDER BY 
        cte.total_citas_paciente DESC;
    ```

#### 2.4.6. JOINs: Combinando Tablas
*   **`INNER JOIN`**: Devuelve solo las filas que tienen una coincidencia en ambas tablas.
    ```sql
    -- Listar citas con nombre de paciente y médico
    SELECT c.fecha, p.nombre AS paciente, m.nombre AS medico
    FROM citas c
    INNER JOIN pacientes p ON c.id_paciente = p.id_paciente
    INNER JOIN medicos m ON c.id_medico = m.id_medico;
    ```
*   **`LEFT JOIN`**: Devuelve todas las filas de la tabla izquierda y las coincidentes de la derecha.
    ```sql
    -- Listar todos los pacientes y sus citas (si tienen)
    SELECT p.nombre, c.fecha
    FROM pacientes p
    LEFT JOIN citas c ON p.id_paciente = c.id_paciente;
    ```
*   **`RIGHT JOIN`**: Devuelve todas las filas de la tabla derecha y las coincidentes de la izquierda.
    ```sql
    -- Listar todos los médicos y las citas que tienen (si tienen)
    SELECT m.nombre, c.fecha
    FROM medicos m
    RIGHT JOIN citas c ON m.id_medico = c.id_medico;
    ```
*   **`FULL OUTER JOIN`**: Devuelve todas las filas cuando hay coincidencia en una de las tablas.
    ```sql
    -- No soportado directamente en MySQL, pero se puede simular con UNION
    SELECT p.nombre, c.fecha
    FROM pacientes p
    LEFT JOIN citas c ON p.id_paciente = c.id_paciente
    UNION
    SELECT p.nombre, c.fecha
    FROM pacientes p
    RIGHT JOIN citas c ON p.id_paciente = c.id_paciente;
    ```
*   **`SELF JOIN`**: Una tabla se une consigo misma.
    ```sql
    -- Ejemplo: Buscar pacientes con la misma dirección
    SELECT a.nombre AS paciente1, b.nombre AS paciente2, a.direccion
    FROM pacientes a
    INNER JOIN pacientes b ON a.direccion = b.direccion AND a.id_paciente <> b.id_paciente;
    ```
### 2.5. Vistas (VIEW)
* **Vistas (VIEW):** Permiten crear una consulta reutilizable como si fuera una tabla virtual.
    ```sql
    -- Crear una vista para el historial de citas de pacientes
    CREATE OR REPLACE VIEW vista_historial_citas AS
    SELECT
        p.nombre AS paciente,
        m.nombre AS medico,
        m.especialidad,
        c.fecha,
        c.created_at
    FROM citas c
    JOIN pacientes p ON c.id_paciente = p.id_paciente
    JOIN medicos m ON c.id_medico = m.id_medico;

    -- Consultar la vista para ver el historial completo
    SELECT * FROM vista_historial_citas ORDER BY fecha DESC;
    ```
---

## 3. El Mundo No Relacional (NoSQL - MongoDB)

### 3.1. Estructura y Atributos

#### 3.1.1. Introducción a MongoDB
MongoDB es una base de datos NoSQL orientada a documentos, que almacena datos en formato BSON (Binary JSON). Esto permite una representación rica y flexible de los datos, ideal para aplicaciones modernas.

#### 3.1.2. Comparación con Modelos Relacionales
*   **Estructura Libre:** A diferencia de las tablas rígidas de SQL, MongoDB usa colecciones y documentos, permitiendo una estructura más flexible.
*   **Escalabilidad Horizontal:** MongoDB está diseñado para escalar fácilmente agregando más servidores.
*   **Alto Rendimiento:** Optimizado para operaciones rápidas y eficientes.

#### 3.1.3. Conceptos Clave
*   **Base de Datos:** Contenedor que agrupa colecciones relacionadas.
*   **Colección:** Conjunto de documentos, equivalente a una tabla en SQL.
*   **Documento:** Registro individual en una colección, equivalente a una fila en SQL.

#### 3.1.4. Ejemplo de Estructura en MongoDB
```json
{
    "pacientes": [
        {
            "_id": "ObjectId('60d5ec49f1a2c30f88f3b2a1')",
            "nombre": "Ana Torres",
            "fecha_nacimiento": "1990-05-12",
            "genero": "Femenino",
            "direccion": "Calle 123",
            "telefonos": ["123456789", "987654321"],
            "historial_medico": {
                "alergias": ["pollen", "nuts"],
                "enfermedades_previas": ["asma"]
            }
        }
    ]
}
```

### 3.2. Operaciones y Consultas (Métodos)

#### 3.2.1. Introducción a las Consultas en MongoDB
Las consultas en MongoDB se realizan mediante documentos JSON que especifican los criterios de búsqueda. La sintaxis es intuitiva y se asemeja a la estructura de los propios documentos.

#### 3.2.2. Métodos Básicos
*   **`find()`**: Recupera documentos que coinciden con los criterios especificados.
*   **`insertOne()`** / **`insertMany()`**: Inserta uno o varios documentos en una colección.
*   **`updateOne()`** / **`updateMany()`**: Actualiza uno o varios documentos que coinciden con los criterios.
*   **`deleteOne()`** / **`deleteMany()`**: Elimina uno o varios documentos.

#### 3.2.3. Ejemplos de Consultas
```javascript
// Conectar a la base de datos
use hospital_db;

// Insertar un nuevo paciente
db.pacientes.insertOne({
    nombre: "Luis Gómez",
    fecha_nacimiento: "1985-11-30",
    genero: "Masculino",
    direccion: "Av. Central 45"
});

// Insertar pacientes
db.pacientes.insertMany([
    {
        nombre: "Ana Torres",
        fecha_nacimiento: "1990-05-12",
        genero: "Femenino",
        direccion: "Calle 123",
        telefonos: ["123456789", "987654321"],
        historial_medico: {
            alergias: ["pollen", "nuts"],
            enfermedades_previas: ["asma"]
        }
    },
    {
        nombre: "Andrés Martínez",
        fecha_nacimiento: "1988-02-15",
        genero: "Masculino",
        direccion: "Calle 456",
        telefonos: ["321654987"],
        historial_medico: {
            alergias: [],
            enfermedades_previas: ["diabetes"]
        }
    }
]);

// Encontrar un paciente por nombre
db.pacientes.find({ nombre: "Ana Torres" });

// Actualizar la dirección de un paciente
db.pacientes.updateOne(
    { nombre: "Ana Torres" },
    { $set: { direccion: "Calle Nueva 456" } }
);

// Eliminar un paciente
db.pacientes.deleteOne({ nombre: "Luis Gómez" });
```

#### 3.2.4. Consultas Avanzadas
*   **Consultas con Condiciones Múltiples:**
    ```javascript
    db.pacientes.find({
        $and: [
            { genero: "Femenino" },
            { "historial_medico.enfermedades_previas": "asma" }
        ]
    });
    ```
*   **Proyecciones:**
    ```javascript
    // Mostrar solo el nombre y la dirección de los pacientes
    db.pacientes.find({}, { nombre: 1, direccion: 1 });
    ```
*   **Ordenamiento y Limitación:**
    ```javascript
    // Obtener los 5 pacientes más recientes
    db.pacientes.find().sort({ fecha_nacimiento: -1 }).limit(5);
    ```
*   **Consultas en Arrays:**
    ```javascript
    // Encontrar pacientes con un número de teléfono específico
    db.pacientes.find({ telefonos: "123456789" });
    ```
*   **Uso de Expresiones Regulares:**
    ```javascript
    // Buscar pacientes cuyo nombre comienza con 'A'
    db.pacientes.find({ nombre: /^A/ });
    ```

#### 3.2.5. Agregaciones
Las operaciones de agregación en MongoDB permiten procesar datos y devolver resultados calculados.
```javascript
// Contar el número de pacientes por género
db.pacientes.aggregate([
    {
        $group: {
            _id: "$genero",
            total: { $sum: 1 }
        }
    }
]);

// Obtener la edad promedio de los pacientes
db.pacientes.aggregate([
    {
        $group: {
            _id: null,
            edad_promedio: {
                $avg: {
                    $divide: [
                        { $subtract: [new Date(), { $toDate: "$fecha_nacimiento" }] },
                        1000 * 60 * 60 * 24 * 365
                    ]
                }
            }
        }
    }
]);
```

#### 3.2.6. Índices
Los índices mejoran el rendimiento de las consultas al permitir un acceso más rápido a los documentos.
```javascript
// Crear un índice en el campo 'nombre'
db.pacientes.createIndex({ nombre: 1 });

// Consultar pacientes con un índice
db.pacientes.find({ nombre: "Ana Torres" }).hint({ nombre: 1 });
```

#### 3.2.7. Transacciones
Las transacciones permiten ejecutar múltiples operaciones de forma atómica.
```javascript
// Iniciar una sesión de transacción
const session = db.getMongo().startSession();
const pacientesCollection = session.getDatabase("hospital_db").pacientes;

// Iniciar una transacción
session.startTransaction();
try {
    // Operaciones dentro de la transacción
    pacientesCollection.updateOne({ nombre: "Ana Torres" }, { $set: { direccion: "Calle 000" } });
    pacientesCollection.deleteOne({ nombre: "Luis Gómez" });

    // Confirmar la transacción
    session.commitTransaction();
} catch (error) {
    // Cancelar la transacción en caso de error
    session.abortTransaction();
} finally {
    session.endSession();
}
```

#### 3.2.8. Métodos de Consulta Específicos
*   **`findOne()`**: Recupera un solo documento que coincide con los criterios.
*   **`countDocuments()`**: Cuenta el número de documentos que coinciden con los criterios.
*   **`distinct()`**: Devuelve los valores únicos de un campo específico.
```javascript
// Encontrar un solo paciente
db.pacientes.findOne({ nombre: "Ana Torres" });

// Contar el número de pacientes
db.pacientes.countDocuments();

// Obtener todos los géneros distintos en la colección de pacientes
db.pacientes.distinct("genero");
```

#### 3.2.9. Manejo de Errores
Es importante manejar los errores adecuadamente, especialmente en operaciones críticas como las transacciones.
```javascript
try {
    // Código que puede generar un error
} catch (error) {
    print(`Error: ${error.message}`);
}
```

#### 3.2.10. Resumen de Comandos Útiles
| Comando | Descripción |
| --- | --- |
| `db.pacientes.find()` | Recupera documentos de la colección `pacientes`. |
| `db.pacientes.insertOne()` | Inserta un nuevo documento en `pacientes`. |
| `db.pacientes.updateOne()` | Actualiza un documento en `pacientes`. |
| `db.pacientes.deleteOne()` | Elimina un documento de `pacientes`. |
| `db.pacientes.aggregate()` | Realiza operaciones de agregación. |
| `db.pacientes.createIndex()` | Crea un índice en un campo específico. |
| `db.getMongo().startSession()` | Inicia una sesión de transacción. |

---

Por: Antonio Santiago
