# RisenPC-Fluxbox-ES
Fluxbox personalizado en español para Ordenadores con pocos recursos

Si bien es cierto MX Linux 21 tiene una versión con Fluxbox no me gusta cómo la han hecho, ejemplo ellos han reemplazado la barra de tareas que si tiene Fluxbox por la de un programa, yo prefiero usar la que tiene Fluxbox

# Requerimientos
Se requiere lo sigiente:

- MX Linux 21 versión XFCE de 32 o 64 bits

**Nota:** Pero también se puede instalar en MX 19 u otro superior de MX Linux

**Descargar MX Linux desde:**

[https://sourceforge.net/projects/mx-linux/files/Final/Xfce/](https://sourceforge.net/projects/mx-linux/files/Final/Xfce/)  

redirigido desde (donde están las ISO más actuales):

[https://mxlinux.org/download-links/](https://mxlinux.org/download-links/)  

**Explicación.-** Esta versión de MX Linux XFCE no trae instalado la versión de Fluxbox MX Linux por lo cual allí podremos usar estas configuraciones (digo esto porque MX Linux tiene una versión de Fluxbox pero yo no la uso porque no me gusta). Además es importante tomar en cuenta que todo este tutorial está diseñado para MX Linux 21 por lo que si lo desea usar en otro Sistema Operativo Linux deberá modificarlo muy seguramente.

# Instalación de Fluxbox y dependencias
Este tutorial ha sido hecho en MX Linux 21 la versión XFCE. Con lo siguiente nos aseguraremos de habilitar lo más basico además de dejar configuradas las aplicaciones KDE 

**Dependencias**


    sudo apt-get install fluxbox lxappearance lxrandr pnmixer numlockx \
    xfce4-appfinder xfce4-notes gnome-terminal qt5ct nitrogen \
    breeze gnome-icon-theme gxkb thunar gammy

dele Enter y poner "s" de que si acepta

**Nota:** Para instalarlo en MX Linux 19 debe quitar el paquete gammy.   

# Borre los estilos del paquete de Fluxbox  

El comando anterior instalará fluxbox pero ese trae unos temas muy feos, yo nunca los uso, yo los borro, le recomiendo hacer lo mismo, ponga en la terminal:

```
sudo rm -fr /usr/share/fluxbox/styles/
```

No se preocupe aquí usaremos los de MX Fluxbox

# Borrar los archivos originales de Fluxbox si Ud los usaba
Si usted estaba usando Fluxbox debe haber una carpeta escondida (Si no es este su caso omita este paso) , veala con Ctrl + H

.fluxbox

esa carpeta hay que borrarla si es que la tenía, así:

```
sudo rm -fr ~/.fluxbox
```

# Instalar RisenPC Fluxbox Español
A continuación les dejaré dos maneras de instalar RisenPC Fluxbox ES, la primera es para un usuario normal

**Nota:** Sólo use una de las **dos** formas

## Instalar RisenPC Fluxbox Español para usuario normal
Abra una terminal y:

![](vx_images/357762909269284.png)

copie todo de una sola vez (Terminales como XFCE4-Terminal o Konsole admiten pegar todo de una sola vez) (también si no le funciona copie uno por uno):

```
    git clone https://github.com/wachin/RisenPC-Fluxbox-ES
    mv RisenPC-Fluxbox-ES ~/.fluxbox
    cd .fluxbox
    mkdir -p ~/.config/pnmixer/
    cp config ~/.config/pnmixer/ && cd && echo "Dios les bendiga"
```

peguelo en una terminal como lo indica la imagen anterior y ejecutelo
    
**Explicación**  
1er línea.- Clona el repositorio  
2da línea.- Mueve el repositorio entero allí mismo en su HOME cambiandole el nombre a .fluxbox  
3ra línea.- Entra en la carpeta oculta .fluxbox  
4ra línea.-  Crea la carpeta pnmixer (si ya estuviera no)  
5ta línea.- Copia y pega el archivo config de pnmixer que puse dentro de la carpeta .fluxbox que contiene la instrucción "pavucontrol" para que al darle clic y dar clic en elbotón "Mixer" aparezca el control de volumen. **Nota:** También se lo podría Ud poner manualmente así: Clic derecho al icono --> Preferences --> Behavior --> Volume Control Command y allí añadir: "pavucontrol"  

Por cierto, en la terminal quedarán ubicados en .fluxbox pero pueden salir de allí con cd.


## Instalar RisenPC Fluxbox Español para Desarrolladores
Esta es la segunda manera de instalar RisenPC Fluxbox si usted es un desarrollador y desea cambiar el funcionamiento de este proyecto le recomiendo instalarlo de otra manera, de clic en el siguiente enlace:

[RisenPC-for-DEV.md](RisenPC-for-DEV.md)



# Configurar qt5ct utilidad de configuración de Qt5
Esto es necesario para las aplicaciones que han sido escritas en Qt (KDE) como por ejemplo Dolphin, Kate, etc para poder elegir los iconos y temas de ellas

Ponga en una terminal:

```
 echo "export QT_QPA_PLATFORMTHEME="qt5ct"" >> ~/.profile
```

Con esto hemos añadido esa última línea al archivo oculto .profile


# Instalar Menú de aplicaciones con iconos, con xdgmenumaker
El siguiente programa necesario se llama xdgmenumaker, que me gustaría que lo pongan dentro de alguna carpeta aparte, yo estoy usando:

🗀AppsLinux

usted puede crearla manualmente:

![](vx_images/300784791826807.png)

o también lo podría hacerlo desde una terminal con los siguientes comandos:

```
mkdir -p ~/AppsLinux
cd ~/AppsLinux
```

de cualquier manera si lo haga manual o desde la terminal, luego instale los paquetes:

```
sudo apt-get install txt2tags python3-xdg gobject-introspection
```
y luego el programa xdgmenumaker:

```
git clone https://github.com/gapan/xdgmenumaker && cd xdgmenumaker && make
```

y hagase super usuario (ponga su contraseña):

```
sudo su 
```
en la siguiente imagen verá usted hasta donde debe usted estar ubicado:

![](vx_images/547226287889771.png)

y luego poner lo siguiente:

```
make install && cd .. && exit
```

aquí un captura:

![](vx_images/547226287889772.png)

Con esto tendrá iconos de la mayoría de las aplicaciones en el menú de fluxbox

**Nota**: Si lo sedea puede borrar la carpeta xdgmenumaker

    sudo rm -fr xdgmenumaker


## Creando el Menu de fluxbox, con xdgmenumaker

Antes de hacer esto debe:

**Reiniciar y entrar en la sesión de Fluxbox**

La primera vez que ha hecho esta instalación debe crear el menu, ponga en una terminal:

    xdgmenumaker -i -s16 -f fluxbox > ~/.fluxbox/xdg_menu

esto es necesario hacerlo sólo una vez

En ese archivo xdg_menu se escribirán todas las aplicaciones que están instaladas en su sistema para que estén disponibles para el menú de Fluxbox 

Para ver el menú de clic derecho en el escritorio o clic derecho en una de las dos esquinas o Super + M quedará así:

![](https://raw.githubusercontent.com/wachin/RisenPC-Fluxbox-ES/main/RisenPC-Fluxbox.png)


## Actualizar el menú de Fluxbox cada vez que instale alguna aplicación
Esto debe saberlo pues en esta instalación se utiliza a xdgmenumaker pero hay que actualizar el menu después que uno instala alguna aplicación, para hacerlo clic en:

**Actualizar menu de Apps**  

![](vx_images/474065919268985.png)

Pero si no desea utilizar este menú sólo use el XFCE4-AppFinder


# Control de volumen
Clic en el control de volumen:
![](vx_images/408873991826523.png)

y clic en "Mixer"
![](vx_images/444275200615615.png)

y se abrirá el control de volumen:

![](vx_images/156116023941366.png)



# Temas de iconos para aplicaciones KDE (Qt)

Para estas aplicaciones se recomienda usar

Breeze  
Papuris  
Oxygen  

se configura en:

**Menú --> Herramientas --> Ajustes Qt "Aplicaciones KDE"**  

![](vx_images/478325900615604.png)

**Nota:** El menú principal de Fluxbox se lo puede abrir desde escritorio con clic derecho, o en las esquinas abajo izquierda o derecha abajo, o con el atajo de teclado Super + M

Esperar un poco hasta que se abran los ajustes de QT

y allí en la pestaña:

**Tema de iconos**

Seleccionar **Papirus**

![](vx_images/367306723941355.png)

este tema además es compatible con 

Dolphin  

como se explica con más detalle en:  

**Cambiar colores en carpetas de Dolphin (Administrador de archivos) en MX Linux 21, antiX 21 basados en Debian 11 Bullseye, y Ubuntu 22.04 y otros con "Dolphin Folder Color"**  
[https://facilitarelsoftwarelibre.blogspot.com/2022/05/cambiar-colores-en-carpetas-de-dolphin-con-dolphin-folder-color-en-debian-11-ubuntu-22.04.html](https://facilitarelsoftwarelibre.blogspot.com/2022/05/cambiar-colores-en-carpetas-de-dolphin-con-dolphin-folder-color-en-debian-11-ubuntu-22.04.html)  

## El tamaño de las fuentes de las aplicaciones QT

Allí mismo en el configurador QT de clic en la pestaña:

**Tipos de letra**

![](vx_images/547226287889779.png)

allí arriba como se ve en la imagen cambiar el tamaño de las fuentes:

![](vx_images/547226287889780.png)

después dar clic en Aplicar luego en Aceptar y cerrar la aplicación escrita en QT ejemplo Kate, Dolphin u otra y vuelvala a abrir y ya tendrán las fuentes otro tamaño, o si cambió la fuente estará usando otra, allí como ve yo le he puesto:

**DejaVu Sans** - **Book** - **11**

pero usted puede elegir otro tipo, estilo, tamaño

como puede ser:

![](vx_images/547226287889781.png)

y lo dejo así:

![](vx_images/547226287889782.png)

y allí le di clic en Aceptar y Aplicar y reinicié la aplicación Qt que necesitaba.

# Atajos de teclado

Antes de que vea la configuración de los atajos de teclado, si usted es curioso y luego quisiera editar los atajos para añadir uno (para usuarios avanzados) puede dar clic derecho en algún lugar del escritorio si estuviera sin ninguna aplicación encima o sino de clic derecho a la izquierda abajo del escritorio:

![](/home/wachin/Dev-wachin/RisenPC-Fluxbox-ES/vx_images/547226287889775.png)

luego clic en:

![](vx_images/547226287889776.png)

allí yo puse las siguientes configuraciones al archivo .fluxbox/keys

![](vx_images/547226287889777.png)

allí si ustedes quisieran podrían editar eso o poner otros atajos, pero esto es opcional

Ahora si, los atajos

## AppFinder
Para abrir el buscador de aplicaciones AppFinder (xfce4-appfinder)

Tecla Windows + A

![](vx_images/547226287889770.png)

**Nota:** La Tecla de Windows también es conocida como Super, o Mod4 en las configuraciones de los atajos de teclado de Fluxbox. El AppFinder es de XFCE y desde la terminal se lo puede lanzar con xfce4-appfinder


## Abrir menu de aplicaciones
EL siguiente atajo de teclado es para abrir el menu de aplicaciones en cualquier lugar donde esté el cursor, con el atajo de teclado:

Tecla Windows + M

o lo que es lo mismo:

Super + M

![](vx_images/528004816576412.png)

**Nota:** Si no elige ninguna aplicación aplaste ESC para escapar

## Poner una ventana siempre encima
Si usted por ejemplo tiene abierta la terminal y quisiera que ella esté siempre enfrente de las demás ventanas aplaste:

Alt + V

para devolver esa ventana a su estado normal, estando enfrente de la ventana de esa aplicación otra vez dar:

Alt + V

**Nota:** La Tecla Alt se llama Mod1 en las configuraciones de los atajos de teclado de Fluxbox


## Minimizar ventanas
En con las teclas:

Alt + Z

le puse este atajo de teclado porque para mi es más fácil de usar, pero si ustedes quisieran le pueden poner otro

**Nota**: Esto lo modifiqué del archivo "key" en # current window commands donde originalmente tenía:  Mod1 + F9


 ## Minimizar todas las ventanas (no se puede)
 Pngo este título pues yo habría querido que hubiera una manerea de poder minimizar todas las ventanas de programas abiertas como en Windows (Super + D) pero no se puede, aunque se puede minimizando una por una


# Control de brillo para evitar cansancio ocular

Gammy está en los repositorios de MX Linux 21 y si ha hecho esta instalación allí pues ya está instalado pues lo he incluido en el archivo .fluxbox/startup al autoinicio, por lo que cuando usted entre en la sesión, Gammy se abrirá a la derecha abajo entre los iconos, la siguiente imagen es de Gammy en MX Linux 21 (yo lo uso como indico en la imagen):

![](vx_images/547226287889778.png)



**Para Instalarlo en MX Linux 19.-** hay que compilarlo desde el código fuente, ver:

**Compilando gammy 0.9.51 (herramienta para ajustar el brillo / temperatura del monitor) en MX Linux 19**
<https://facilitarelsoftwarelibre.blogspot.com/2022/02/compilando-gammy-en-mx-linux-19.html>


# Cómo cambiar de Estilo de Fluxbox
Cuando usted cambie de estilo:

En es escritorio clic derecho en el menú, o en las esquinas o Super + M y clic en **Estilos**

![](vx_images/67240114268985.png)

en esta imagen ustedes ven que se ven bien los nombres de los estilos disponibles, sin embargo cuando elijan otro estilo muy posiblemente no se verán bien, para que se vean bien si lo desean pueden cerrar sesión y cuando entren otra vez ya se verán bien las letras, pero esto de cerrar sesión no es necesario de hacerlo del todo, pueden seguir usando Fluxbox y ya en el siguiente ingreso se verá bien.

Por cierto hay algunos de estos temas en lo que al cambiar de tema no se ven todos los estilos disponibles, para arreglar eso de clic:

En es escritorio clic derecho en el menú, o en las esquinas o Super + M y clic en **Reajustar Fluxbox**

![](vx_images/353071596826508.png)

al hacer eso ya se verán bien todos los estilos disponibles


# Cambiar el idioma del teclado
Yo vivo en el Ecuador en Latinoamérica y uso la Distribución para Español Latino y por eso lo he dejado configurado para usarlo, cic en:

**Menú --> Preferencias > Startup "Aplicaciones que se cargan al inicio"**

![](vx_images/143144309268994.png)

allí en:

![](vx_images/424300892826517.png)

como ve en esa imagen lo puede cambiar por Español España siguiendo esos pasos, así cada vez que usted inicie su ordenador se cargará ese teclado


## Cambiando el idioma del teclado al vuelo (cambio rápido)
Les he dejado un menú para cambiar rápidamente de teclado

En es escritorio clic derecho en el menú, o en las esquinas o Super + M y clic en **Idioma del teclado**

![](vx_images/463993105615600.png)

No hay muchos idiomas, pero si ustedes necesiten algún otro me avisan

Esto es util pues imaginese que usted está traduciendo algún documento y quiera cambiar rapido a otro idoma


# Cambiar el wallpaper (Fonde de pantall)
Les he dajado en un menú para cambiarlo, la primera vez es necesario reiniciar nitrogen, clic en:

**Menú --> Herramientas --> Resetear  nitrogen en 1er uso y para usar Dos Monitores**

![](vx_images/378662901615609.png)

después de esto si ya pueden dar clic en:

**Menú --> Herramientas --> Cambiar Wallpaper con Nitrogen**

allí se abrirá nitrogen y podrán cambiar de wallpaper


# Problemas con abrir terminal en Thunar, cambiar por otra terminal
Si usted usa la opción de abrir la terminal aquí de Thunar pues no lo haga pues la terminal de XFCE (xfce4-terminal) no funciona bien en Fluxbox no se porqué (esto en MX Linux 19 o 21), mejor use Konsole, o gnome-terminal u otra

para hacerlo en el siguiente ejemplo con Konsole (debe ternerla instalada) añada otra terminal así, clic en:

**Editar --> Configurar Acciones personalizadas**

![](vx_images/227491714268986.png)

allí clic en el + y llene las siguientes acciones:

![](vx_images/224692296826509.png)

con los siguientes datos:

**Nombre:** Abrir Gnome Terminal aquí  
**Descripción:** Iniciar emulador de consola aquí  
**Orden:** gnome-terminal %f  

En icono pongale un icono de terminal, de clic en el botón

**Icono:**

luego clic en y ponga:

**Seleccionar icono de:** Todos los iconos  
**Buscar un icono:** utilities-terminal  

y **aceptar**

![](./img/196002%20pongale%20un%20icono%20de%20terminal.png)

y en la pestaña "**Condiciones de aparición**", marcar **Carpetas**:

![](./img/1960021%20pestaña%20condiciones%20de%20apareción%20marcar%20Carpetas.png)

y **Aceptar**

Ahora si desea puede ubicar más arriba a gnome-terminal, haga así búsque abajo a:

"**Abrir Gnome Terminal aquí**"

![](vx_images/547226287889773.png)

y me queda así:

![](vx_images/547226287889774.png)

Cuando quiera abrir terminal le aparecerá disponible Gnome Terminal

![](./img/1960024%20abrir%20con%20Gnome-terminal.png)



## Para añadir la terminal **Konsole**

Debe ternerla instalada:

`sudo apt install konsole`

los datos son así:

**Nombre**: Abrir Konsole aquí  
**Descripción**: Iniciar emulador de consola aquí  
**Orden**: konsole --workdir %f  

y en la pestaña "**Condiciones de aparición**", marcar **Carpetas**

y en **icono** lo mismo de arriba

cuando quiera abrir terminal aquí le aparecerá disponible Konsole

![](vx_images/300524728941352.png)

También si desea la puede mover más arriba

**Nota:** Se debería poder añadir otras terminales algo así mismo.

# Temas de iconos recomendados para usar Thunar 
Por defecto será usado el tema de iconos de Gnome que instalamos arriba y se verá el icono en la barra de herramientas, pero si usted desea usar otro como lo es Breeze, ya no se verá el icono de Thunar en la barra de herramientas

Si usted quiere usar otro tema de iconos uno de los que recomiendo es:

Papirus  

para usarlo 

**Menú --> Herramientas --> Personalizar apariencia y comportamiento**

**Nota:** El menú principal de Fluxbox se lo puede abrir desde escritorio con clic derecho, o en las esquinas abajo izquierda o derecha abajo, o con el atajo de teclado Super + M

![](vx_images/506513509268989.png)

allí en la pestaña:

Tema de iconos

![](vx_images/511683991826512.png)

También pueden usar las variantes:

Papirus-Dark  
Papirus-Light  

además el tema:

Numix también debería de funcionar bien. Pueden probar otros si desean

este tema de iconos es además compatible con las aplicaciones KDE si lo usaran también al ponerlo en "Qt5Ct"




# Editar las opciones de Fluxbox (opcional)
Para facil acceso les he dejado 

En es escritorio clic derecho en el menú, o en las esquinas o Super + M y clic en **Preferencias**

![](vx_images/455513928941351.png)

se abrirá el editor de texto que ustedes usen

# Gracias a Note
Este tutorial ha sido hecho gracias al editor de Markdown Multiplataforma VNote:

**Vnote for MX Linux 21 (y Linux basados en Debian 11 Bullseye) ~ Proyecto Facilitar el Software Libre en el Ecuador**
[https://facilitarelsoftwarelibre.blogspot.com/2022/07/vnote-for-mx-linux-deb-package.html](https://facilitarelsoftwarelibre.blogspot.com/2022/07/vnote-for-mx-linux-deb-package.html)

# Configurar la velocidad del cursor en dispositivos 
xinput-gui es una interfaz grafica para xinput que le permitirá editar propiedades de dispositivos como:

- Teclados
- Ratones
- Paneles táctiles
- Touchpad

Así será más rápido y fácil de usar, vea la siguiente entrada para ello:

**No funciona la velocidad del cursor al cambiar o poner un Mouse(o Touchpad) externo en Ubuntu 16.04, 18.04, OpenSUSE, Linux Mint, Debian, antiX, MX Linux, etc - SOLUCIÓN xinput-gui **  
[https://facilitarelsoftwarelibre.blogspot.com/2020/07/no-funciona-la-velocidad-del-cursor-al.html](https://facilitarelsoftwarelibre.blogspot.com/2020/07/no-funciona-la-velocidad-del-cursor-al.html)


Dios les bendiga  


# CONSULTAS: 

Editing_the_init_file  
http://fluxbox-wiki.org/category/howtos/en/Editing_the_init_file.html  

How to place the toolbar to the top in fluxbox? - Unix & Linux Stack Exchange   
https://unix.stackexchange.com/questions/146277/how-to-place-the-toolbar-to-the-top-in-fluxbox  

Fluxbox Documentation  
http://fluxbox.sourceforge.net/docbook/en/html/  

DSL Tips and Tricks :: Changing Fluxbox time display to 24 hour format  
http://www.damnsmalllinux.org/f/topic-3-26-12332-0.html  

IceWM install and setup guide  
http://forums.fedoraforum.org/showthread.php?t=282433  

xdgmenumaker  
https://github.com/gapan/xdgmenumaker  

Nitrogen - ArchWiki  
https://wiki.archlinux.org/title/nitrogen  

Xubuntu Thunar "Open Terminal Here" opens konsole in homefolder  
https://askubuntu.com/questions/891680/xubuntu-thunar-open-terminal-here-opens-konsole-in-homefolder  
https://askubuntu.com/a/892502  https://github.com/mifi/lossless-cut
