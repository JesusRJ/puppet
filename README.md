# Coleção de dicas e scripts para montagem de ambientes com Puppet + Foreman

## Instalação do Foreman + Puppet Server no Centos 7.1

Comandos para configurar em uma mesma máquina o Foreman (1.9) com o Puppet Server (3.8):

rpm -ivh http://yum.puppetlabs.com/puppetlabs-release-el-7.noarch.rpm
yum -y install epel-release http://yum.theforeman.org/releases/1.7/el7/x86_64/foreman-release.rpm
yum -y install foreman-installer
yum install puppet-server
reboot
foreman-installer --enable-foreman-proxy

Seguir a ordem dos comandos é necessário, pois o foreman-installer é um conjunto de módulos do Puppet para configurar o todo ambiente. Ao executar o instalador do foreman será configurado não só o foreman, mas também o puppet.
O Puppet Master
