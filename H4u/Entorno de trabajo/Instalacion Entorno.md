
## Instalacion del SO

1. Instalar Parrot o Kali
2. En caso de no tener internet, configurar una direccion estatica en '/etc/network/interfaces' . Los datos son relativos al usuario
```txt
auto ens33
iface ens33 inet static
		address 192.168.1.150
		netmask 255.255.255.0
		gateway 192.168.1.1
		dns-nameservers 8.8.8.8
```

3. En caso de que no resuelva el dns de google, modificar el archivo '/etc/resolv.conf'
```txt
nameserver 8.8.8.8
nameserver 1.1.1.1
```

--- 
## Instalando Bspwm y Sxhkd

- Bspwn: Gestor de ventanas tipo mosaico que las organiza
- Sxhkd: Gestor de atajos de teclado

1. Realizar un sudo apt-get update
2. Instalar todos los paquetes: apt install build-essential git vim xcb libxcb-util0-dev libxcb-ewmh-dev libxcb-randr0-dev libxcb-icccm4-dev libxcb-keysyms1-dev libxcb-xinerama0-dev libasound2-dev libxcb-xtest0-dev libxcb-shape0-dev
3. Realizar un upgrade: parrot-upgrade
4. Clonar los respositorios:
	- git clone https://github.com/baskerville/bspwm.git
	- git clone https://github.com/baskerville/sxhkd.git
5. Colocar en ambas carpetas 'sudo make' y 'sudo make install'

---
## Configurando el sxhkd

1. Del repositorio bspwm entrar a examples
2. Crear 2 directorios en ~/.config/{bspwm,sxhkd}
3. Copiar los archivos bspwnrc y sxhkdrc de examples a las nuevas carpetas creadas correspondientemente
4. Instalar la kitty: sudo apt install kitty -y
5. Ingresar al archivo sxhkdrc ubicado en : ~/.config/sxhkd/sxhkdrc y realizar las siguientes configuraciones:
	- terminal emulator: super + Return // kitty
	- focus the node in the given direction : reemplazar h,j,k por Left, Down, Up, Right
	- Preselect the direction: Reemplazar super + ctrl + alt + {Left,Down,Up,Right}
	- Cancel the preselection: super + ctrl + alt + space
	- Move a floating window : super + shift + {Left,Down,Up,Right}
	- Comentar todo lo anterior hasta move/resize
	- Agregar:
```txt
# Custom Resize
alt + super + {Left,Down,Up,Right}
	/home/jesus/.config/bspwm/scripts/bspwm_resize {west,south,north,east}
```

6. Crear la carpeta donde ira el script : mkdir /home/jesus/.config/bspwm/scripts/
7. Crear el archivo del script: touch /home/jesus/.config/bspwm/scripts/bspwm_resize y darle permisos de ejecucion
8. Introducir este script:
```bash
#!/usr/bin/env dash

if bspc query -N -n focused.floating > /dev/null; then
	step=20
else
	step=100
fi

case "$1" in
	west) dir=right; falldir=left; x="-$step"; y=0;;
	east) dir=right; falldir=left; x="$step"; y=0;;
	north) dir=top; falldir=bottom; x=0; y="-$step";;
	south) dir=top; falldir=bottom; x=0; y="$step";;
esac

bspc node -z "$dir" "$x" "$y" || bspc node -z "$falldir" "$x" "$y"

```

---
## Instalacion de la Polybar

- Status bar

1. Instalar paquetes como root: apt install cmake cmake-data pkg-config python3-sphinx libcairo2-dev libxcb1-dev libxcb-util0-dev libxcb-randr0-dev libxcb-composite0-dev python3-xcbgen xcb-proto libxcb-image0-dev libxcb-ewmh-dev libxcb-icccm4-dev libxcb-xkb-dev libxcb-xrm-dev libxcb-cursor-dev libasound2-dev libpulse-dev libjsoncpp-dev libmpdclient-dev libuv1-dev libnl-genl-3-dev
	- python3-sphinx : Si genera conflicto, remover
2. Clonar el repositorio: git clone --recursive https://github.com/polybar/polybar
3. cd polybar > mkdir build > cd build > cmake ..
4. make -j$(nproc) > sudo make install
5. Verificar si ya se instalo el binario de la polybar: which polybar

---
## Instalacion de Picom 

1. Instalar paquetes como root: apt install meson libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev libpcre2-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev libxcb-glx0-dev
2. Clonamos el projecto de Picom: git clone https://github.com/ibhagwan/picom.git
3. cd picom > git submodule update --init --recursive > meson --buildtype=release . build
	- Si da inconvenientes el meso > sudo apt-get install libpcre3-dev 
4. ninja -C build > sudo ninja -C build install
5. sudo apt install rofi
6. Ir a la carpeta del sxhkdrc
7. Modificar:
```txt
# program launcher (ROFI)
super + d
	rofi -show run

# quit/restart bspwm
super + shift + {q,r}

# close and kill
super + {_,shift + }q

# Open Firefox                // Nueva instruccion
super + shift + f
	/urs/bin/firefox          // Ubicacion del binario
```
8. sudo apt install bspwm
9. Ir a la pantalla de bloqueo: kill -9 -1
10. Seleccionar el perfil de bspwm e ingresar
	- Cualquier modificacion en el sxhkd en el entorno bspwm se aplica con un W + ESC

---
## Configuracion de fuentes, kitty e instalacion de Feh

1. Descargar la fuente hack nerd Font de la pagina nerdFonts.com
2. Como root movemos el comprimido a '/usr/local/share/fonts'
3. En el directorio anterior descomprimimos el archivo: unzip Hack.zip > Eliminamos el comprimido
4. Habilitar la clipboard bidireccional: 
	- En el archivo ~/.config/bspwm/bspwmrc colocamos:
	- vmware-user-suid-wrapper & > Win + shift + r para recargar
5. Instalar zsh : sudo apt install zsh
6. Dentro de la carpeta kitty: cd ~/.config/kitty crear un archivo kitty.conf y pegar el siguiente documento [[Kitty.conf]] 
7. En la misma carpeta crear el archivo 'color.ini' y pegar el siguiente documento: [[Color.ini]]
8. Cerramos la terminal y volvemos a abrirla
9. Como root instalamos unos pluggins: apt install zsh-autosuggestions zsh-syntax-highlighting zsh-autocomplete (???????)
	- Si no funciona el syntax-highlighting, agregar esta linea al archivo /home/jesus/.zshrc : source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
10. Actualizar la kitty: Buscar en google kitty github y clickear en la ultima version de la kitty
11. Descargar el 'Linux amd64 binary bundle'
12. Por comodidad y orden, movemos el archivo descargado a '/opt' como root
13. Descomprimimos: 7z x kitty-xx-xx 
14. Descomprimimos el nuevo archivo: tar -xf kitty-x-x.tar en una carpeta 'kitty'
15. Eliminamos los comprimidos
16. Entramos a '/opt/kitty/bin/'
17. apt remove kitty
18. Configuramos la nueva direccion de la kitty que usaremos en el sxhkdrc, guardamos y reiniciamos el entorno
```txt
# terminal emulator
super + Return
    /opt/kitty/bin/kitty
```

19. Copiar toda la configuracion de la kitty del usuario no privilegiado al root: cp /home/jesus/.config/kitty/* /root/.config/kitty/

**Fondo de pantalla**
1. sudo apt install imagemagick
2. kitty +kitten icat shogunWallpaper.png : Comando para visualizar una imagen en consola
3. sudo apt install feh > feh --bg-fill shogunWallpaper.png : Establece un fondo de pantalla
4. Colocamos este comando en el bspwm para que se ejecute cada vez que iniciemos sesion
 
---
## Despliegue de la Polybar

1. Clonar : git clone https://github.com/VaughnValle/blue-sky.git
2. cd blue-sky/polybar > cp -r * ~/.config/polybar/
3. echo '~/.config/polybar/./launch.sh' >> ~/.config/bspwm/bspwmrc
4. cd fonts > sudo cp * /usr/share/fonts/truetype/ > fc-cache -v
5. Reiniciar : Win + shift + r

---
## Configurando bordeados, sombras etc con PICOM

1. Creamos el directorio picom en /home/jesus/.config/picom
2. Creamos el archivo 'picom.conf' y pegamos el contenido de [[picom.conf]]
3. Agregamos el picom al bspwm : echo 'picom &' >> /home/jesus/.config/bspwm/bspwmrc 
4. Actualizamos Win + shift + r
5. Opcional, quitarle el borde al marco de la kitty : bspc config border_with 0

---
## Configurando la ZSH

1. Buscamos en internet: powerlevel 10k github y buscamos la instalacion manual
2. Ejecutamos los comandos de la instalacion manual y ponemos en consola *zsh*
3. Procedemos con la instalacion
4. Entramos al archivo nano /home/jesus/.p10k.zsh y comentamos todo lo del POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS
5. Agregamos al POWERLEVEEL9K_LEFT_PROMP_ELEMENTS : context, command_execution_time, status
6. Realizar los mismos pasos para el usuario root
7. Establecer la zsh como terminal principal a ambos usuarios: usermod --shell /usr/bin/zsh root | usermod --shell /usr/bin/zsh jesus
8. Creamos un link simbolico para que los cambios en un .zshrc de user tambien se apliquen en root, se tiene que estar en el /root/: 
	- ln -s -f /home/jesus/.zshrc .zshrc 
	- Modificar esta linea del .zshrc: source /home/jesus/powerlevel10k/powerlevel10k.zsh-theme
9. Retocar de nuevo el .p10k.zsh de root del paso 4 y 5
10. Buscar en el .p10k del root (Ctrl + Q) ROOT_TEMPLATE 
	- typeset -g POWERLEVEL9K_CONTEXT_PREFIX=''
	- typeset -f POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE='Icono'  <- Que identificara al root en la powerlevel10k
11. Ajustar el bold de la powerlevel
	- Entrar al archivo .p10k de root y user, buscar DIR_ANCHOR_BOLD y setearlo en false
	- p10k configure : Para volver a configurar de 0 la powerlevel

---
## Batcat y lsd

1. Buscar en google bat github > release > bat \_xxx_amd64.deb 
2. dpkg -i bat\_xx_amd64.deb (como root)
3. Buscar en google lsd github > release > lsd \_xxx_amd64.dev
4. dpkg -i lsd...deb
5. sudo apt locate > updatedb
	- Las direcciones que nos digan permission denied hay que desmontarlas con: umount dire/ccion
6. Agregar en la ultima linea del .zshrc: [[LS_COLORS Definition]]
7. Agregar aliases en el .zshrc: [[Custom Aliases]]
8. Arreglando burpsuite
	- En el .zshrc agregar : # Fix Java Problem \\n export \_JAVA_AWT_WM_NONREPARENTING=1
	- Agregar en el bspwmrc : wmname LG3D &
9. Extra: Si hay problemas de proporcion
	- xrandr : Revisas el nombre del monitor
	- xrandr --output NombreMonitor --mode 1920x1080

---

## Configurando la Polybar

- launch.sh : Configuracion de lo que se quiere ver de la polybar se ubica en /home/jesus/.config/polybar

1. Revisar el archivo de configuracion launch.sh y ver la direcciones de las barras
2. Buscar (ctrl+q) el nombre de la barra en el archivo de donde carga y fijarse en 'modules-center', me indicara el modulo donde podre modificar su contenido


---
## Plugins en la zsh y NVChad

**Sudo plugin:**
1. Crear la carpeta /usr/share/zsh-sudo y darle al usuario : chown jesus:jesus zsh-sudo
2. Buscamos en google sudo plugin zsh y lo descargamos con wget link_en_raw.com/...
3. Damos permiso de ejecucion al script descargado
4. Agregamos el siguiente codigo al .zshrc
```bash
# SUDO ZSH
if [ -f /usr/share/zsh-sudo/sudo.plugin.zsh ]; then
    source /usr/share/zsh-sudo/sudo.plugin.zsh
fi
```

**NVChad:**
1. Descargamos npm: sudo apt install npm
2. Buscamos la wiki de NVChad y la linea de codigo de instalacion, antes borrar todo el contenido de rm ~/.config/nvim/* en caso de que exista
3. Buscamos nvim en github y descargamos nvim-amd64...
4. Lo descomprimimos en /opt como root y entramos al archivo
5. Entramos a bin > nvim de la carpeta /opt/nvim/bin/vim y ejecutamos nvim para que se instale, todo como usuario
6. Eliminamos el nvim de la maquina: sudo apt remove neovim
7. Agregar el binario del vin descargado al path, en el archivo .zshrc , agregar: /opt/nvim-linux64/bin:

- Para quitar el autocompletado
	- cd ~/.config/nvim/lua/plugins
	- Abrir el init.lua , buscar /cmp y eliminar todo

**ROFI:**
1. En la carpeta blue-sky que se descargo, hay un tema para el nord: nord.rasi
2. Crear una carpeta : mkdir -d ~/.config/rofi/themes y copiar el nord.rasi en la carpeta creada
3. rofi-themes-selector y seleccionar el ultimo

**Utilidades:**
- apt install flameshot ranger
- ranger : Navegacion facil entre directorios
- flameshot : Toma screenshots editables , flameshot gui
- i3lock : Bloqueador de pantalla
	- sudo apt install i3lock 
	- Buscar i3lockfancy e instalar el proyecto
	- i3lock-fancy 
- Agregar los binarios al sxhkd para tener atajos directos
- fzf : Buscar git hub e instala. Shorcut: ctrl + t
