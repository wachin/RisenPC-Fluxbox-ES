## Instalar RisenPC Fluxbox Español para Desarrolladores

Si usted es un desarrollador y si le gustara esta manera de personalización de Fluxbox que yo he hecho, y lo quisiera cambiar a su gusto, primero:

- Haga haga un fork de mi repositorio entrando en la siguiente dirección (para ello usted debe tener una cuenta de Github y saberlo usar):

[https://github.com/wachin/RisenPC-Fluxbox-ES](https://github.com/wachin/RisenPC-Fluxbox-ES)

Segundo, le sugiero que lo ubique en una carpeta, ejemplo yo estoy usando una carpeta con el nombre:

🗀AppsLinux

usted puede crearla manualmente:

![](/home/wachin/Dev-wachin/RisenPC-Fluxbox-ES/vx_images/300784791826807.png)

o también lo podría hacerlo desde una terminal con los siguientes comandos:

```
mkdir -p AppsLinux
cd AppsLinux
```

sea como sea, usted deberá quedar ubicado en una terminal allí en AppsLinux o en la carpeta que usted quiera y allí poner los siguientes comandos: 

![](/home/wachin/Dev-wachin/RisenPC-Fluxbox-ES/vx_images/509041601615899.png)

copiar lo siguiente y ponerlo en una terminal:

```
git clone https://github.com/wachin/RisenPC-Fluxbox-ES
ln -s ~/AppsLinux/RisenPC-Fluxbox-ES ~/.fluxbox
```

esto clonará el repositorio creando la carpeta:

🗀RisenPC-Fluxbox-ES

y creará un enlace a:

.fluxbox

entonces usted podrá hacer cambios en el repositorio y automáticamente se verán reflejados en .fluxbox que es la carpeta de configuraciones de Fluxbox y serán aplicados los cambios en el menú u otras configuraciones que haga.

**Nota:** No borre la carpeta: RisenPC-Fluxbox-ES
