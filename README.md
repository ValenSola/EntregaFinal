# PROYECTO FINAL - Coderhouse/Backend

## Descripción

El objetivo de este proyecto fue aplicar los conocimientos adquiridos durante el curso "Programación Backend" de Coderhouse. Se llevó a cabo la integración de los diferentes desafíos del programa en el desarrollo de una API REST para un e-commerce con las siguientes características:

### Arquitectura SOA (Service-Oriented Architecture)

Se optó por una arquitectura orientada a servicios para organizar eficientemente las diversas funciones del sistema, permitiendo modularidad y escalabilidad.

### Cookies

Utilización del almacenamiento de tokens JWT en cookies, mejorando la seguridad del sistema y facilitando la gestión de sesiones.

### CRUD (Create, Read, Update, Delete)

Se implementó la funcionalidad completa de Crear, Leer, Actualizar y Eliminar (CRUD) para la gestión eficiente de usuarios, productos y carritos.

### Factory

Implementación de la configuración de persistencia utilizando el patrón Factory.

### DAO

Interacción directa con la fuente de datos. Proporciona métodos para realizar operaciones CRUD.

### Logger - Winston

Incorporación de Winston para la gestión de logs, mejorando la capacidad de seguimiento y depuración del sistema.

### Mailing - Nodemailer

Implementación de Nodemailer para el envío de correos electrónicos a los usuarios después de determinadas acciones, mejorando la interacción y la comunicación con los clientes.

### Manejo de errores - Customizador de errores

Customizador de errores básico y un diccionario para los errores más comunes al crear un producto, mejorando la experiencia del usuario y facilitando la resolución de problemas.

### Mocking - Faker

Utilización de Faker para la creación de usuarios y productos ficticios con fines de testing, mejorando la capacidad de realizar pruebas en diferentes escenarios.

### Motor de plantillas Handlebars

Implementación de Handlebars como motor de plantillas para la generación dinámica de contenido HTML, mejorando la presentación de la información.

### Pasarela de pago para tarjetas - Stripe

Incorporación de una pasarela de pago segura utilizando Stripe, permitiendo transacciones confiables en la plataforma.

### Passport y session para autenticación de terceros con GitHub

Integración de Passport y session para permitir la autenticación de usuarios a través de GitHub.

### Vercel

Despliegue de la aplicación.

### Repository

Actúa como un intermediario entre la capa de servicios y la capa de datos (DAO). Proporciona una interfaz simplificada para que los servicios interactúen con la base de datos sin necesidad de conocer los detalles de implementación de la persistencia.

### Ruteo avanzado - Custom Responses y restricción de parámetros

Ruteo avanzado que incluye respuestas personalizadas y restricciones de parámetros, mejorando la robustez y seguridad del sistema.

### Sistema de autenticación JSON Web Token (JWT)

Establecimiento de un sólido sistema de autenticación mediante JWT, asegurando la identidad de los usuarios a través de tokens firmados digitalmente.

### Sistema de roles y políticas - Handle Policies

Sistema de roles y políticas utilizando Handle Policies para gestionar con precisión los permisos y accesos a diferentes funcionalidades.

### Testing

- Artillery para el testing del flujo de registro y login de usuarios, mejorando la evaluación del rendimiento del sistema.

- Mocha + Chai + Supertest para llevar a cabo pruebas unitarias introductorias para algunas funcionalidades, asegurando la confiabilidad y el rendimiento del sistema.

### Websockets

Se llevó a cabo la incorporación de Websockets en un chat general y en vistas del administrador, proporcionando una comunicación bidireccional en tiempo real.

## Requerimientos específicos de la entrega :

### Router /api/users - rutas

- GET / - Obtiene a todos los usuarios y solo devuelve los datos principales: nombre, correo y tipo de cuenta (role).

  - <small>Directorio/s de referencia</small>

    - `src/components/users/index.js`: Rutas de users.
    - `src/components/users/usersController/usersController.js` : Controlador del método getPrincipalDataUser.
    - `src/components/users/usersServices/usersServices.js`: Servicios del método getPrincipalDataUser.

- DELETE / - Limpia a todos los usuarios que no hayan tenido conexión en los últimos 2 días y le envía un correo al usuario indicándole que su cuenta ha sido eliminada por inactividad. (Puedes hacer pruebas con el último minuto, por ejemplo. Ver código comentado del método **deleteInactiveUsers**).

  - <small>Directorio/s de referencia</small>

    - `src/components/users/index.js`: Rutas de users.
    - `src/components/users/usersController/usersController.js` : Controlador del método deleteInactiveUsers.
    - `src/components/users/usersServices/usersServices.js`: Servicios del método deleteInactiveUsers.

### Views

- ADMIN View - Vista donde se puede visualizar, modificar el role, eliminar un usuario y eliminar a los usuarios inactivos en los últimos 2 días. Esta vista únicamente es accesible para el administrador del ecommerce.

  - <small>Directorio/s de referencia</small>

    - `src/views/layouts/main.handlebars`: Main del motor de plantillas handlebars.
    - `src/views/adminDashboardUsers.handlebars` : Vista del Admin Dashboard de Usuarios.

    - `src/components/handlebars/index.js`: Rutas de views.
    - `src/components/handlebars/handlebarsController/handlebarsController.js` : Controlador del método getAdminDashboardUsers.
    - `src/components/handlebars/handlebarsServices/handlebarsServices.js`: Servicio del método getAdminDashboardUsers.

    - `src/components/users/index.js`: Rutas de users.
    - `src/components/users/usersController/usersController.js` : Controlador de los métodos getUserViews, updateUser , deletUser y deleteInactiveUsers.
    - `src/components/users/usersServices/usersServices.js`: Servicios de de los métodos getUserViews, updateUser , deletUser y deleteInactiveUsers.

### Endpoint /api/products/:pid

- Endpoint que elimina productos modificado. En caso de que el producto eliminado pertenezca a un usuario premium, le envía un correo indicándole que el producto fue eliminado.

  - <small>Directorio/s de referencia</small>

    - `src/components/products/index.js`: Rutas de productos.
    - `src/components/products/productsController/productsController.js`: Controlador del método deleteProduct.
    - `src/components/products/serviceController/serviceController.js`: Servicios del método deleteProduct.

## Credenciales de users con roles asignados para testing:<a name="credenciales"></a>

Cuando se inicia el servidor, si no existen en la base de datos, se crearán automáticamente usuarios y productos para realizar testings:

- 15 Productos y un user "owner" de los productos - Creados con Faker.
- 3 Usuarios con los roles "admin", "user" y "premium".

### Credenciales de Admin (role: "admin") creado en la DB al iniciar la app:

#### Email:

```
admin@correo.com
```

#### Password:

```
1234
```

### Credenciales de User (role: "user") creado en la DB al iniciar la app:

#### Email:

```
user@correo.com
```

#### Password:

```
1234
```

### Credenciales de User Premium (role: "premium") creado en la DB al iniciar la app:

#### Email:

```
premium@correo.com
```

#### Password:

```
1234
```

## STRIPE - Datos ficticios para simular el pago con tarjeta de crédito:

#### Card Number:

```
4242424242424242
```

#### MM/YY :

```
1234
```

#### CVC :

```
567
```

#### ZIP :

```
89123
```

## Testing - Mocha + Chai + Supertest

Realización de módulos de testing para el proyecto principal, utilizando los módulos de mocha, chai y supertest.
Incluye 3 (tres) tests desarrollados para:

- Router de products.
- Router de carts.
- Router de sessions.

<small>Directorio/s de referencia</small>

- `/test/carts.test.js`: Configuración del test de carts.
- `/test/products.test.js`: Configuración del test de products.
- `/test/sessions.test.js`: Configuración del test de sessions.

### Comando para ejecutar el test:

```bash
npm test
```

## Testing - Artillery

- Simulación de registro y logins de usuarios mediante artillery.

<small>Directorio/s de referencia</small>

- `src/components/users/index.js`: Rutas de users.
- `src/components/users/usersController/usersController.js` : Controlador del método createFakeUser.
- `src/components/users/usersServices/usersServices.js`: Servicios del método createFakeUser.

- `config.yaml`: Instrucciones de testing de nuestro respectivo flujo de performance con artillery.

- `restPerformance.json`: Archivo donde se guardan los resultados del test en formato json.

### Comandos para ejecutar el test con Artillery:

Para realizar pruebas de rendimiento con Artillery, sigue estos pasos:

- Iniciar la Aplicación:

  Ejecuta el siguiente comando en una terminal para iniciar la aplicación. Asegúrate de que la aplicación esté en ejecución antes de ejecutar las pruebas de Artillery.

```bash
npm run dev
```

- Ejecutar las pruebas con Artillery:

  Abre otra terminal y ejecuta el siguiente comando para iniciar las pruebas con Artillery. El archivo de configuración config.yaml se utiliza para definir las especificaciones de las pruebas. Los resultados se guardarán en el archivo restPerformance.json.

```bash
npx artillery run config.yaml --output restPerformance.json
```

- Resultados de las Pruebas:

  Después de ejecutar las pruebas, encontrarás los resultados en el archivo `restPerformance.json`. Puedes analizar este archivo para obtener información detallada sobre el rendimiento de la aplicación durante las pruebas.

### Estructura general del proyecto

Aquí tienes la estructura del proyecto con descripciones para cada directorio:

El proyecto sigue la siguiente estructura de directorios:

- `.env.example`: Archivo de ejemplo que muestra la estructura y variables de entorno requeridas para la configuración de la aplicación.

- `src/components`: Carpeta contenedora de todos los componentes. Cada componente contiene un archivo index.js con sus rutas, una carpeta de controlador y una de servicios.

- `src/config`: Configuración de la aplicación.

- `src/dao`: Configuración de persistencia de datos.

- `src/docs`: Documentación.

- `src/models`: Modelos de datos de la aplicación.

- `src/public`: Archivos públicos de la aplicación, como estilos CSS, imágenes y scripts JavaScript.

- `src/repositories`: Capas de acceso de datos.

- `src/routes`: Definición de rutas de la aplicación.

- `src/scripts`: Scripts.

- `src/uploads`: Repositorios de archivos subidos.

- `src/utils`: Archivos relacionados con la configuración de las utilidades reutilizables.

- `src/views`: Todas las vistas del proyecto.

- `src/test`: Test de funcionalidades.

- `src/index.js`: Punto de entrada principal para la ejecución de la aplicación.

- `src/errors.log`: Registro de errores.

## Enlace al sitio activo

- [Deploy en Render](https://entrega-final-psi.vercel.app/) (Funcionalidad Front-end básica) - Vercel

