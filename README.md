# Setup your own Ansible Lab (jalinare)
A Vagrant configuration file to setup an Ansible Tower Lab to test it.

## Prerequisites
- VirtualBox
  https://www.virtualbox.org/wiki/Downloads 
- Vagrant 
  https://www.vagrantup.com/downloads 
- Git for Windows
  https://git-scm.com/downloads 
- Mobaxterm (Optional)
  https://mobaxterm.mobatek.net/download.html

### Additional software recommended
- **Microsoft Visual Code** (or your own prefered text editor)
  https://code.visualstudio.com/download 
- Postman 
  https://www.postman.com/downloads/ 
- HeidiSQL
  https://www.heidisql.com/download.php
- Ubuntu for Windows 10 https://ubuntu.com/tutorials/ubuntu-on-windows#1-overview

> You can find the complete list [here](./SOFTWARE.md)

## Setup your lab environment
Once you have all the prerequisites covered you have to download the Vagrant configuration file from this repository:

``git clone https://github.com/karkul/ansiblelab.git``

> Note: you shuld open a git bash shell or use a git GUI client

Then change to the new directory created:

``cd ansiblelab``

Then run `vagrant up` wait... and *¡Voila!* you have your own Ansible Tower lab.

> Note: if you want to add more hosts to test you must change the value of the `NodeCount` variable in the `Vagrantfile` and run `vagrant reload` from your terminal to add the new nodes.

For more information about how to adjust the `Vagrantfile` please refer to [here](https://www.vagrantup.com/docs/vagrantfile)

At least please join us in our **Slack** [#automation2021](https://join.slack.com/t/automation2021/shared_invite/zt-pz48bp9j-9g7UYbVUlc82E4SKyAO2MQ) channel and be part of our community!
