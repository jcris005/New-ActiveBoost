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

Primero comenzamos creando el local "ActiveBoost":

![floorplaner](fotos/floorplaner.png)

Lo equipamos con muebles y le añadimos una receoción.

Para finalizar con los planos proseguimos cerando la oficina que dirige el local:

![floorplaner](fotos/floorplaner1.png)

Me inspire en la empresa donde hago las practicas, y posiblemente también copie algunos de sus servicios entre otros.

El cableado irá por las paredes, el router se encontrará en la sala de servidores/rack, esta repartira las IP a la sala Tecnica y oficina Tecnica con diferentes IP repartida por switches y tambié a la sala de vigilancia, reuniones, recepción y a los AccesPoint para el local ActiveBoost.

- Resumen:

    - Servico tecnico, rack de servidores, sala vigilancia -> 192.168.5.0/24

    - Oficina Tecnica, recepción -> 192.168.4.0/24

    - Para los AccesPoint, uno alado de recepción y el otro a la entrada al local --> 192.168.6.0/24 




## 5. Instalar Proxmox en una MV

Primero pillamos una iso de la página oficial´de proxmox https://enterprise.proxmox.com/iso/ 
Proseguimos por arrancar la iso en Virtualbox y seguimos con las configuraciones.

![proxmox](fotos/proxmox.png)

Nos instalamos un CT, en mi caso Ubuntu

![proxmox](fotos/proxmox1.png)

## 6. Instalación de servicios "solo necesarios para ActiveBoost" 

En el anterior proyecto yo me encargue de todas las que se tenian que hacer, yo me encrague de hacer desde la primera a la ultima, exepto algunas que no salkieron, pero ahora decidi que solo pondria las necesarias y algunas que que no estaban en la instalación del anterior proyecto.

- Me vase en 6 puntos:

    - Mensageria instantanea que lo haré con matermost
    - Software de gestión empresarial, SAP Business One, esta herramienta es muy útil ya que es una solución unica y asequible para gestionar toda pequeña empresa desde contabilidad y finanzas, compras, inventario, ventas y relaciones con los clientes hasta informes y análisis.
    - Seguridad fisica y lógica, para la segurida física creare las medidas de seguridad e instalare un servidor en el cual pueda acceder a las camaras de seguridad 
    ZoneMinder que es la que tenemos montada en el canodrom, tambie necesitariamos targetas de acceso, es decir "CardPass3" su función es limitar el paso a cualquier persona que no tenga esta targeta. Para la seguridad logica bastaria con un wirewall de red en nuestro router que será creado pon PfSense.
    - Servicio de copias de seguridad y almacenamiento, nosotros tenemos montado una "raid 5" y aparte tambien tenemos instalado el "proxmox backup" que remplace esta opción enves del TrueNas. Cabe destacra que también tenemos las backups en la nube.
    - Servicios de logisticca, Manhattan Associates nos facilitará muchisimo la administración del almacén , tambien estube pensando en instalar un nexcloud para el 
    servivio tecnico y otro para la oficina tecnica.
    - Tambien haremos uso de apache2 para la web.

Psiblemente no acabe de instalar todos estos servicios ya que no dispongo del tiempo y conocimiento y material necesario, pero llegare hasta donde se pueda, le dare más inportancia a los mas necesarios para el funcionamiento de la empresa ActiveBoost.

Cabe destacar que aqui no haré la cnfiguración de DNS y DHCP porque ya las hice en el anterior proyecto, y daremos por hecho que ya están instalados. También, los servicios desconocidos mencionados antes me recomendo Alfons("Tutor de précticas") que se encraga de todo el canodrom, le pregunte estas cosas para que mi empresa tenga más sentido, que creo que era eso lo que fallaba en el anterior proyecto.

### 6.1 Instalación y configuración de servidor Mattermost:

- Comenzamos con buscar si se puede instalar con docker-compose para facilitarnos el trabajo, si se puede, el script para el containet de docker-compose.yml me lo proporciono chat-gpt, lo que se usa seria mb y matermost:

![mattermost](fotos/mattermost.png)

En la imagen se puede apresiar como ejecutamos el container docker-compose.yml que tiene el siguiente contenido:

![mattermost](fotos/mattermost1.png)

También qui podemos observar que no nos dio ninngun error y podemos ver los contenedores que fueron ejecutados:

![mattermost](fotos/mattermost3.png)

![mattermost](fotos/mattermos4.png)

- Ahora pasemos al servidor:

Ahora abrimos un navegador y ponemos la ip del server-ubuntu donde tenemos montado el matermost con el puerto :8065 y al entrar lo primero que nos pude es crear una cuenta administrador y despues una "Team" nueva, en nuestro caso ActiveBoost

![mattermost](fotos/mattermost5.png)

![mattermost](fotos/mattermost_admin.png)

Y aquí podemos ver que ya se creo:

![mattermost](fotos/mattermost_creado_ya_la_chanel_de_activeboost.png)

En la siguiente imagen se muestra algunos chanels que son los mas importantes, oficina tecnica: solo pa los que se encargan del papeleo y administración entre otros, servicio técnico: para el chat del los encragados del correcto funcionamiento de los servidores, impresoras, web... entre otros, town square: que es una chanel para que todos dentro del servidor lo vean, y por ultimo off-topic: que una chanel que no está relacionada con el trabajo.

cabe destacar que este es la beta, después con el tiempo lo mejoraremos todo.

![mattermost](fotos/mattermost6.png)

Otra cosa conveniente al usar mattermost es que tiene "boards" en cada chanel, para asignar tareas con una fecha, importancia entre otros, y admeás también puedes hacer llamadas, la mensageria instantanea ideal para una empresa.

![mattermost](fotos/mattermost7.png)

![mattermost](fotos/mattermost8boards.png)

Estos solo son algunas cosas de las cuales haremos uso, pero mattermost ofece mucho más.

### 6.2 Instalación y configuración Nexcloud, para servicio técnico y oficina técnica

En este apartado lo que haremos será crear otro container y subirlo con docker compose, como hicimos con matermost.

![nexcloud](fotos/nexcloud1.png)

La siguiente imagen mustra el contenido de docker-compose.yml 

![nexcloud](fotos/nexcloud2.png)

Lo que hace es usar la imagen de mariadb como base de datos y nexclaud que indica el puerto y el archivo donde se alojara.

Una vez que veamos que no hay ningun error solo tenemos que poner nuestra ip del server y el puerto 8080, este es el que usamos para nexcloud.

En las siguientes imágenes podemos ver que primero nos logueamos con la cuenta del server y la contraceña creada en mariadb y después ya podemos acceder al nexcloud.

![nexcloud](fotos/nexcloud3.png)

![nexcloud](fotos/nexcloud4.png)

Una vez terminado esto lo que haremos será crear grupos, oficina tecnica, servicio técnico, sala de vídeo vigilancia entre otros. Tambien creamos carpetas para estos. Y por ultimo añadimos usuarios yo añadi al usuario "jhoselin" y le asigne al grupo servicio técnico, y le comparti es acceso a la carpeta servicio técnico al grupo de servicio técnico, es decir al grupo en el que se encuentra el usuario "jhoselin". Accedí desde otro orenador, me loguee con la cuenta, y me salía la la carpeta de servicio técnico y las subcarpetas creadas.

![nexcloud](fotos/nexcloud5.png)

Aqui las imagenes del otro ordenador:

![nexcloud](fotos/nexcloud6.png)

![nexcloud](fotos/nexcloud7.png)

![nexcloud](fotos/nexcloud8.png)

![nexcloud](fotos/nexcloud9.png)

![nexcloud](fotos/nexcloud10.png)

Al parecer no le comparti solo la carpeta de servicio técnico, sino de la carpeta "Documents" que es sonde puse todos los demás.

### 6.3. DNS

Yo decidi implementar un servidor DNS para la futura web que se llamara actu¡iveboost.com y necesitamos un servidor DNS para combertir la ip a nombre de dominio.

Configure nuestro servidor DNS con bind9: sudo apt-get install bind9 para descargar el paquete, proseguimos editando el sihuiente archivo /etc/bind/named.conf.local

![dns](fotos/dns.png)

Dentro del archivo agregamos las zonas de dominio a configurar "activeboost.com".

Proseguimos por crear el archivo /etc/bind/db.activeboost.com

![dns](fotos/dns1.png)

añadimos las siguientes lineas, estas configuraciones en el archivo de zona definen los registros de resolución de nombres para el dominio. Cada registro especifica una relación entre un nombre y una dirección IP, lo que permite que el servidor DNS resuelva las consultas de DNS y dirija el tráfico hacia el destino correcto.
Por ultimo receteamos el servicio de bind 9 con: sudo service bind9 restart.

![dns](fotos/dns2.png)



### 6.4 DHCP

Nosotros instalamos isc-dhcp-server, comenzamos descargando el paquete con apt-get install y procedimos con la edición del archivo /etc/dhcp/dhcpd.conf que nos sirvio para establecer el nombre de dominio.

![DHCP](fotos/DHCP.png)

Esta imagesn también es el mismo archivo de antes, sinó con la diferencia de que este se encrga de configurar el rango de direcciones IP que el servidor DHCP asignará a los clientes

![DHCP](fotos/DHCP1.png)

![DHCP](fotos/DHCP2.png)

Esto es un poco de lo que hice en el anterior proyecto y lo expliqué mejor ahí.

### 6.5 SAP Business One

No hay tiempo, pero tampoco es tán necesario ya que tenemos nexcloud, pero con esta herrramienta boosteariamos nuestra empresa.
Ya explique un poco de para que lo queria en el punto 6.

![businessOne](fotos/BusinessOne.png)

### 6.6 Seguridad

- ZoneMinder 

Este servidor practicante un servidor para monitorear camaras, seria más que todo para nuestra sala de videovigiláncia.

- CardPass3

Este servidor nos serviria para gestionar el acceso al recinto, en nuestro caso al local de ActiveBoost y a las oficinas, aparte de crear targetas de acceso para siertas salas, también gestiona a los departamentos a los que pertenecen los trabajadores. Esto tambien formaria parte de la sala de seguridad.

![targeta](fotos/tarjetaDeAcceso.jpg)

- Medidas de seguridad para el local y oficinas:

    - Sistema de vigilancia por video
    - Control de acceso
    - Alarma de seguridad
    - Seguridad física de los productos, (vitrinas, para proteger los productos)
    - Control de inventario
    - Políticas de seguridad de datos
    - Extintores de incendios
    - Detectores de incendios
    - Señalización de salidas de emergencia
    - Salida de emergencia
    - Capacitación en primeros auxilios

### 6.7 Proxmox Backup Server

Esta herramienta como su nombre lo dice, es un servidor proxmox que hace backups a un servidor proxmox, es muy fácil de configurar y puedes decidir cuando hara la backup, que CT o PVS hacer la backup, es una altrnativa al TrueNas, que me abria gustado hacer.

![Proxmox](fotos/proxmox_backup_server.png)

Mi idea era de tener montado una "RAID 5" en nuestro servidor proxmox, y que aparte se hagan las backups en proxmox server que estaria en otra máquina.

![Proxmox](fotos/rack-servidor.png)

![Proxmox](fotos/rack-servidor1.png)

Claro, aparte también tendríamos las backups en la nube , estuve pensando en "MANHATTAN ACTIVE" que es la que usan el corte ingles, Nissan, Kiani entre, otras grandes empresas.
Aparte tmbién nos serviria para gestionar mejor nuestro almacén entre otros...

### 6.8 Pagina Web

Par este partado, quería reutilizar la página web del anterior proyecto y modificarlo un poco, pero no dio tiempo, así que pense en porlomenos hacer el diceño de la página.

## 8. Configuración Pfsense y Firewall 

No me dio tiempo a instalar un PfSense y mi PC está apunto de explotar, pero seria lo mismo que en el anterior proyecto, añadir tres redes, crear una red wan que de salida a internet y tres redes lan para las sistintas redes que tenemos.

Por parte del Firewall de Red que lo queria configurar qui, seria Un firewall de red "denegativo", lo contrario a permisivo.

- Lista de IP de servidores y puertos, protocolos:

    - Servidor DNS: 192.168.1.53: UDP 53 y TCP 53
    - Servidor DHCP:192.168.1.53: UDP 67
    - Servidor Mattermost: 192.168.1.56: TCP 8065
    - Servidor Nexcloud: 192.168.1.57:  TCP 8080

Yo montaria un firewall de red restrictivo, es decir el más seguro, permitiria el paso a los servidores anteriormente mencionados y y obiamnete a http 80 y https 443, para poder navegar por internet y ssh 22, para poder conectarnos por ssh y poder acceder siempre a los servidores.

![PfSense](fotos/pfsense.jpg)

## 9 Lista de productos de venta y productos de oficina

Suplementos deportivos 

- Proteínas en polvo:

    - Proteína de suero de leche (whey protein)
    - Proteína de caseína
    - Proteína vegetal (soja, guisante, arroz, cáñamo)

- Pre-entrenamientos (Mezclas de pre-entrenamiento con ingredientes como cafeína, beta-alanina, creatina y aminoácidos para aumentar la energía y el rendimiento durante el entrenamiento)
- BCAA (Aminoácidos de Cadena Ramificada)--> Suplementos de aminoácidos esenciales que incluyen leucina, isoleucina y valina, que pueden ayudar a la recuperación muscular y el crecimiento)

- Glutamina (Un aminoácido que puede ayudar en la recuperación muscular y la salud del sistema inmunológico)

- Creatina (Suplemento popular que puede aumentar la fuerza y la resistencia muscular)

- Quemadores de grasa (Suplementos que contienen ingredientes como cafeína, extracto de té verde y otros estimulantes para ayudar en la pérdida de peso y el metabolismo de las grasas.
Vitaminas y minerales)

- Suplementos multivitamínicos y minerales diseñados específicamente para deportistas, que pueden ayudar a cubrir las necesidades nutricionales adicionales.

- Omega-3 (Ácidos grasos esenciales que promueven la salud cardiovascular y la función cerebral)

- Recuperadores post-entrenamiento (Mezclas de nutrientes que contienen proteínas, carbohidratos y aminoácidos para ayudar en la recuperación muscular después del ejercicio)

- Barras y snacks proteicos

Material Deportivo

- Straps o correas de levantamiento (Ayudan a mejorar el agarre durante ejercicios de levantamiento de peso, como levantamiento muerto o dominadas)

- Cinturones de levantamiento de peso (Proporcionan soporte para la columna vertebral y los músculos abdominales durante levantamientos pesados, como sentadillas o peso muerto)

- Rodilleras (Brindan soporte y estabilidad a las rodillas durante ejercicios que involucran movimientos de flexión y extensión de las rodillas, como sentadillas o levantamiento de peso)

- Muñequeras (Proporcionan estabilidad y soporte a las muñecas durante ejercicios que involucran movimientos de empuje o levantamiento de peso, como press de banca o levantamiento militar)

- Fajas de compresión (Ayudan a proporcionar compresión y soporte a los músculos durante el entrenamiento, reduciendo la fatiga muscular y promoviendo una mejor circulación sanguínea)

- Bandas de resistencia (Proporcionan resistencia adicional para ejercicios de fuerza y ​​acondicionamiento, ayudando a fortalecer y tonificar los músculos)

- Agarres para levantamiento de pesas (Mejoran el agarre durante ejercicios de levantamiento de peso, como levantamiento muerto o remo, ayudando a reducir la fatiga de los antebrazos)

- Rulos de espuma o foam rollers (Se utilizan para el automasaje y la liberación miofascial, ayudando a aliviar la tensión muscular y mejorar la movilidad)

- Balones medicinales (Son utilizados para ejercicios de resistencia y fortalecimiento, así como para mejorar el equilibrio y la coordinación)

- Bandas elásticas de estiramiento (Se utilizan para mejorar la flexibilidad, realizar estiramientos y ejercicios de movilidad)

Material de Oficina

- 8 Portatilres
- 2 Impresoras
- 3 PC de sobremesa
- 2 Rack de servidor pequeño
- 1 Rack para el router
- Cables Ethernet
- 10 Monitores
- 1 Proyector para la sala de reuniones
- 12 Camaras
- Lectores de targetas de acceso 
- Teclados y ratones

## 10. marketing

Primero,tenemos que pensar porque las personas que eligirían a nuestri local para dejar su dinero?

Puntos a favor ActiveBoost:

- Localización estratégica, ya que estámos cerca de un gym, en el cual no venden duplementos.
- Gran variedad de productos,
- Web en internet para la venta de productos.
- Calidad/precio

Puntos en contra?

- Creo que no hay

### 10.1. Analizar Competencia en el mercado

Porque MyProtein vende mucho más que otras tiendas, que incluso ya se volvió mundial, es decir que tiene tiendas por todo el mundo?

Haciendo una brebe busqueda, te das cuenta de que myprotein no vende sus productos a bajo precio, mantiene una media, no tiene tanta variedad de productos e incluso su página web no es llamativa. Entonces porque vende mucho más que otras empresas? 

- Porque dan a conocer su tienda por redes sociales y pagan a influencers fitnes para promocionar su tienda, cosa que pocas tiendas hacen y se limitan a vender en un local y abrir una página web para vender más.

Entonces para triunfar en el mercado de venta de suplementación tenemos que comenzar ahacer conocer nustra marca ActiveBoost-













