#!/bin/bash


# Arch Linux Desktop Install (archdi)
# -----------------------------------
# author    : MatMoul
#             https://github.com/MatMoul
#             http://sourceforge.net/u/matmoul
# project   : https://github.com/MatMoul/archdi
#             http://sourceforge.net/projects/archdi/
# license   : GPLv3 (http://opensource.org/licenses/GPL-3.0)



apptitle="Arch Linux Desktop Install (archdi) - Version: 2019.07.03.22.44.21 (GPLv3)"
version="2019.07.03.22.44.21"
cachedir=~/.cache/archdi

lastverurl1=http://archdi.sourceforge.net/version
lastverurl2=https://raw.githubusercontent.com/MatMoul/archdi/master/version

binurl1=archdi.sourceforge.net/archdi
binurl2=matmoul.github.io/archdi

liburl1=http://archdi.sourceforge.net/archdi-lib
liburl2=https://raw.githubusercontent.com/MatMoul/archdi-pkg/master/lib

pkgurl1=http://archdi.sourceforge.net/archdi-pkg
pkgurl2=https://raw.githubusercontent.com/MatMoul/archdi-pkg/master/pkg.tar


help(){
  echo "-h | --help                   : this screen"
  echo "-i | --install                : install"
  echo "-l | --local dir              : run local archdi-pkg dir"
  echo "-t | --test githubuser branch : launch a forked branch"
  echo "no args                       : start archdi"
}

install(){
  dependencies
  echo "Install $apptitle ..."
  echo ""
  chmod 755 $0 2>/dev/null
  mv $0 /usr/bin/archdi 2>/dev/null
  echo ""
  echo "$apptitle is installed."
  echo "type archdi to start."
}

run(){
  dependencies
  rm -R $cachedir 2>/dev/null
  mkdir -p $cachedir 2>/dev/null
  cd $cachedir 2>/dev/null
  
  if [ ! "$pkgdir" = "" ]; then
    cp -r $pkgdir/* . >/dev/null
  else
    if [ "$pkgurl" == "" ]; then
      wget -O lib $liburl 2>/dev/null
    else
      echo ""
      echo "Downloading packages..."
      wget -O pkg.tar $pkgurl 2>/dev/null
      tar -xf pkg.tar
    fi
  fi
  
  chmod 755 lib 2>/dev/null
  if [ "$chrootoption" = "true" ]; then
    ./lib --chroot
    if [ ! "$?" = "0" ]; then
      archdi --branch master
    fi
  else
    if [ ! "$pkgdir" = "" ]; then
      sed -i "/apptitle=/c\apptitle=\"Arch Linux Desktop Install (archdi) - local: $pkgdir (GPLv3)\"" lib
      sed -i "/baseurl=/c\baseurl=$pkgdir" lib
      ./lib --root
      if [ ! "$?" = "0" ]; then
        archdi --branch master
      fi
    else
      if [ "$branchoption" = "" ]; then
        ./lib --root
        if [ ! "$?" = "0" ]; then
          archdi --branch master
        fi
      else
        sed -i "/apptitle=/c\apptitle=\"Arch Linux Desktop Install (archdi) - Branch: $branchoption (GPLv3)\"" lib
        sed -i "/baseurl=/c\baseurl=https://raw.githubusercontent.com/$githubuser/archdi-pkg/$branchoption" lib
        ./lib --root
        if [ ! "$?" = "0" ]; then
          archdi --branch master
        fi
      fi
    fi
  fi
  
  
  cd 2>/dev/null
  rm -R $cachedir 2>/dev/null
}

dependencies(){
  needinstall="false"
  clear
  echo "Checking internet and server connexion ..."
  lastverurl=$lastverurl1
  lastver=$(curl $lastverurl)
  if [ "$?" = "0" ] && [ "${#lastver}" = "19" ]; then
    binurl=$binurl1
    liburl=$liburl1
    pkgurl=$pkgurl1
  else
    lastverurl=$lastverurl2
    lastver=$(curl $lastverurl)
    if [ "$?" = "0" ] && [ "${#lastver}" = "19" ]; then
      binurl=$binurl2
      liburl=$liburl2
      pkgurl=$pkgurl2
    else
      exit 1
    fi
  fi
  echo ""
  echo "Checking $apptitle dependencies :"
  echo ""
  if [ -e /usr/bin/wget ]; then
    echo "wget : installed"
  else
    echo "wget : not installed"
    needinstall="true"
  fi
  if [ -e /usr/bin/whiptail ]; then
    echo "libnewt : installed"
  else
    echo "libnewt : not installed"
    needinstall="true"
  fi
  if [ "$needinstall" = "true" ]; then
    echo ""
    echo "Install missing dependencies ?"
    read -p "Install missing dependencies ? (Y/n)" choice
    case "$choice" in 
      n|N ) exit 1;;
    esac
    pacman -S --needed wget libnewt
  fi
  echo ""
  echo "Checking bin version..."
  chkupgrade
}

chkupgrade(){
  if [ "$0" = "/usr/bin/archdi" ]; then
    if [ ! "$version" = "$lastver" ]; then
      if (whiptail --backtitle "$apptitle" --yesno "New version found !\n\nInstall last version ?" 0 0) then
        cd /tmp
        wget $binurl
        sh archdi -i
        exit 0
      fi
    fi
  fi
}

branchoption=""
while (( "$#" )); do
  case $1 in
    -h|--help) help
               exit 0;;
    -i|--install) install
                  exit 0;;
    --chroot) chrootoption="true";;
    -b | --branch)
      shift
      liburl1=https://raw.githubusercontent.com/MatMoul/archdi-pkg/$1/lib
      liburl2=https://raw.githubusercontent.com/MatMoul/archdi-pkg/$1/lib
      pkgurl1=""
      pkgurl2=""
      branchoption="$1"
      githubuser="MatMoul"
    ;;
    -l | --local)
      shift
      apptitle="Arch Linux Desktop Install (archdi) - Version: local ($1)"
version="2019.07.03.22.44.21"
      pkgdir="$1"
    ;;
    -t | --test)
      shift
      liburl1=https://raw.githubusercontent.com/$1/archdi-pkg/$2/lib
      liburl2=https://raw.githubusercontent.com/$1/archdi-pkg/$2/lib
      pkgurl1=""
      pkgurl2=""
      branchoption="$2"
      githubuser="$1"
    ;;
  esac
  shift
done

run
