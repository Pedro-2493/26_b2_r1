# Proyecto - Sistema de Gestión de Estudiantes

Este es un proyecto backend desarrollado con **Java 21** y **Spring Boot** para la gestión de estudiantes. Incluye una API RESTful que permite crear, leer, actualizar y eliminar (CRUD) registros de estudiantes, persistiendo los datos en una base de datos **PostgreSQL**.

## 🚀 Tecnologías Utilizadas

- **Java 21**: Lenguaje de programación.
- **Spring Boot 3.x**: Framework para el desarrollo de la aplicación.
- **Maven**: Gestor de dependencias y construcción.
- **PostgreSQL**: Base de datos relacional.
- **Lombok**: Librería para reducir el código boilerplate (Getters, Setters, etc.).
- **Spring Data JPA**: Abstracción para la capa de persistencia.

## 📋 Requisitos Previos

Asegúrate de tener instalado lo siguiente en tu entorno local:

- [Java JDK 21](https://www.oracle.com/java/technologies/downloads/#java21)
- [Maven](https://maven.apache.org/download.cgi)
- Cliente para probar la API (como [Postman](https://www.postman.com/) o [Insomnia](https://insomnia.rest/)).

## ⚙️ Configuración

La configuración de la base de datos se maneja a través de variables de entorno definidas en un archivo `.env` en la raíz del proyecto.

1.  Copia el archivo de ejemplo:
    ```bash
    copy .env.example .env
    ```

2.  Edita el archivo `.env` y define tus credenciales:
    ```ini
    DB_URL=jdbc:postgresql://localhost:5432/tu_base_de_datos
    DB_USERNAME=tu_usuario
    DB_PASSWORD=tu_contraseña
    ```

> **Nota:** El archivo `.env` está excluido del control de versiones para mantener tus credenciales seguras.

## 🛠️ Instalación y Ejecución (Windows)

1.  **Clonar el repositorio**:
    ```powershell
    git clone <url-del-repositorio>
    cd pi
    ```

2.  **Compilar el proyecto**:
    Asegúrate de estar en la raíz del proyecto y ejecuta:
    ```powershell
    .\mvnw.cmd clean install
    ```
    *Nota: Si tienes Maven instalado globalmente, puedes usar simplemente `mvn clean install`.*

3.  **Ejecutar la aplicación**:
    ```powershell
    .\mvnw.cmd spring-boot:run
    ```

    La aplicación se iniciará en el puerto `8080` (por defecto).

## 🔌 Uso de la API (Endpoints)

La API base es `/api/students`. A continuación se detallan los endpoints disponibles:

### 1. Obtener todos los estudiantes
- **Método**: `GET`
- **URL**: `/api/students`
- **Respuesta**: Lista de estudiantes en formato JSON.

### 2. Obtener un estudiante por ID
- **Método**: `GET`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`

### 3. Obtener un estudiante por Email
- **Método**: `GET`
- **URL**: `/api/students/email/{email}`
- **Ejemplo**: `/api/students/email/ejemplo@correo.com`

### 4. Crear un nuevo estudiante
- **Método**: `POST`
- **URL**: `/api/students`
- **Body (JSON)**:
    ```json
    {
      "firstName": "Juan",
      "lastName": "Pérez",
      "email": "juan.perez@example.com",
      "birthDate": "2000-01-15",
      "phone": "1234567890"
    }
    ```

### 5. Actualizar un estudiante
- **Método**: `PUT`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`
- **Body (JSON)**:
    ```json
    {
      "firstName": "Juan Carlos",
      "lastName": "Pérez",
      "email": "juan.perez@example.com",
      "birthDate": "2000-01-15",
      "phone": "0987654321"
    }
    ```

### 6. Eliminar un estudiante
- **Método**: `DELETE`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`

## 🧪 Ejecutar Pruebas

Para ejecutar las pruebas unitarias y de integración, usa el siguiente comando:

```powershell
.\mvnw.cmd test
```

## 📂 Estructura del Proyecto

```
src/main/java/com/cesde/pi
├── controller    # Controladores REST (StudentController)
├── model         # Entidades JPA (Student)
├── repository    # Interfaces de Repositorio (StudentRepository)
├── service       # Lógica de Negocio (StudentService)
├── dto           # Objetos de Transferencia de Datos
└── exception     # Manejo de Excepciones Globales
```

# Laboratorio: Documentación de Pruebas de API REST

## Información del estudiante
- **nombre** Pedro Luis Zamora Martinez

---

## Pruebas de Endpoints

### 1. Crear estudiante (POST)
- **Método**: `POST`
- **URL**: `http://localhost:8080/api/students`
- **Cuerpo de la petición**: 
```json


{
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "phone": "3004445566"    
    
}
```
- **Código de estado**:`201 Created`
- **Respuesta del servidor**:
```json
{
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id":"1",
    "phone": "3004445566"
       
    
}
```

---

### 2. Obtener lista completa (GET)
- **Método**: `GET`
- **URL**: `http://localhost:8080/api/students`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**:`200 OK`
- **Respuesta del servidor**:
```json
[
   {
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id":"1",
    "phone": "3004445566"    
    },
    {
        "firstName": "Andres",
        "lastName": "Garcia",
        "email": "andres.garcia@example.com",
        "birthDate": "1990-01-01",
        "id": 2,
        "phone": "312565466"
    },
    {
        "firstName": "Maria",
        "lastName": "Mendoza",
        "email": "maria.mendoza@example.com",
        "birthDate": "1985-05-05",
        "id": 3,
        "phone": "312565466"
    },
    {
        "firstName": "Kevin",
        "lastName": "Velez",
        "email": "kevin.Velez_marin@example.com",
        "birthDate": "1990-07-10",
        "id": 4,
        "phone": "3154562134"
    },
    {
        "firstName": "David",
        "lastName": "Martinez",
        "email": "David.Mar@example.com",
        "birthDate": "1993-05-22",
        "id": 5,
        "phone": "3004587785"
    }
]
```

### 3. Buscar estudiante por ID (GET)
- **Método**: `GET`
- **URL**: `http://localhost:8080/api/students/1`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**:`200 OK`
- **Respuesta del servidor**:
```json
   {
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id":"1",
    "phone": "3004445566"    
    }
```

### 4. Buscar estudiante por Email (GET)
- **Método**: `GET`
- **URL**: `http://localhost:8080/api/students/email/ana.garcia@estudiante.com`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**: `200 OK`
- **Respuesta del servidor**:
```json
 {
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id":"1",
    "phone": "3004445566"    
    }
```

### 5. Actualizar datos del estudante (PUT)
- **Método**: `PUT`
- **URL**: `http://localhost:8080/api/students/1`
- **Cuerpo de la petición**: 
```json
   {
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id":"1",
    "phone": "3004445566"    
    }
```
- **Código de estado**: `200 OK`
- **Respuesta del servidor**:
```json
  {
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id":"1",
    "phone": "3114566852"    
    }
```

### 6.Escenario de error: Buscar ID inexistente (GET)
- **Método**: `GET`
- **URL**: `http:localhost:8080/api/students/999`
- **Cuerpo de la petición**: Sin body
```json

```
- **Código de estado**: `404 Not Found`
- **Respuesta del servidor**:
```json

```

### 7. Eliminar registro (DELETE)
- **Método**: `DELETE`
- **URL**: `http:localhost:8080/api/students/1`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**: `204 No Content`
- **Respuesta del servidor**:
```json

```

## Análisis de Técnico

### 1. Diferenciación semántica: 200 vs 201

El código **201 Created** se reserva exlusivamente para decir que nuestro recurso (`POST`) se creo con éxito, confirmando que el servidor ha asignado un URI al nuevo objeto, el código **200 OK** es generico para operaciones de lectura o actualización donde el recurso ya existe.

- **Endpoints**: 201 en el punto 1; 200 en los puntos 2,3,4 y 5.

### 2. Importancia del error 404 sobre el 500

Un **404** es un error de cliente (lógica de negocio): indica que la ruta es valida pero el dato no existe. Un **500** es una falla critica del servidor (exepción no controlada).
Para un desarrollador Frontend, el 404 permite ejecutar una validación de interfaz (ej."Usuario no encontrado"), mientras que el 500 obliga a reportar un fallo en la infraestructura del Backend.

### 3. Impacto en Persistencia (PostgreSQL)

Al ejecutar un `DELETE`, postgreSQL ejecuta un comando de manipulacón de datos (DML) que elimina la tupla específica de la tabla mediante su Primary Key. En terminos de persistensia, se rompe el vínculo físico de esos datos, liberando el espacio y garantizando que futuras consultas no recuperen información residual.

### 4. Escenario de Duplicidad de Email

Al intentar registrar un nuevo estudiante con un email preexistente, el sistema retorna un **409 Conflict**. Esto ocurre por que el campo {email} posee una restricción de unicidad (`UNIQUE CONSTRAINT`) a nivel de esquema. El servidor detecta el conflicto antes de comprometer la transacción.

### 5. Idempotencia: PUT vs POST

Utilizamos **PUT** por su propiedad de **idempotencia**: múltiples peticiones identicas resultarán siempre en el mismo estado del recurso. **POST** no es idempotente; si se utilizara para actualizar, se correria el riesgo de generar efectos secundarios indeseados o duplicados en implementaciones no controladas. La convención REST dicta que PUT reemplaza un recurso conocido, mientras que POST crea uno nuevo o procesa datos.
