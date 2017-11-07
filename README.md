# Running

## Your PC - Experiment Manager:

* Install Python 2.7
  * Most Linux distributions have python installed natively. To test, 
  run on terminal: ```python --version```
* [Install ansible](http://docs.ansible.com/ansible/intro_installation.html)
* [Install pip](https://pip.pypa.io/en/stable/installing/)
  * You can install pip using: ```easy_install pip```
* Change [ansible/hosts](ansible/hosts) file to put your hosts IP
* Install ansible extra modules:
  * RVM: `sudo ansible-galaxy install rvm_io.rvm1-ruby`

### Install collectl visualization tool - colplot:

Based on [this tutorial](http://www.krazyworks.com/collectl-colplot-sytem-performance-analysis-tools/)

* Install apache2: `sudo apt-get install apache2`
* Install collectl: `sudo apt-get install collectl`
* Install colplot:
```
v="5.0.0"
cd /tmp
wget http://downloads.sourceforge.net/project/collectl/Colplot/colplot-${v}.src.tar.gz
gzip -d colplot-${v}.src.tar.gz
tar xvf colplot-${v}.src.tar
cd colplot-${v}
sudo ./INSTALL
```
* Configure apache2:

```
logdir=/opt/colplot/logs
sudo mkdir -p "${logdir}"
sudo chown -R www-data:www-data "${logdir}"
```
* Restart apache2: `sudo service apache2 restart`

## Remote hosts - Managed nodes:

* In each managed node, pointed by [hosts](ansible/hosts), you need to
communicate via **ssh** :
  * Install python 2.4 or later
  * Enable ssh communication
  * Add you ssh public key to **root** user in remote hosts. [Here's an
  example](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server)