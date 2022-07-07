# RisenPC-Fluxbox
FluxBox personalizado para Ordenadores con pocos recursos

Si bien es cierto MX Linux 21 tiene una versión con Fluxbox no me gusta cómo la han hecho, ejemplo ellos han reemplazado la barra de tareas que si tiene Fluxbox por la de un programa, yo prefiero usar la que tiene Fluxbox

# Requerimientos

Usar MX Linux versión XFCE, aquí unos enlaces para descargar:

https://sourceforge.net/projects/mx-linux/files/Final/Xfce/

https://mxlinux.org/download-links/

**Explicación.-** Esta versión no trae instalado la versión de Fluxbox MX Linux por lo cual allí podremos usar estas configuraciones

# Instalación de Fluxbox y dependencias
Este ha sido hecho en MX Linux 21 la versión XFCE. Con lo siguiente nos aseguraremos de habilitar lo más basico además de dejar configuradas las aplicaciones KDE 

Dependencias

    sudo apt-get install fluxbox lxappearance lxrandr pnmixer numlockx xfce4-appfinder xfce4-notes gnome-terminal qt5ct gammy breeze gnome-icon-theme gxkb

# Borre los estilos del paquete de Fluxbox  

Esto es porque los que vienen allí son para mi de mala calidad:

`sudo rm -fr /usr/share/fluxbox/styles/`

No se preocupe aquí usaremos los de MX Fluxbox, ponga en una terminal:

# Copiar los archivos de Fluxbox

Ponga en una terminal:

    git clone https://github.com/wachin/RisenPC-Fluxbox
    cd RisenPC-Fluxbox
    cp .fluxbox ~/.fluxbox

# qt5ct utilidad de configuración de Qt5
Ponga en una terminal:

    echo "export QT_QPA_PLATFORMTHEME="qt5ct"" >> ~/.profile

Con esto hemos añadido esa última línea al archivo, esto es necesario para las aplicaciones que han sido escritas en Qt (KDE) como por ejemplo Dolphin, Kate, etc para poder elegir los iconos y temas de ellas

Ahora cierre sesión y entre en la sesión de Fluxbox 



# Atajos de teclado
Las siguientes configuraciones pertenecen al archivo .fluxbox/keys

## AppFinder
Para abrir el buscador de aplicaciones AppFinder (xfce4-appfinder)

Tecla Windows + A

**Nota:** La Tecla de Windows también es conocida como Super, o Mod4 en las configuraciones de los atajos de teclado de Fluxbox


## Abrir menu de aplicaciones
EL siguiente atajo de teclado es para abrir el menu de aplicaciones en cualquier lugar donde esté el cursor, aplaste:

Tecla Windows + M

Si no elige ninguna aplaste ESC para escapar

## Poner una ventana siempre encima
Si usted por ejemplo tiene abierta la terminal y quisiera que ella esté siempre enfrente de las demás ventanas aplaste:

Alt + V

para devolver esa ventana a su estado normal, estando enfrente de la ventana de esa aplicación otra vez dar:

Alt + V

**Nota:** La Tecla Alt se llama Mod1 en las configuraciones de los atajos de teclado de Fluxbox


# Control de brillo para evitar cansancio ocular

Gammy está incluido en el archivo .fluxbox/startup al autoinicio, por lo que cuando usted entre en la sesión, Gammy se abrirá a la derecha abajo entre los iconos, allí usted la puede configurar a su gusto, también puede ver la entrada:

**Instalando Gammy 0.9.64 en MX Linux 21 desde los repositorios (Herramienta para ajustar el brillo / temperatura del monitor)**
https://facilitarelsoftwarelibre.blogspot.com/2022/01/control-de-brillo-de-pantalla-con-gammy-en-linux.html


# Menu de aplicaciones con iconos con xdgmenumaker
Ponga una por una estas siete lineas de comandos en una terminal:

```
sudo apt-get install txt2tags python3-xdg gobject-introspection
git clone https://github.com/gapan/xdgmenumaker
cd xdgmenumaker
make
sudo su
make install
exit
```

Con esto tendrá iconos de la mayoría de las aplicaciones en fluxbox


# Creando el Menu de fluxbox, con xdgmenumaker

La primera vez que ha hecho esta instalación debe crear el menu, ponga en la terminal:

    xdgmenumaker -i -s16 -f fluxbox > ~/.fluxbox/xdg_menu

en ese archivo se escribirán todas las aplicaciones que están instaladas en su sistema    

Reiniciar Fluxbox, para hacer esto de clic derecho en el escritorio y clic en "Reiniciar fluxbox"



y cuando entre quedará así:

![](https://raw.githubusercontent.com/wachin/RisenPC-Fluxbox-ES/main/RisenPC-Fluxbox.png)

Dios les bendiga


# CONSULTAS: 

fluxbox-wiki.org/category/howtos/en/Editing_the_init_file.html
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



