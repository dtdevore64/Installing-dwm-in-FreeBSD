# Installing-dwm-in-FreeBSD

<br><br>


***Step 1.*** First we will need to install some packages. I will list all of the packages and a brief description of them after installing them.

```
pkg install git xorg slim slim-themes pkgconf dmenu
```
<br><br>

| Package | Description |
| --------- | ----------- |
| git | Needed to clone repositories |
| xorg | X Display Server |
| slim | Lightweight login manager for X11, allowing for the initialization of a graphical session |
| slim-themes | Themes for the Slim login manager |
| pkgconf | Program which helps to configure compiler and linker flags for development libraries |
| dmenu | Dynamic Menu for X |

<br><br>

***Step 2.*** Now we will edit the ```/etc/rc.conf``` file to add a few lines in there to enable dbus and slim

```
dbus_enable="YES"
slim_enable="YES"
```

<br><br>

***Step 3.*** We need to create our ```~/.xinitrc``` file to add one line so we can execute dwm

```
exec dwm
```

<br><br>

***Step 4.*** Since we installed ```git``` earlier on we will now start cloning dwm

```
git clone https://git.suckless.org/dwm
```

<br><br>

***Step 5.*** After cloning the repository we need to ```cd``` into it to edit the ```config.mk``` file. Make sure the file says these exact lines:

```
X11INC = /usr/local/include
X11LIB = /usr/local/lib

FREETYPELIBS = -lfontconfig -lXft
FREETYPEINC = /usr/local/include/freetype2

```

<br><br>

***Step 6.*** We made changes to the file so now we have to compile it

```
make clean install
```

<br><br>

***Step 7.*** Time to clone the st terminal now

```
git clone https://git.suckless.org/st
```

<br><br>

***Step 8.*** After cloning the repository we need to ```cd``` into it to edit the ```config.mk``` file. Make sure the file says these exact lines:

```
X11INC=/usr/local/include
X11LIB=/usr/local/lib

```

<br><br>

***Step 9.*** Since we made the changes to the file in Step 11 we have to install one more package which is ```pkgconf``` for it to work because if not when we compile---it will give us errors so we will install the package and then compile.

```
pkg install -y pkgconf
make clean install
```

<br><br>

***Step 10.*** All we have to do now is just reboot and it will bring us into dwm

```
reboot
```

<br><br>







