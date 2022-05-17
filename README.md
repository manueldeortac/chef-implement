# CHEF

![logo Chef](assets/img/Chef-logo1.png)

## ¿Qué es?

Es una herramienta de gestión de la configuración de código abierto que puede utilizar para crear partes de una infraestructura como un servicio (IaaS), que automatiza el proceso de entrega de aplicaciones. Chef es una plataforma de automatización simple y poderosa que transforma la infraestructura en código. Puede utilizar scripts Chef para suministrar una instalación de IBM® Integration Bus.

Los scripts Chef, que se denominan recetas, están formados por definiciones reutilizables que están escritas en el lenguaje de programación Ruby para escribir configuraciones del sistema. Las recetas Chef que realizan funciones relacionadas se agrupan en un único contenedor, denominado un recetario. Los recetarios y las recetas automatizan tareas de infraestructura comunes. Las definiciones de recetas describen de qué consiste su infraestructura y cómo cada parte de su infraestructura se despliega, configura y gestiona. Chef aplica estas definiciones para servidores, para producir una infraestructura automatizada.

Chef puede administrar múltiples servidores a la vez. Chef puede integrarse con otras herramientas de DevOps como Circle CI/CD, Jenkins, etc. Chef funciona en la capa de configuración y está automatizado por secuencias de comandos.

En Chef, los nodos se actualizan dinámicamente con las configuraciones en el servidor. Se llama Configuración de extracción lo que significa que no necesitamos ejecutar ni un solo comando en el servidor Chef para impulsar la configuración en los nodos, los nodos se actualizarán automáticamente con las configuraciones presentes en el servidor.

## Características de Chef

- Chef es compatible con múltiples plataformas como AIX, RHEL / CentOS, FreeBSD, OS X, Solaris, Microsoft Windows y Ubuntu. Las plataformas de cliente adicionales incluyen Arch Linux, Debian y Fedora.
- Chef puede integrarse con plataformas basadas en la nube como Internap, Amazon EC2, Google Cloud Platform, OpenStack, SoftLayer, Microsoft Azure y Rackspace para aprovisionar y configurar automáticamente nuevas máquinas.
- Debido a la madurez y flexibilidad de Chef, está siendo utilizado por gigantes como Mozilla, Expedia, Facebook, HP Public Cloud, Prezi, Xero, [Ancestry.com](https://ancestry.com/), Rackspace, Get Satisfaction, IGN, Marshall University, Socrata, University of Minnesota, Wharton School de la Universidad de Pennsylvania, Bonobos, Splunk, Citi, DueDil, Disney y Cheezburger

## Implementación:

En la fase de implementación se puede desarrollar 3 puntos que son importantes:

- _ **Puesto de Trabajo:** _

![Image 1](assets/img/image1.jpg)

La estación de trabajo es la ubicación desde la que se realizan todas las configuraciones de Chef.gestionado. Esta máquina contiene todos los datos de configuración que luego se pueden enviar al servidor Chef central. Estas configuraciones se prueban en la estación de trabajo antes de insertarlas en Chef Server. Una estación de trabajo consta de una herramienta de línea de comandos llamada Cuchillo, que se utiliza para interactuar con Chef Server. Puede haber varias estaciones de trabajo que administran juntas el servidor Chef central.

- _ **Servidor:** _

Actúa como un centro para los datos de configuración. Chef Server almacena los libros de recetas, las políticas que se aplican a los nodos y los metadatos que describen cada nodo registrado que está siendo administrado por Chef-Client.

Los nodos usan Chef-Client para pedirle al Chef Server detalles de configuración, como recetas, plantillas y distribuciones de archivos. El Chef-Client luego hace la mayor parte del trabajo de configuración posible en los propios Nodos (y no en el Chef Server).

![Image 2](assets/img/image2.jpg)


- _ **Nodos:** _

Los nodos pueden ser un servidor virtual basado en la nube o un servidor físico en su propio centro de datos, que se administra mediante el servidor Chef central. El componente principal que debe estar presente en el nodo es un agente que establecerá la comunicación con el servidor Chef central. Esto se llama Chef Client.

**Ventajas**

- Puede automatizar toda una infraestructura con Chef. Todas las tareas que se realizaban manualmente ahora se pueden realizar a través de la herramienta Chef.
- Puede configurar miles de nodos en minutos con Chef.
- La automatización de Chef funciona con la mayoría de las ofertas de nube pública como .
- Chef no solo automatizará las cosas, sino que también mantendrá los sistemas bajo un control constante y confirmará que el sistema está configurado de hecho de la manera que se requiere (Chef Agent / Client hace este trabajo). Si alguien comete un error al modificar un archivo, Chef lo corregirá.
- Se puede registrar una infraestructura completa en forma de un repositorio de Chef, que se puede utilizar como modelo para recrear la infraestructura desde cero.

## Desventajas del Chef

- Una de las grandes desventajas de Chef es la forma en que se controlan los libros de cocina. Necesita cuidados constantes para que las personas que están trabajando no se equivoquen con los libros de cocina de otros.
- No es muy fácil de aprender si la persona no está familiarizada con Ruby.
- Aún falta buena documentación.

## Paso a Paso:

- **Paso 1:** Instale Chef DK (kit de desarrollo) en su estación de trabajo Chef.

Chef DK es un paquete que contiene todas las herramientas de desarrollo que necesitará al programar Chef. Aquí está el enlace para descargar Chef DK .

Aquí, elija el sistema operativo que está utilizando. Estoy usando CentOS 6.8. Entonces, haré clic en Red Hat Enterprise Linux .

Copie el enlace según la versión de CentOS que esté utilizando. Estoy usando CentOS 6, como puede ver, lo he resaltado en la captura de pantalla anterior.

Vaya a la terminal de su estación de trabajo y descargue Chef DK usando el comando wget y pegue el enlace.

_ **Ejecuta esto:** _

`wget https://packages.chef.io/stable/el/6/chefdk-1.0.3-1.el6.x86\_64.rpm
`
El paquete ahora está descargado. Es hora de instalar este paquete usando rpm.

_ **Ejecuta esto:** _

`rpm -ivh chefdk-1.0.3-1.el6.x86\_64.rpm
`
Chef DK ahora está instalado en mi estación de trabajo.

- **Paso 2** : Cree una receta en la estación de trabajo

Comencemos por crear una receta en la estación de trabajo y probarla localmente para asegurarnos de que está funcionando.Cree una carpeta llamada chef-repo. Podemos crear nuestras Recetas dentro de esta carpeta.

_ **Ejecuta esto:** _

`mkdir chef-repo cd chef-repo
`
En este directorio chef-repo, crearé una receta llamada edureka.rb. .rb es la extensión utilizada para ruby. Usaré el editor vim, puedes usar cualquier otro editor que quieras como gedit, emac, vi, etc.

_ **Ejecuta esto:** _

vim edureka.rb

_ **Aquí agregue lo siguiente:** _

`archivo &#39;/ etc / motd&#39; contenido &#39;Bienvenido a Chef&#39; final
`
Esta rreceta es dureka .rb crea un archivo llamado / etc / motd con el contenido &#39;Bienvenido a Chef&#39;.

C ++ Stl Sort

Ahora usaré esta receta para verificar si está funcionando.

_ **Ejecutar esta:** _

`chef-aplicar edureka.rb
`
Entonces, hay un archivo creado en el repositorio de chef que tiene contenido Bienvenido a Chef.

- **Paso 3:** METRO modificar el archivo de receta para instalar el paquete httpd

Modificaré la receta para instalar el paquete httpd en mi estación de trabajo y copiaré un archivo index.html en la raíz del documento predeterminado para confirmar la instalación. La acción predeterminada para un recurso de paquete es la instalación, por lo tanto, no necesito especificar esa acción por separado.

_ **Ejecutar esta:** _

``vim edureka.rb``

_ **Aquí agregue lo siguiente:** _

paquete &#39;httpd&#39; servicio &#39;httpd&#39; hacer acción [: habilitar,: inicio] finalizar archivo &#39;/var/www/html/index.html&#39; hacer contenido &#39;Bienvenido a Apache en Chef&#39; final

Ahora aplicaré estas configuraciones ejecutando el siguiente comando:

_ **Ejecutar esta:** _

``chef-aplicar edureka.rb
``
La ejecución del comando describe claramente cada instancia en la receta. Instala el paquete Apache, habilita e inicia el servicio httpd en la estación de trabajo. Y crea un archivo index.html en la raíz del documento predeterminado con el contenido &#39;Bienvenido a Apache en Chef&#39;.

Ahora confirme la instalación de Apache2 abriendo su navegador web. Escriba su dirección IP pública o el nombre de su anfitrión. En mi caso, es localhost.

- **Etapa 4:** Ahora crearemos nuestro primer libro de cocina.

Cree un directorio llamado libros de recetas y ejecute el siguiente comando para generar el libro de recetas.

_ **Ejecutar esta:** _

Libros de cocina mkdir cd libros de cocina chef generar libro de cocina httpd\_deploy

httpd\_deploy es un nombre que se le da al libro de cocina. Puede dar el nombre que desee.

Pasemos a este nuevo directorio httpd\_deploy.

_ **Ejecutar esta:** _

`cd httpd\_deploy
`

Ahora veamos la estructura de archivos del libro de recetas creado.

_ **Ejecutar esta:** _

árbol

- **Paso 5** : Crear un archivo de plantilla.

Anteriormente, creé un archivo con algunos contenidos, pero que no encaja con las estructuras de mis recetas y libros de recetas. Así que veamos cómo podemos crear una plantilla para la página index.html.

_ **Ejecutar esta:** _

chef generar plantilla httpd\_deploy index.html

Ahora, si ve la estructura de archivos de mi libro de recetas, hay una carpeta creada con las plantillas de nombre con el archivo index.html.erb. Editaré este archivo de plantilla index.html.erb y le agregaré mi Receta. Consulte el siguiente ejemplo:

Ir al directorio predeterminado

_ **Ejecutar esta:** _

`cd / root / chef-repo / cookbook / httpd\_deploy / templates / default
`
Aquí, edite la plantilla index.html.erb usando cualquier editor con el que se sienta cómodo. Usaré el editor vim.

_ **Ejecutar esta:** _

`vim index.html.erb
`
Ahora agregue lo siguiente:

Bienvenido a Chef Apache Deployment

- **Paso 6:** CCrea una receta con esta plantilla.

Vaya al directorio de recetas.

_ **Ejecutar esta:** _

`cd / root / chef-repo / cookbooks / httpd\_deploy / recipes
`
Ahora edite el archivo default.rb usando cualquier editor que desee. Usaré el editor vim.

_ **Ejecutar esta:** _

`vim default.rb`

Aquí agregue lo siguiente:

paquete &#39;httpd&#39; servicio &#39;httpd&#39; hacer acción [: habilitar,: inicio] finalizar plantilla &#39;/var/www/html/index.html&#39; hacer fuente &#39;index.html.erb&#39; final

Ahora volveré a mi carpeta chef-repo y ejecutaré / probaré mi receta en mi estación de trabajo.

_ **Ejecutar esta:** _

`cd /root/chef-repo chef-client --local-mode --runlist &#39;receta [httpd\_deploy]&#39;`

De acuerdo con mi receta, Apache está instalado en mi estación de trabajo, el servicio se está iniciando y habilitando al arrancar. También se ha creado un archivo de plantilla en la raíz de mi documento predeterminado.

Ahora que he probado mi Workstation. Es hora de configurar Chef Server.

- **Paso 7:** Configurar Chef Server

Usaré la versión alojada de Chef Server en la nube, pero también puede usar una máquina física. Este Chef-Servidor está presente en manage.chef.io

Aquí cree una cuenta si no tiene una. Una vez que haya creado una cuenta, inicie sesión con sus credenciales de inicio de sesión.

Así es como se ve Chef Server.

Si se registra por primera vez, lo primero que hará es crear una organización. La organización es básicamente un grupo de máquinas que administrará con Chef Server.

Primero, iré a la pestaña de administración. Allí ya he creado una organización llamada edu. Entonces necesito descargar el kit de inicio en mi estación de trabajo. Este kit de inicio le ayudará a enviar archivos desde la estación de trabajo al servidor Chef. Haga clic en el icono de configuración en el lado derecho y haga clic en Starter Kit.

Al hacer clic allí, obtendrá una opción para descargar el Kit de inicio. Simplemente haga clic en él para descargar el archivo zip del Starter Kit.

Mueva este archivo a su directorio raíz.Ahora descomprima este archivo zip usando el comando descomprimir en su terminal. Notarás que incluye un directorio llamado chef-repo.

_ **Ejecutar esta:** _

`unzip chef-starter.zip`

Ahora mueva este kit de inicio al directorio de libros de cocina en el directorio chef-repo.

_ **Ejecutar esta:** _

`mv starter/root/chef-repo/cookbook`

Los libros de cocina del chef están disponibles en el Supermercado de libros de cocina, podemos ir al Supermercado del chef. Descargue los libros de cocina necesarios de supermarket.chef.io . Estoy descargando uno de los libros de cocina para instalar Apache desde allí.

_ **Ejecutar esta:** _

cd chef-repo cuchillo libro de cocina descarga del sitio learn\_chef\_httpd

Hay Tar ball descargado para Apache Cookbook. Ahora, necesitamos extraer el contenido de este archivo Tar descargado. Para eso, usaré el comando tar.

`tar -xvf learn\_chef\_httpd-0.2.0.tar.gz`

Todos los archivos necesarios se crean automáticamente en este Libro de recetas. No es necesario realizar modificaciones. Revisemos la descripción de la receta dentro de mi carpeta de recetas.

_ **Ejecutar esta:** _

`cd /root/chef-repo/ learn\_chef\_httpd/recipes cat default.rb`

Ahora, simplemente cargaré este libro de cocina en mi Chef Server, ya que me parece perfecto.

- **Paso 8:** Cargue el libro de recetas en Chef Server.

Para cargar el libro de cocina de Apache que he descargado, primero mueva este archivo learn\_chef\_httpd a la carpeta de libros de cocina en el repositorio de chef. Luego cambie su directorio a libros de cocina.

_ **Ejecutar esta:** _

`mv/root/chef-repo/learn\_chef\_httpd/root/chef-repo/cookbooks
`
Ahora vaya a este directorio de libros de cocina.

_ **Ejecutar esta:** _

libros de cocina en CD

Ahora en este directorio, ejecute el siguiente comando para cargar Apache Cookbooa:

Ejecutivo ute t h es:

cargar libro de cocina con cuchillo learn\_chef\_httpd

Verifique el libro de recetas desde la consola de administración del servidor Chef. En la sección de políticas, encontrará el libro de cocina que ha subido. Consulte la captura de pantalla a continuación:

Ahora nuestro último paso es agregar Chef Node. He configurado una estación de trabajo, un servidor Chef y ahora necesito agregar mis clientes al servidor Chef para la automatización.

- **Paso 9:** Añadiendo Chef Node al Chef Server.

Para fines de demostración, usaré una máquina CentOS como Chef Node. Puede haber cientos de nodos conectados a un servidor Chef. El color del terminal de mi máquina Node es diferente al de la Workstation, por lo que podrá diferenciar entre ambos.

Solo necesito la dirección IP de mi nodo para eso ejecutaré el siguiente comando en mi máquina de nodoes.

Ejecutivo tu t es t h es:

`ifconfig`

Agregaré mi nodo Chef al servidor ejecutando el comando Knife Bootstrap en el que especificaré la dirección IP del nodo Chef y su nombre. Ejecute el comando que se muestra a continuación.en:

Ejecutivo ute t h es:

Cómo Instalar Php En Windows 10

cuchillo bootstrap 192.168.56.102 --ssh-usuario root --ssh-contraseña edureka --nombre de nodo chefNode

Este comando también inicializará la instalación del Chef-Client en el Chef Node. Puede verificarlo desde la CLI en la estación de trabajo usando el comando cuchillo, como se muestra a continuación.en:

Ejecutivo ute t h es:

Lista de nodos de cuchillo

También puede verificar desde el servidor Chef. Vaya a la pestaña de nodos en su Consola de administración del servidor, aquí notará que el nodo que ha agregado está presente. Consulte la captura de pantalla a continuación.

- **Paso 10:** Administrar lista de ejecución de nodos

Veamos cómo podemos agregar un libro de cocina al nodo y administrar su lista de ejecución desde el servidor Chef. Como puede ver en la captura de pantalla a continuación, haga clic en la pestaña Acciones y seleccione la opción Editar lista de ejecución para administrar la lista de ejecución.

En Recetas disponibles, puede ver nuestra Receta learn\_chef\_httpd, puede arrastrarla desde los paquetes disponibles a la Lista de ejecución actual y guardar la lista de ejecución.

Ahora inicie sesión en su nodo y simplemente ejecute chef-client para ejecutar Run List.

Ejecutivo ute t h es:

cliente principal

Espero que hayas disfrutado de este tutorial de Chef y hayas aprendido cómo se puede utilizar Chef para configurar cientos de nodos. Chef juega un papel vital en muchas organizaciones para lograr DevOps. Con Chef, las organizaciones están lanzando aplicaciones con mayor frecuencia y confiabilidad.bvaso.

Si encontraste este blog en &#39; Chef Tutorial &#39;Relevante, revisar la por Edureka, una empresa de aprendizaje en línea de confianza con una red de más de 250.000 alumnos satisfechos repartidos por todo el mundo. El curso de formación de certificación de Edureka DevOps ayuda a los alumnos a adquirir experiencia en varios procesos y herramientas de DevOps, como Puppet, Chef, Jenkins, Nagios y GIT, para automatizar varios pasos en SDLC.
