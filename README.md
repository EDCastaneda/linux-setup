# Linux Setup Guide
Description and tools to set up linux dev machine.

## Install Ubuntu

### Bootable USB 

* Download the latest ISO LTS [ubuntu](https://ubuntu.com/download/desktop) distribution.
* Run `Startup Disk Creator` to write the ISO image to your USB stick.

## Security Tools

### Livepatch

Setup Canonical Livepatch Service from official [docs](https://ubuntu.com/security/livepatch).

```bash
sudo snap install canonical-livepatch
sudo canonical-livepatch enable
```

### Synaptic Package Manager GUI

```bash
sudo apt-get update
sudo apt-get install synaptic
```

### GUFW

```bash 
sudo apt-get update -y
sudo apt-get install -y gufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

### Prey

See more info in the [help](https://help.preyproject.com/article/292-install-prey-on-ubuntu-or-any-other-debian-based-distribution) page.

```bash
# download deb file
cd $HOME/Downloads/ 
wget https://downloads.preyproject.com/prey-client-releases/node-client/1.9.11/prey_1.9.11_i386.deb 

# install dependencies
sudo apt install libgtk-3-dev scrot streamer mpg123

# if you have issues adding these dependencies
sudo apt --fix-broken install

# install package
sudo dpkg -i prey_1.9.11_i386.deb
sudo apt-get install -f

# launch the config page
sudo /usr/lib/prey/current/bin/prey config panel

# run gui and login
cd /usr/lib/prey
find * -name *.py
sudo versions/1.9.11/lib/conf/gui/linux/prey-config3.py
```

## gocryptfs + sirikali

TO encrypt folders follow the [quickstart](https://nuetzlich.net/gocryptfs/quickstart/).

```bash 
sudo apt install gocryptfs
```

The GUI is provided by [sirikali](https://github.com/mhogomchungu/sirikali).



## System Tools

### Docker

Follow instructions for [docker](https://docs.docker.com/engine/install/ubuntu/) installation.

Once Docker is up and running, install [docker-compose](https://docs.docker.com/compose/install/).

### Terminator

```bash 
sudo apt-get update -y
sudo apt-get install -y terminator
```

### Unison

```bash 
sudo apt-get update -y
sudo apt-get install -y unison-gtk
```

### Tweaks

```bash 
sudo apt install gnome-tweaks
```

### BingWall

```bash 
sudo snap install bing-wall
```

## Dev Tools

### Git

From the official [documentation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
```bash
sudo apt install git-all
```

## Node.js

Following the tutorial by [digitalocean](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04).

```bash
sudo apt update
sudo apt install nodejs
sudo apt install npm
```

## Data Bases

### PostgreSQL

From installation [tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart).

```bash 
# install package
sudo apt install postgresql postgresql-contrib

# test default postgres user
sudo -u postgres psql

# exit db session
postgres=# \q
```

To add new user to use the db

```bash 
sudo -u postgres createuser --interactive

# or within the session
postgres=# createuser --interactive

# the output within the session
postgres=# Enter name of role to add: new_user
postgres=# Shall the new role be a superuser? (y/n) y
```

To create a new db

```bash 
sudo -u postgres createdb new_db_name

# or within the session
postgres=# createdb new_db_name
```

### MongoDB

Follow instructions for [installation](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/).

