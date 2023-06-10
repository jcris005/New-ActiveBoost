# Proyecto M12

## 1. Valorar proyecto:

- Lo primero sería pensar qué proyecto sería el indicado para aprobar la asignatura y sea compatible, así que pensé en los trabajos de la mayoría de mis compañeros y
 decidí montar un negocio de venta de productos, como tos.

- Posibles ideas:
    - Una de mis primeras ideas fue simular el Canódromo, que es la empresa donde hago las prácticas, me pareció buena idea debido a que tengo mucha información sobre ello y además tengo a mi tutor de prácticas para preguntarle sobre varios ámbitos.
    - También pensé en una tienda de suplementación deportiva.
    - También en un gimnasio.

Estas son las ideas que más me convencieron, pero descarte la primera pensando en su complejidad a la hora de ejecutar el plan y me dio miedo no hacerlo del todo bien, ya que el canódromo ofrece diversos servicios y me iba a costar mucho tiempo ejecútalo, y el tiempo es lo que me faltaba.

Opté por la segunda opción debido a que me pareció la más asequible al tiempo disponible.

La tercera opción me pareció la más entretenida, pero visto como nos fue con la peluquería, mejor opté por la segunda.

### 1.1 Valorar nombre de la empresa:

- Primero hagamos un listado de posibles nombre originales:

    - FitSupp
    - SupremeFit
    - MusclePro
    - VitaSport
    - ElevateNutrition
    - ActiveBoost
    - OptiHealth
    - IronEdge
    - ProVitality
    - PeakFuel
    - EliteSupps
    - PrimeNutrition

Esta es la lista de las opciones recomendadas, al final opte por ActiveBoost, ya que el nombre es pegadizo y además pensé que nuestros productos estrella serán los prework que te activa.

Nuestra Empresa aparte de dedicarse a la venta de suplementos deportivos, también se dedicará a la venta de material de GYM así tendremos más variedad en la tienda.

## 2. Administración de Trabajos

Para este primer día /4/6/23 comencé a pensar en cómo tenía que hacer el proyecto de recuperación, no recibí ninguna instrucción ni respuesta a los mensajes hechos a los maestros, debido a que tengo poco tiempo preferí ya a comenzarlo, pensé que sería como el último proyecto y me puse a ello.

Para comenzar el trabajo primero pensé en crear una plantilla en trello para administrar mi trabajo:

![Trello](fotos/trello.png)

Creé esos trabajos de momento para iniciar mi proyecto.

## 3. Localización

En primer lugar, decidí que mi local estuviera lo más cerca posible a un GYM, ya que mi local tendrá más demanda, porque no en todos los GYM venden suplementos y productos en el mismo recinto.

Dicho lo anterior comencé a buscar un local cerca de un gym y también que esté lo bastante cerca del metro y un centro comercial grande.

Santa Eulalia, L'Hospitalet de Llobregat, con unos 200 y dos plantas m2 a 60.000 €

![localización](fotos/localizaci%C3%B3n1.png)

![localización](fotos/localizacion2.png)


## 4. Topología de la red y Planos

Comenzaré haciendo un esquema de la red de nuestra empresa con packet tracer y proseguí haciendo nuestros planos.

- Principalmente tendremos tres redes:

    - Para los clientes, por si quieren conectarse a nuestro WIFI montamos un AccesPoint: 192.168.6.0/24
    - Para nuestro Servicio tecnico, “equipos y servidores entre otros”: 192.168.5.0/24
    - Para nuestros administradores y que encargan del papeleo y esas cosas: 192.168.4.0/24

![packettracer](fotos/packettracer.png)

- Configuraciones hechas para el AccesPoint

![packettracer](fotos/packettracer1.png)

![packettracer](fotos/packettracer2.png)

![packettracer](fotos/packettracer3.png)

![packettracer](fotos/packettracer4.png)

![packettracer](fotos/packettracer6.png)

- Planos de nuestro Local hechos con FloorPlaner:

- - Primero comenzamos creando el local "ActiveBoost":

![floorplaner](fotos/floorplaner.png)

Lo equipamos con muebles y le añadimos una receoción.

- - Para finalizar con los planos proseguimos cerando la oficina que dirige el local:

![floorplaner](fotos/floorplaner1.png)

Me inspire en la empresa donde hago las practicas, y posiblemente también copie algunos de sus servicios entre otros.

- - El cableado irá por las paredes, el router se encontrará en la sala de servidores/rack, esta repartira las IP a la sala Tecnica y oficina Tecnica con diferentes IP repartida por switches y tambié a la sala de vigilancia, reuniones, recepción y a los AccesPoint para el local ActiveBoost.

Resumen:

Servico tecnico, rack de servidores, sala vigilancia -> 192.168.5.0/24
Oficina Tecnica, recepción -> 192.168.4.0/24
Para los AccesPoint, uno alado de recepción y el otro a la entrada al local --> 192.168.6.0/24 




## 5. Instalar Proxmox en una MV

Primero pillamos una iso de la página oficial´de proxmox https://enterprise.proxmox.com/iso/ 
Proseguimos por arrancar la iso en Virtualbox y seguimos con las configuraciones.

![proxmox](fotos/proxmox.png)

Nos instalamos un CT, en mi caso Ubuntu

![proxmox](fotos/proxmox1.png)




