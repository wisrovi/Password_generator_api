# Password_generator_api
 
Este proyecto crea una api_rest donde por un post a /password, se le envia un usuario en string (podria ser un id, mac, etc) y generara una clave que cumple todos los parametros de seguridad para ese usuario recibido, en respuesta a este usuario devolvera dicha clave generada y la misma clave encriptada en AES256.

A la par de generarla, y para evitar que se vuelva a repetir la clave o que si el mismo usuario vuelve a pedir la clave se le entregue la generada originalmente, estas claves se guardan en base de datos (mongo en esta ocasion).
