# Installing-dwm-in-FreeBSD

<br><br>

I will be installing dwm on FreeBSD 13.0-RELEASE on VirtualBox. This tutorial assumes you already have FreeBSD 13.0-RELEASE installed on your system.
<br><br>

***Step 1.*** First we will install ```git``` as you will need this to clone some repositories later on.

```
pkg install -y git
```

<br><br>

***Step 2.*** Next we will install ```xorg```.

```
pkg install -y xorg
```

<br><br>

***Step 3.*** Next we will install ```dmenu```.

```
pkg install -y dmenu
```

<br><br>

***Step 4.*** Next we will install ```slim``` and ```slim-themes```.

```
pkg install -y slim slim-themes
```

<br><br>

***Step 5.*** Now we will edit the ```/etc/rc.conf``` file to add a few lines in there to enable dbus and slim

```
dbus_enable="YES"
slim_enable="YES"
```

<br><br>

***Step 6.*** We need to create our ```.xinitrc``` file to add a line so we execute dwm

```
exec dwm
```

<br><br>

***Step 7.*** Since we installed ```git``` earlier on we will now start cloning dwm

```
git clone https://git.suckless.org/dwm
```

<br><br>

***Step 8.*** After cloning the repository we need to ```cd``` into it to edit the ```config.mk``` file. Make sure the file says these exact lines:

```
X11INC = /usr/local/include
X11LIB = /usr/local/lib

FREETYPELIBS = -lfontconfig -lXft
FREETYPEINC = /usr/local/include/freetype2

```

<br><br>

***Step 9.*** We made changes to the file so now we have to compile it

```
make clean install
```

<br><br>

***Step 10.*** Time to clone the st terminal now

```
git clone https://git.suckless.org/st
```

<br><br>

***Step 11.*** After cloning the repository we need to ```cd``` into it to edit the ```config.mk``` file. Make sure the file says these exact lines:

```
X11INC=/usr/local/include
X11LIB=/usr/local/lib

```

<br><br>

***Step 12.*** Since we made the changes to the file in Step 11 we have to install one more package which is ```pkgconf``` for it to work because if not when we compile---it will give us errors so we will install the package and then compile.

```
pkg install pkgconf
make clean install
```

<br><br>

***Step 13.*** All we have to do now is just reboot and it will bring us into dwm

```
reboot
```

<br><br>







