# Puppet

Coleção de dicas e scripts para montagem de ambientes com Puppet + Foreman

## Instalação do Foreman + Puppet Server no Centos 7.1

Comandos para configurar em uma mesma máquina o Foreman (1.9) com o Puppet Server (3.8):
```
rpm -ivh http://yum.puppetlabs.com/puppetlabs-release-el-7.noarch.rpm
yum -y install epel-release http://yum.theforeman.org/releases/1.7/el7/x86_64/foreman-release.rpm
yum -y install foreman-installer
yum install puppet-server
reboot
foreman-installer --enable-foreman-proxy
```
Seguir a ordem dos comandos é necessário, pois o foreman-installer é um conjunto de módulos do Puppet para configurar o todo ambiente. Ao executar o instalador do foreman será configurado não só o foreman, mas também o puppet.
O Puppet Master será executado com o passenger e não mais no systemd.

Referência: https://themacwrangler.wordpress.com/2015/01/07/installing-the-foreman-on-centos-7/

## Personalizando a instalação do Foreman

A execução do foreman-installer pode ser personalizada com os opções fornecidas pelo foreman-installer (exe.: foreman-installer -h para ver a lista de opções)

Ex.:
```
foreman-installer \
  --enable-foreman-proxy \
  --foreman-proxy-tftp=true \
  --foreman-proxy-tftp-servername=192.168.74.2 \
  --enable-foreman-compute-libvirt \
  --enable-foreman-compute-vmware \
  --enable-foreman-plugin-bootdisk \
  --enable-foreman-plugin-puppetdb \
  --foreman-environment=production \
  --foreman-db-type=postgresql
```

# Modulos do puppet a serem instalados

# Instalação do PuppetDB
```
puppet module install puppetlabs-puppetdb
```

```
puppet module install puppetlabs-puppetdb
puppet resource package puppetdb ensure=latest
puppet resource service puppetdb ensure=running enable=true
puppet resource package puppetdb-terminus ensure=latest
```
