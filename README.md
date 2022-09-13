# Flow5
Temperatura por MQTT  y API desde OpenWeather

Se crea un flow que grafica mediante un dashboard los datos de temperatura y humedad utilizando OpenWEather

Material Necesario

-Ubuntu 20.04 NodeJS NPM NodeRed Nodos Dashboard -MQTT (Mosquito)
-Registrase en OpenWeather
-Optener un Key de openWEather  para realizar el enlace

Instrucciones y requisitos previos (Previamente instalados)

Para que el flow arranque , se deben instalar los siguientes requisitos:

Instalación de NodeJS. Se recomienda tener instalado NodeJS en alguna versión LTS. Al momento de creación de este documento, se usó la versión 16.17.0LTS. Esta instalación debe incluir las Build-Tools para hacer uso de NPM Instalación de NodeRed. La instalación se realiza por NPM. Al momento de la creación de este contenido, se usó la versión 3.0.2

-sudo apt install curl curl -curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - sudo apt-get install -y nodejs sudo apt-get install -y bulid -esential sudo npm install -g -unsite-perm node-red node red --version Instrucciones de preparación del entorno

Introduccion

Se crea un flow en notered que es capaz de  obtener los datos de temperatura y clima medante un portal web OpenWeather de donde se obtiene los datos climatologicos que posterioermente pondran ser graficados en un dashboard de nuestra computadora mediante un notered. 
Posterior a ello se conecta a un broquer publico para mostrar los datos de todos los participantes.

Ubuntu 20.04 NodeJS NPM NodeRed Nodos Dashboard

Instrucciones y requisitos previos (Previamente instalados)

Para que el flow arranque , se deben instalar los siguientes requisitos:

Instalación de NodeJS. Se recomienda tener instalado NodeJS en alguna versión LTS. Al momento de creación de este documento, se usó la versión 16.17.0LTS. Esta instalación debe incluir las Build-Tools para hacer uso de NPM Instalación de NodeRed. La instalación se realiza por NPM. Al momento de la creación de este contenido, se usó la versión 3.0.2

-sudo apt install curl curl -curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - sudo apt-get install -y nodejs sudo apt-get install -y bulid -esential sudo npm install -g -unsite-perm node-red node red --version

Instrucciones de preparación del entorno Para ejecutar este flow, es necesario lo siguiente crear los siguientes nodos en node-red :
![image](https://user-images.githubusercontent.com/111370930/188949328-99268f8f-b621-46c4-ac40-bf654c7a9ed8.png)
Los primeros 2 son clonados del repositorio del Flow4, mientras que los siguientes son agregados manualmente:
se debe agregar dentro de los modulos de funcion las siguientes intrsucciones:
![image](https://user-images.githubusercontent.com/111370930/188949817-a102524f-50ef-4cf5-a96d-b547676f4fa8.png)

Una vez registrados en la pagina OPenWeahter y obteniendo un KEY o llave para tener acceso a los datos de clima, se debe determinar la ubicacion de nuestra ciudad, mediante googlemaps:
![image](https://user-images.githubusercontent.com/111370930/188950678-c96dd684-727e-4307-8701-0d7b32f5167b.png)

y procedemos hacer las configuraciones de los nodos:
![image](https://user-images.githubusercontent.com/111370930/188951196-9ce27e3e-6228-41d6-acf9-1aff23b52c58.png)

Se configuran los modulos de funtion para los nodos:
Temperatura API:

msg.topic=msg.payload.id;
msg.payload=msg.payload.temp;
return msg;

Humedad API:

msg.topic=msg.payload.id;
msg.payload=msg.payload.hum;
return msg;

Por ultimo se configuran los layoouts para agrupar en 2 diferentes dahsboard losdatos uno por MQTT y otro por API, obteniendo los datos directamente de OpenWEather.

Y se procede hacer deploy,

Instrucciones de operación

Para poder visualizar los resultados es necesario abrir una terminal de mosquito y ejecutar los commandos para mandar la informacion a un JSON mediante el puerto local, local host para el caso de MQTT y para el caso de API los datos son automatizados.


Resultados

Se muestran los resultados del flujo de datos de la API por OpenWether:

Para el caso del API local.
![image](https://user-images.githubusercontent.com/111370930/188952350-aed4c3ec-1dcd-41ca-a215-0b72139892d1.png)

Para el caso de un broker publico:

![image](https://user-images.githubusercontent.com/111370930/188952871-c45f01ad-94ac-44ad-a626-79a64e3f7018.png)


Podemos observar que para varios resultados la grafica historico toma significancia, pues se van ordenando los nuevos resultados a los resultados anteriormente obtenidos asi como los resultados individuales y los resultados mediante un broker.

Evidencias

Repositorio github: https://github.com/Gustavo-MA/Flow5/blob/main/README.md

Créditos

Desarrollado por Gustavo Medina e-mail: gustavo.medina@uaem.edu.mx
