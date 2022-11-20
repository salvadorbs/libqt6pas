README
===========



**Unofficial libqt6pas**
========


<sub>Don't edit this markdown file, its generated from the tomboy-ng note.</sub>



**Please Note :** you probably don't need these files unless you are using Lazarus Main and Qt6. Several LTS distros will not have a viable Qt6 at present.



Download packaged libraries (Debs, RPMs and a tar ball) for x86_64 from https://github.com/davidbannon/libqt6pas/releases/latest



The packages should work on distributions like Ubuntu 21.10, Fedora 35 and RH EL9.  Note that ones like Debian Bullseye, Ubuntu 20.04 for example will not work with these libraries, their official repos do not have  Qt6. In paractis, you need a Qt6 6.2.3 and GLibc 2.34 or later. But there are no guarantees folks !



Its possible libraries pacman and for arm and arm64 will appear in the not too distant future.



libqt6pas is an interface between Lazarus and the Qt5 libraries.  Not all Qt6 functions are available, only those necessary for Lazarus functionality. See https://wiki.freepascal.org/Qt6_Interface



This is an unofficial copy of the libqt6pas code from the Lazarus Main (aka Trunk, master). It is very new, should be regarded as experimental but does appear to work ! At some point in time, the distros will catch up and, if you can, you should use a distro distributed verion of the library. However, its possible that the libraries here will often be ahead of your distro.



The code here will never be ahead of that in the Lazarus trunk but will track it, superficially tested as changes are made to the relevant content in Lazarus Main.



Bug reports about the library itself should be submitted to the normal Lazarus bug tracking system, https://gitlab.com/groups/freepascal.org/lazarus/-/issues



Bug reports relating to this repository's **packaging or currency** should be reported here.



**Names and Numbers**
--------


The main library Deb package looks a bit like this - `libqt6pas6_2_0-0_amd64.deb`

   * The package name is   libqt6pas

   * The "6_2" indicates its based on Qt6.2 LTS series, works fine with later Qt6 too.

   * The "_0" will indicate later release of the bindings, still with Qt6.2

   * The "-3" is the usual debian packaging release, I'll increment that if I release new packages with same library. Yeah, '3', I am not doing well !



The library itself, is called `libQt6Pas.so.6.2.0`, note the upper case letters, its a Qt thing apparently. It will normally have symlinks from libQt6Pas.so.6.2 and  libQt6Pas.so.6. If you have the -dev package installed, it will add a symlink from libQt6Pas.so



Note that in the early release stages of this library, its version number was 6.2.3 (reflecting the exact release it was first built on). That was wrong, you should remove and discard that package. It number conflicts ....



**Repackaging**
--------
OK, we are now on the third packaging of the same library. All to do with version numbers and issues relating to building the library in the correct Linux Distro. Note, it does not matter which distro you **use** it in (as long as its new enough), but it must be **built** on, eg, Fedora 35 (my problem, not yours!).





**Building this Library**
--------
**For example, on an Ubuntu 20.04 box.**

**Note :** I choose U2004 because it has the Qt6.2 series (6.2.4) and its a long term support release. Below are just my notes really but might help someone else. However, I soon found that was wrong (thanks bogan85) !  There are still some Linux Distros, under support, with Qt6 that predate U2204. So, its necessary to build the library on, in my case, a Fedora 35 VM, install qt6-qtbase-devel 6.2.3, pulldown the github files and -



wget https://github.com/davidbannon/libqt6pas/archive/refs/heads/master.zip

// unzip the above somewhere

    cd libqt6pas-master/cbindings
    qmake6 -query   // just to have a look
    qmake6   // to build the Makefile
    make     // build the library, slow !


Then copy the resulting library back somewhere where it can be used on build the debs, for me that my U2204m VM.



    sudo apt install qt6-base-dev alien rpm lintian, vim  // bit over 400Meg
    // cd to the libqt6pas git controlled directory
    cd libqt6pas-master/cbindings/package
    // if its a repackage of same code, edit PACKVER in script
    ./deb-package   // Make debs, RPMs and tarball


Upload the packages, do the git stuff !












