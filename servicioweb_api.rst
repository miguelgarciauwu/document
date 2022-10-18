****************
Servicio Web Api
****************

El protocolo HTTP no sirve sólo para proveer páginas web sino también es una potente plataforma para la construcción de APIs que exponen 
servicios y datos. HTTP es simple, flexible y ubicuo. Casi cualquier plataforma actualmente tiene o utiliza el protocolo HTTP, por lo que 
los servicios HTTP pueden llegar a una amplia gama de clientes, incluyendo los navegadores, dispositivos móviles y aplicaciones de escritorio 
tradicionales. 

Microsoft ASP.NET WebAPI es un marco para la construcción de las API web en la parte superior del marco .NET de Microsoft 
que permite aprovechar todo el conjunto de características presente sobre el protocolo HTTP. 

El servicio WebAPI de LegisOffice utiliza esta herramienta de Microsoft WebAPI para exponer servicios a sus clientes mediante 
peticiones HTTP (GET, POST, PUT, DELETE) en formato JSON.

El servicio WebAPI de LegisOffice se encarga de exponer métodos generales de recepción de información de vigilancia judicial 
a partir de un mecanismo de autenticación basado en Usuario / Clave / Proveedor. 

Para poder acceder a algún un recurso – excepto Test y ValidarCredenciales – es requerido que el cliente incluya el Token 
de acceso - obtenido al validar sus credenciales - en el encabezado de autorización de la petición HTTP.

A continuación, se describen a detalla los contratos expuestos en el servicio WebAPI.

URL del servicio en producción: https://vj.legisoffice.com/LOServiceVJ/. Todos los recursos están agrupados sobre el controlador 
llamado: VJ, la URL de consumo quedaría así: https://vj.legisoffice.com/LOServiceVJ/VJ/ + EL RECURSO SOLICITADO


**Test**

Método HTTP: GET
Verifica si el servicio de vigilancia judicial está disponible.
INFORMACIÓN SOLICITUD
Parámetros URL: Ninguno

Parámetros cuerpo solicitud: Ninguno

INFORMACIÓN RESPUESTA

+--------------+-------------------------------------+----------------+
|  Tipo        | Descripcion                         | Mensaje        |
|              |                                     |                |
+==============+=====================================+================+
| String       | Mensaje de conexión establecida     | Conexión       |
+--------------+-------------------------------------+----------------+

===================
ValidarCredenciales
===================

Método HTTP: **POST**
Valida las credenciales de autenticación para un proveedor y genera un identificador único de sesión

---------------------
INFORMACIÓN SOLICITUD
---------------------

Parámetros URL: Ninguno

Parámetros cuerpo solicitud:

+--------------+-------------------------------------------------------------------------------------+
|  Objeto      | AutenticaciónModel                                                                  | 
+==============+=====================================+================+================+=============+
| Nombre       | Descripcion                         | Tipo           | Obligatorio    |Restricción  | 
+--------------+-------------------------------------+----------------+----------------+-------------+
| Usuario      | Nombre de Usuario                   | String         | Si             |             | 
+--------------+-------------------------------------+----------------+----------------+-------------+
| Clave        | Constraseña                         | String         | Si             |             | 
+--------------+-------------------------------------+----------------+----------------+-------------+
| Proveedor    | Nombre del proveedor                | String         | Si             |             | 
+--------------+-------------------------------------+----------------+----------------+-------------+


