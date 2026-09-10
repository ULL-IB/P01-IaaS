# Práctica 01. El Entorno de trabajo IaaS para la asignatura

# Factor de ponderación: 3

### Objetivos

Los objetivos de esta práctica son:

* Realizar algunas tareas administrativas previas para facilitar el trabajo en la asignatura 
* Conocer y configurar el entorno de trabajo de la asignatura en el sistema Linux del IaaS 
* Ser capaz de usar comandos de la shell de GNU/Linux para trabajar en la Máquina Virtual (VM) de la asignatura
* Editar, compilar y ejecutar `hello_world.cc` 

### Rúbrica de evaluacion del ejercicio
Se señalan a continuación los aspectos más relevantes (la lista no es exhaustiva)
que se tendrán en cuenta a la hora de evaluar esta práctica:
* Se valorará positivamente que el alumnado haya realizado de forma efectiva las tareas propuestas con anterioridad a la sesión de prácticas

Con anterioridad a la sesión de prácticas, debe Ud. estudiar los documentos que se enlazan desde
éste, así como realizar todas las tareas posibles de las que en este documento se proponen.

### Tareas previas
#### GNU/Linux en su ordenador de trabajo
1. Para el trabajo en las prácticas de la asignatura se utilizará intensivamente el Sistema Operativo Linux,
trabajando fundamentalmente en una [máquina virtual](https://es.wikipedia.org/wiki/M%C3%A1quina_virtual) disponible a través de la infraestructura 
[IaaS](https://es.wikipedia.org/wiki/Infraestructura_como_servicio_(IaaS)) de la ULL.
Es por ello que resulta muy conveniente que el alumnado tenga instalado Linux en un ordenador personal con el que
trabaje desde su casa. 

Se optará preferentemente por la distribución Ubuntu para que sea la misma que tiene la máquina virtual de la asignatura.  
Hay al menos tres opciones para ello, que son las siguientes en orden de mayor a menor idoneidad para el trabajo en la asignatura:

  * Si dispone Ud. de un ordenador propio, puede instalar Ubuntu directamente en él, bien [reemplazando el sistema operativo actual](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) (y por tanto eliminando todos los datos del equipo), bien [creando una partición para conservarlo](https://www.youtube.com/watch?v=5Yre3OnMUws). 
  Para esta instalación necesitará Ud. crear un pendrive desde el que pueda arrancar el ordenador, siguiendo para ello (por ejemplo) 
  [estas otras instrucciones](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview).

  * Instalar Ubuntu como un sistema "invitado" dentro de Windows, usando para ello un software de virtualización como VirtualBox. [Este tutorial](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox) contiene las instrucciones a seguir para instalar Ubuntu como sistema invitado en Windows.
  
  * Utilizar WSL, [Windows subsystem for Linux](https://docs.microsoft.com/es-es/windows/wsl/install-win10).
  WSL es una característica introducida en Windows 10 que permite instalar un núcleo Linux directamente sobre el sistema operativo de Microsoft.

Las tres opciones anteriores están ordenadas atendiendo a la que consideramos idoneidad de cada una, siendo la primera la más idónea, pero este orden posiblemente coincide con el orden inverso de complejidad de la instalación: la primera es posiblemente más compleja que la tercera. 
Tenga esto en cuenta a la hora de decidirse por cualquiera de estas opciones.

Una opción alternativa que se considera menos adecuada consiste en no instalar un sistema Linux sino acceder 
a la máquina virtual IaaS de la asignatura desde Windows usando para ello un cliente *ssh*. 
Se recomienda para este caso utilizar el que viene instalado con Windows 10 y posteriores, a través de la aplicación *Símbolo del Sistema*.  

En todo caso, recuerde que si desea acceder a las máquinas de la Universidad desde fuera del campus universitario necesitará Ud. configurar una conexión usando [VPN](https://es.wikipedia.org/wiki/Red_privada_virtual).
Para configurar la conexión VPN siga las instrucciones de la página [Servicio de VPN de la ULL](https://www.ull.es/servicios/stic/2026/07/08/servicio-de-vpn-de-la-ull/).  
[Este vídeo](https://www.youtube.com/watch?v=jHUfeN_NMYE) muestra cómo conectar desde linux usando ssh con una máquina virtual del IaaS.

#### Dirección de correo alternativa
2. Acceda al [portal de gestión de usuarios](https://usuarios.ull.es/autogestion/cambio_alias/)
del Servicio TIC de la ULL y configure allí una dirección de correo electrónico alternativa a su dirección
`aluXXXX@ull.edu.es`.
Las direcciones (alias) alternativas que el sistema le ofrece han de incluir necesariamente dos dígitos
numéricos (sin significado específico alguno) y permiten que su dirección de correo sea más legible y fácil de
recordar, sobre todo para otras personas.
Podrá utilizar indistintamente las direcciones `aluXXXX@ull.edu.es` y el alias que configure.

#### GitHub
3. [GitHub](https://github.com/) es una plataforma de desarrollo colaborativo para alojar proyectos utilizando el sistema de control de versiones Git. Cree una cuenta en [GitHub](https://github.com/) y configure su perfil de usuario para que la cuenta de correo electrónico asociada sea su dirección institucional o su alias. También es recomendable incluir una imagen (fotografía) en la que se le reconozca y usar su nombre real, puesto que sus repositorios de código en GitHub pasarán a formar parte de su curriculum profesional.

#### El editor Vim
4. Para editar ficheros en las prácticas de la asignatura se utilizará el editor [vim](https://www.vim.org/) (*vim* es *vi - iMproved*) .
Estudie detenidamente los primeros pasos de [este tutorial](https://blog.desdelinux.net/usando-vim-tutorial-basico/) para que
aprenda lo básico sobre cómo editar y modificar un fichero usando vi.
Con el estudio de este otro [tutorial interactivo on-line](https://www.openvim.com/) debe aprender lo mínimo que necesita
para comenzar a utilizar vi.
Se trata de un editor muy potente pero al principio puede resultar difícil iniciarse en su uso. 
Para que estudie y practique vim dispone de muchos tutoriales en la web. 
[Este tutorial](https://github.com/Izaird/Vim-primeros-pasos) explica lo básico del editor a través de ejemplos concretos con ficheros de texto.

Para editar algunas líneas concretas de un fichero de texto usando vi siga estas indicaciones:
* Use las teclas con flechas arriba/abajo para mover el cursor a la línea que desee editar.
* Antes de modificar el texto ha de presionar `i` para acceder al modo de inserción de vim.
* Cuando acabe de modificar el texto, pulse ESC (para salir del modo de inserción)
* Ahora escriba `:wq!` y presione ENTER para guardar los cambios en disco. W es para escribir (Write), Q para salir (Quit) y ! se usa para forzar la escritura.

#### El entorno de trabajo en el Centro de Cálculo (CC) de la ESIT
Puesto que la evaluación de las prácticas se va a realizar en los ordenadores del CC, resulta
necesario que previo a la sesión de evaluación de la práctica visite Ud. el CC, inicie sesión
en Linux en alguno de los ordenadores de la sala y se familiarice con ese entorno de trabajo.
No espere al día de evaluación de su práctica para realizar estas tareas.

El documento 
[Guía para configuración de entornos de escritorio del Centro de
Cálculo](https://docs.google.com/document/d/1ciTxGwuoJTBQJRB972iAOxt_kHg9pT_HmwrGa4-0aQA/edit?usp=sharing)
que puede Ud. hallar en el Aula Virtual contiene instrucciones para configurar el entorno de trabajo 
de modo que su configuración se mantenga cada vez que visite una sala del CC.

5. Estudie ese documento y utilícelo como guía para configurar su cuenta de usuario en esa instalación.
Si tiene Ud. alguna duda, consulte con el personal del CC.


### El Entorno ULL-IaaS
6. Inicie sesión en Linux en alguno de los PCs de una sala del Centro de Cálculo o bien desde otro ordenador usando VPN si lo hace desde fuera de la Universidad.
En este documento se denominará máquina remota a la máquina virtual (VM) del [IaaS-ULL](https://www.ull.es/servicios/stic/2015/10/27/nuevo-servicio-iaas/) 
y máquina local al PC en el que está Ud. trabajando.

7. Acceda a la [interfaz web](https://iaas.ull.es) 
de la plataforma IaaS-ULL (recuerde tener iniciada una conexión VPN si trabaja desde fuera del campus universitario) y autentifíquese en esa interfaz con sus credenciales (username + password) de la cuenta institucional. Si no tiene acceso a la plataforma, identifíquese primero en el [sistema de autenticación de la ULL](https://valida.ull.es/) y vuelva a intentarlo. 

![login](ovirt-login.png)

Tenga en cuenta que la 
[interfaz web de las máquinas IaaS](https://iaas.ull.es)
no soporta muchas conexiones concurrentes de modo que es conveniente que se conecte Ud. cuanto antes para no
coincidir con otros estudiantes en esa conexión.

A continuación encontrará un listado con todas las máquinas virtuales que tiene disponibles, entre las que debería aparecer la de esta asignatura. Si es la primera vez que accede, pulse "Tomar una máquina virtual" y, en unos minutos, su máquina estará lista para usarse. La siguiente vez que acceda, la máquina estará ya accesible. Si la máquina está apagada, pulse el botón "Ejecutar". El proceso de arranque de la máquina puede durar unos minutos.

![solicitar](ovirt-vm.png)

Una vez que la máquina haya arrancado, haga click sobre su imagen para acceder a su información. Tome nota de la Dirección IP de la máquina, que se muestra en el apartado "Detalles" de la máquina. La [dirección IP](https://en.wikipedia.org/wiki/IP_address) es una secuencia de números (de la forma `10.6.131.106`) que identifican de forma unívoca a cualquier dispositivo conectado a Internet.

![ip](ovirt-ip.png)

Esta dirección será necesaria para establecer conexiones directas a la máquina a través de ssh desde su casa o desde las salas del Centro de Cálculo de la ESIT. 
Anote esa dirección IP puesto que la máquina conserva esa dirección IP de forma estable. 
Si en algún momento **experimenta dificultades de conexión**, conecte a través de la interfaz web y compruebe que
la dirección de la máquina no ha cambiado.

Observe que en la página en la que se encuentra también hay un botón de "Reiniciar" (que usaremos más adelante) y uno de "Apagar". **Nunca pulse el botón de Apagar ni ejecute la orden `halt` desde su máquina virtual,** ya que las máquinas virtuales de este servicio no tienen estado interno y apagarlas de esta manera eliminaría permanentemente todo su contenido, incluyendo su sistema operativo.

8. Abra una conexión ssh con su máquina usando la dirección IP que ha obtenido en el paso anterior.
Si esa conexión la realiza desde Linux el comando que ha de usar para establecerla es el siguiente, cambiando la dirección IP por la de su máquina:
```
$ ssh usuario@10.6.131.106
```
En cuanto se conecte a la máquina remota, el sistema le pedirá sus credenciales.
Recuerde que inicialmente esas credenciales de acceso son: Username: `usuario` y password: `usuario`.

La primera vez que se conecte puede que se le muestre un mensaje similar al siguiente, para preguntarle si confía Ud. en esta IP.
```
The authenticity of host '10.6.128.999 (10.6.128.999)' can't be established.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
Responda `yes` para continuar con la conexión.

En este primer acceso el sistema le solicitará que introduzca la contraseña actual y que escriba dos veces la nueva contraseña elegida.
**Preste mucha atención a este paso** porque si comete un error, puede ser irreparable y su máquina resultará inaccesible.
No se preocupe por ahora por la contraseña que elija puesto que siempre la puede cambiar en el futuro 
pero **anote** el password que elija para no perderlo u olvidarlo.
La recomendación es que elija ahora un password simple (algo como `minombresintildes` o similar).
Ya en el futuro podrá cambiarlo por otro más robusto.

Compruebe a continuación el sistema operativo y versión del mismo:
```
$ lsb_release -a
```

9. Actualice el software (paquetes) de la máquina siguiendo las indicaciones de [esta página](https://linuxconfig.org/how-to-update-ubuntu-packages-on-18-04-bionic-beaver-linux) (por ejemplo).
Los comandos que tendrá que utilizar son:
```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt autoremove
```
[Esta imagen](https://raw.githubusercontent.com/fsande/IB-P01-EntornoIaaS/3b0223eef4fff02835108ac59ea8d2f2f26c43cc/img/update.png)
muestra un posible resultado de la ejecución del primero de estos comandos y 
[esta otra](https://raw.githubusercontent.com/fsande/IB-P01-EntornoIaaS/3b0223eef4fff02835108ac59ea8d2f2f26c43cc/img/upgrade2.png)
del segundo de ellos.    
Si el sistema le pregunta si desea instalar `grub`, responda que no.

Los comandos que se ejecutan con `sudo` se están ejecutando como "superusuario" de modo que **nunca** ejecute comandos con `sudo` salvo 
que sepa muy bien lo que está haciendo o se le indique (como en este caso) cómo usarlo.

10. Para consultar la IP de una máquina en un terminal Linux utilice el comando:
```
$ ifconfig -a
```
Si recibe el mensaje de que `ifconfig` no está instalado, se le indicará qué comando ejecutar para instalarlo. Ejecútelo y pruebe el comando de nuevo. Observe que la IP mostrada es la misma que se le indicó en la interfaz web del IaaS.

11. Edite los ficheros necesarios para [cambiar el nombre lógico de la máquina](https://askubuntu.com/questions/9540/how-do-i-change-the-computer-name) que le ha sido asignada. 
Se propone utilizar como nombre algo como Ubuntu-18-ASIG-XXX (cambiando "ASIG" por el acrónimo de la asignatura y 
"XXX" por lo que Ud. quiera), aunque puede Ud. usar para su máquina el nombre que prefiera.
Para realizar ese cambio ha de editar Ud. los siguientes ficheros (necesita usar `sudo` para tener permisos de
root al tratarse de ficheros del sistema) y sustituir en ellos el nombre actual de la máquina (que es "ubuntu") por el que haya elegido:
```
$ sudo vi /etc/hostname
$ sudo vi /etc/hosts
```
Para que este cambio tenga efecto, ha de reiniciar la máquina.  
Siempre puede reiniciar la máquina desde la interfaz web de administración o bien usando el comando:
```
$ sudo reboot
```

#### git y GitHub
12. Compruebe que `git` está instalado en su máquina:
```
$ git --version
```
Si nunca ha usado Git, tal vez le interese conocer los
[conceptos básicos](https://docs.github.com/es/get-started/using-git/about-git)
de la herramienta.
Si quiere un tutorial rápido sobre los principales comandos que necesitará, 
[esta](https://www.linux.com/topic/desktop/introduction-using-git/)
puede ser una buena referencia para comenzar.
Hay mucha más documentación sobre Git en línea:
* [GitHub Guides](https://docs.github.com/es)
* [Cheat Sheet for Common Operations](https://training.github.com/downloads/github-git-cheat-sheet.pdf)
* [Command Reference](https://git-scm.com/docs)
* [Online Simulator/Tutorial](https://learngitbranching.js.org/?locale=es_ES)
Con posterioridad a esta práctica, revise esta documentación.

13. Consiga que se pueda subir código desde su máquina virtual hacia su cuenta GitHub sin necesidad de autentificación. 
Consulte para ello las instrucciones
[Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
En su máquina virtual ejecute los siguientes comandos para generar e instalar una clave SSH (donde `alu...edu.es` es la cuenta que haya utilizado para registrarse en GitHub):
```
$ ssh-keygen -t ed25519 -C "alu...edu.es"
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_ed25519
$ cat ~/.ssh/id_ed25519.pub
```
  - El primer comando le preguntará dónde generar la clave y si desea darle una contraseña. En ambos casos puede pulsar *Enter* sin escribir ningún valor para mantener los valores por defecto.
  - El cuarto comando mostrará por pantalla todo el contenido de la clave generada, que debería ser una línea que comienza por `ssh-ed25519` y termina con su cuenta de correo electrónico. Seleccione y copie la línea completa.
  - En su cuenta de GitHub, haga clic en el icono con su foto en la esquina superior derecha y luego en *Settings.* En la columna izquierda, haga clic *SSH and GPG keys* del apartado *Access* y luego en el botón *New SSH key.*
  - Dé a su nueva clave el nombre que prefiera (por ejemplos, "Informática Básica 2026/2027") y pegue el contenido de la clave generada. Pulse en "Add SSH Key" y su cuenta GitHub quedará enlazada con su máquina virtual.

14. Cree un directorio `practicas` y clone en él un repositorio git:
```
cd
mkdir practicas
cd practicas
git clone git@github.com:ULL-IB/P01-IaaS.git P01-EntornoIaaS
```

#### Edición y compilación
15. Colóquese en el directorio `practicas` (`cd ~/practicas`) y utilice el editor `vi` para escribir el código fuente del programa 
[hello_world.cc](https://github.com/ULL-IB/code-examples/blob/main/introduction/hello_world.cc).
A continuación, compile y ejecute ese programa.
Para compilar el programa escriba el siguiente comando (que estudiaremos más adelante en la asignatura)

`$ g++ -std=c++14 -g -Wall -o hello_world hello_world.cc`

Si `g++` no está instalado, instálelo siguiendo las instrucciones que se le mostrarán al intentar ejecutarlo. Utilice los comandos linux que conozca para ver los ficheros del directorio `~/practicas` en el que está
trabajando.

Para ejecutar el programa escriba:

`$ ./hello_world`

#### Simplificar la conexión a la VM

Los siguientes dos pasos son opcionales y deben ejecutarse en el equipo *desde el cual* se va a conectar a su máquina virtual, si éste tiene un sistema operativo Linux y tiene Ud. permisos de administrador

16. Siga [estas instrucciones](http://www.linuxproblem.org/art_9.html) 
para establecer la configuración de la máquina de modo que se pueda conectar a ella sin necesidad de escribir el password en cada conexión. 
Para poder conectarse por ssh con las máquinas virtuales de IaaS ull ha de autentificarse en la página [valida.ull.es](https://valida.ull.es).  
Recuerde que en caso de acceder desde fuera de del campus ULL ha de hacerlo mediante una conexión VPN. 
Consulte [esta referencia](https://www.ull.es/servicios/stic/2026/07/08/servicio-de-vpn-de-la-ull/) 
(en el Centro de Cálculo, por ahora no lo necesita) para conectarse a través de vpn.

17. También resulta conveniente utilizar alguno de los métodos (ssh config o alias) que se presentan en 
[estas instrucciones](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssh-shortcut)
de modo que se simplifique la conexión con la máquina remota pudiendo escribir algo como:
```
$ ssh vm_asignatura
```
para conectarse a la máquina virtual.
