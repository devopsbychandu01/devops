### windows ###
# 32 bit: 
https://github.com/git-for-windows/git/releases/download/v2.42.0.windows.2/Git-2.42.0.2-32-bit.exe
# 64 bit
https://github.com/git-for-windows/git/releases/download/v2.42.0.windows.2/Git-2.42.0.2-64-bit.exe
# Using winget tool
winget install --id Git.Git -e --source winget


### Linux ###
# Debian/Ubuntu

apt-get install git
add-apt-repository ppa:git-core/ppa # apt update; apt install git

# Fedora
yum install git (up to Fedora 21)
dnf install git (Fedora 22 and later)

# Gentoo
emerge --ask --verbose dev-vcs/git

# Arch Linux
pacman -S git
# openSUSE
zypper install git

# Mageia
urpmi git

# Nix/NixOS
nix-env -i git

# FreeBSD
pkg install git

# Solaris 9/10/11 (OpenCSW)
pkgutil -i git

# Solaris 11 Express
pkg install developer/versioning/git

# OpenBSD
pkg_add git

# Alpine
apk add git

# Red Hat Enterprise Linux, Oracle Linux, CentOS, Scientific Linux, et al.
yum install git

# Slitaz
tazpkg get-install git


### MacOS ###
# Using Homebrew
brew install git
# using MacPorts
sudo port install git
