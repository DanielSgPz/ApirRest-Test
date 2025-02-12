
# ApiRest-Test :notebook_with_decorative_cover:

**Descripción del Proyecto :paperclip:**
Este proyecto es una aplicación web desarrollada en Laravel que actúa como un servicio web RESTful para gestionar usuarios. La aplicación utiliza un patrón Singleton para la conexión a la base de datos y DAO (Data Access Object) para interactuar con la tabla users, a demás se usa una autenticación básica para el acceso a las apis.


**Requisitos :white_check_mark:**

    PHP >= 7.3
    
    Composer
    
    Laravel >= 8.x
    
    Base de datos PostgreSQL
    
    Postman (opcional, para pruebas de API)
    
    Variables de entorno configuradas para la autenticación básica

**Instalación :sparkler:**

 - Clona el repositorio:

    https://github.com/DanielSgPz/ApiRest-Test

    cd ApiRest-Test

 - Instala las dependencias:

    composer install

 - Crea un archivo .env a partir del ejemplo:

    cp .env.example .env

 - Configura tu archivo .env con los datos de conexión a la base de
   datos y las credenciales para la autenticación básica:

  

    env
    DB_CONNECTION=pgsql
    DB_HOST=127.0.0.1
    DB_PORT=5432
    DB_DATABASE=usuarios
    DB_USERNAME=root
    DB_PASSWORD=
    
      
    BASIC_AUTH_USER=pruebas
    BASIC_AUTH_PASSWORD=prueba123

 - Genera la clave de la aplicación:

    php artisan key:generate

 - Ejecuta las migraciones para crear las tablas en la base de datos:

  

    php artisan migrate

## Uso :muscle:

**Rutas:link:**
La aplicación define las siguientes rutas para la gestión de usuarios. Todas las rutas están protegidas por middleware de autenticación básica.

  

 - Registrar usuario: POST /users/register
 - Obtener todos los usuarios: GET /users
 - Obtener usuario por ID: GET /users/{id}
 - Actualizar usuario por ID: PUT /users/{id}
 - Eliminar usuario por ID: DELETE /users/{id}

**Ejemplo de Peticiones con Postman**

**Registrar Usuario**

*Método: POST*
URL: /users/register
*Authorization: Basic Auth (usuario y contraseña configurados en .env)*

*Body (raw, JSON):*

    {
    "name": "John Doe",
    
    "email": "john.doe@example.com",
    
    "password": "password123"
    }

**Obtener Todos los Usuarios**

*Método: GET*
*URL: /users*
*Authorization: Basic Auth (usuario y contraseña configurados en .env)*

**Obtener Usuario por ID**
*Método: GET*
*URL: /users/{id}
Authorization: Basic Auth (usuario y contraseña configurados en .env)*

**Actualizar Usuario por ID**
*Método: PUT
URL: /users/{id}
Authorization: Basic Auth (usuario y contraseña configurados en .env)*

Body (raw, JSON):

    {
    "name": "John Doe Updated",
    "email": "john.doe.updated@example.com",
    "password": "newpassword123"
    }

**Eliminar Usuario por ID**

*Método: DELETE
URL: /users/{id}
Authorization: Basic Auth (usuario y contraseña configurados en .env)*

## Estructura del Código

**Singleton de Conexión a la Base de Datos**

El patrón Singleton se utiliza para asegurar que haya una única instancia de la conexión a la base de datos.


**DAO para la Gestión de Usuarios**

El DAO proporciona métodos para interactuar con la tabla users.

  
**Controlador de Usuarios**

El controlador utiliza el DAO para gestionar las peticiones relacionadas con los usuarios.


**Middleware de Autenticación Básica**

Este middleware protege las rutas de la API mediante autenticación básica.


**Definición de Rutas**

Las rutas para la gestión de usuarios se definen en routes/api.php y están protegidas por el middleware de autenticación básica.

Las rutas para las vistas se definen en routes/web.php.


