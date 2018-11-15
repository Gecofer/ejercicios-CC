# MICROSERVICIOS Y POR QUÉ DEBERÍAN DE IMPORTARME

## Comenzamos con un monolítico

*Monolito*: aplicaciones tradicionales, siguen un flujo, lo que habitualmente se llaman, aplicaciones en pila.

- Nosotros no queremos una app tan tradicional, usaremos gancho de github.

- Está hecho en ruby y con el microframework Sinatra.

- Tres microservicios:
  1. Responde una petición desde github
  2. Hacer una peticion a github
  3. Almacenarlo en una BD

## Usa ngrok para url
### Alta de hook en github

*Concepto de Hook*: Programa que se van a ejecutar cuando sucede algo. Noostros usamos el alta del hook en github

- Doy eso de alta (suele durar 8 horas) y puedo trabajar desde Github. En un momento determinadado, va a recibir muchas peticiones y tiene que hacer los 3 puntos comentados previamente. Tener una aplicación monolítica de esto, es
peligroso.

## REST, el interfaz universal

- Se utiliza para llamada a procedimientos. Cada una de las transacciones no tienen estado. Está basada en las órdenes de HTTP _put_ (crear recurso), _get_ (recuperar recurso), _post_ (modificar recurso), _delete_ (eliminar recurso).

- Usa tambien los estados que devuelve HTTP. Los estado de HTTP tienen 3 cifras:

    - 200 signgica OK, te los devuelve en los metadatos del mensaje (cabecera del mensaje)
    - 300 significa que ha pasado algo
    - 404 significa página no encontrado, ha pasado algo y la culpa es tuya
    - 500 ha pasado algo y la culpa es mía

- El tipo de mensaje: desribe el contenido, la mayoría de las veces vamos a usar JSON (aplicaciones/JSON)

## Problemas monoliticos: Incontsista en la respuesta

- _Difícil escalado_: solo escalar de forma horizontal, ¿pero y el precio? Creando más MV, pero si solo escalas el servicio que ncesitas.
- _Inflexibilidad en implementación_: no te deja usar los lenguajes que quieras o librerías.

## Arquitectura basada en MICROSERVICIOS

- Creas una aplicación, y son replicas de una sola cosa.
- Creas una arquitectura a partir de muchas cosas, en base a muchas piezas, y esas piezas forman un todo, que forma una apliacioón.
- Metafora: crear un mosaico a partir de otros mas chiquititos.

- _Divide por servicios autónomos_: Servicios que no necesitan de ningún otro, una parte que tú puedes programas de forma autonama.

- Podemos testear de forma independiente y no necesitamos de GITHUB para testearlo.


##### Microservicio que solo responde a la petición de GIthub.

Tenemos uan cola de mensaje, va a leer la petición de Github, y una vez hecho eso, va a publicar esta cadena en una cola que hemos definido anteriormente (hook o gancho). Aquí estamos empezando a crear esta aqruitectura --> cola de mensjaes usa RabbitMQ (brojer que hestiona esa cola de mensaje) Cuando le dices que te un mensaje te lo da.

## Presentando a RabbitMQ

- Usando un interfaz estándar permite usar muchos microservicios.
- Hay mas implmentaciones.
- Tiene clientes para muchos lenguajes.

- Recibe la petición; lee, dispara y olvida y ya esta listo para la siguiente peticion (tener instalado previamente).
- Se conetan estos dos microservicios a través de la cola --> soluciona problema de escalado.

- Esto tambien se llama colas de mensajes o broker. _Broker_: intermedia entre las distintas partes de la aplicacion.

- Ahora vamos a trabajar con Python --> la biblioteca se llama Pyka la que usa RabbitMQ.
- Biblioteca cereli
- El de Ruby se llama Bunny
- el de Pythn se llama Pika

- Toda esta imnformacion, la vamos a pasar al tercer microservicio, para ello usamos _put_, que el contenido es aplications/json
- POST: modificar recursos con urllib
- PUT: crear nuevo repositorio
covertimos a json el fichero

- Ahora vamos hacer uso del tercer microservicio
- Librería CRO

*TRes microservicios diferents unidos por interfaces estandar diferentes, es lo que usa*


## Publicando en la Web

Todo esto es que:

- Heroku: plataforma como Servicios
- seit.co: depslegar o en javaescript o contenderos docker
- Azure Webpps

Lo podemos publicar de distintas maneras nativas o en MVs. La idea principal es que cada una de estos microservicios vaya con un docker.
