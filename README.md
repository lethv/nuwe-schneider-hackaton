# nuwe-schneider-hackaton

Durante la realización del hackaton se han encontrado 2 flags.
Tras encontrar la página wp.geohome.com y conseguir acceso a ella mediante la modificación de /etc/hosts se ha logrado acceso al github de desarrollo de geohome. En estos commits se encontraba la primera flag. Entre los commits se encontraba también la clave para validar la firma de tokens jwt.

![imagen](https://user-images.githubusercontent.com/36164157/169660163-c4ad6b7f-2434-485a-a68f-6fdb647fe142.png)

Además de esto, se explicaba también el funcionamiento de la API, que nos permitia generar nuevos usuarios y obtener su token JWT para autenticarse. Con esto y la clave, podíamos generar un token, adaptarlo para que el usuario al que se refería fuese "admin" y firmarlo con la clave lekeada.

![imagen](https://user-images.githubusercontent.com/36164157/169660348-61febf4f-4563-40ba-a3f9-b1c9c722e3fd.png)


Tras esto ganabamos acceso a /admin mediante el token modificado:
![imagen](https://user-images.githubusercontent.com/36164157/169660329-9c560516-aa2c-4025-85a5-a6db8492075b.png)

Con esto sacábamos la 2da flag.
Infructuosmanete se realizan las siguientes acciones:
- Escaneo del sistema mediante Nessus, única vulnerabilidad acceso anonimo vía samba. No practicable.
- Fuerzabruta sobre la funcionalidad wp.geohome.com/xmlrpc.php sobre el usuario geoadmin, con el objetivo de saltar las limitaciones y ganar acceso. Se consiguen listar todos los comandos pero no explotar el comando para consultar usuario.
- Por último se realiza exploración sobre CMS, encontrando:

![imagen](https://user-images.githubusercontent.com/36164157/169660028-eee76135-74e5-4417-b53e-033bc5a417db.png)

Posible XSS en el plugin de elementor.

En general los resultados han sido limitados, pero al tratarse de nuestro primer hackaton esperamos que nos sirva de experiencia para los proximos. Muchas gracias!

