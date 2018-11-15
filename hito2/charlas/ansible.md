## Provisionamiento con Ansible

Estanos puldando un botn, se encarga de MV una vez que ya las tengamos, un pequeño boton que se llama aProvisionamiento
Esta funcionando esa maquina virtual y queremos echar a andar unos servicios

EJ: echar a andar un servidor web en un sistema, ansible, te configura el servidor APache y te lo lanza

1. Consigue maquina virtual
- Trabajamos con maquinas virtuales locales (ssh)
-Vamos a trabajar con Vagrant
- Muy facil cambiar la configuracion de virtual box en local, para trabajr luego en la nube
 Vagrant.configure("2") do |config|
  config.mv.box = "debian/jessie64"
end
(en la debian jessie tienes instalado ya python)
- Vagran se complementa muy bien con ansible
- Ansible esta escrito en Python


Tiene una cierta parte que está creado como biblioteca

Es muy facil instalar ansible --> Ansible no requiere que haya nada instalado en la cual vamos a trabajar --> sino está python instslado la primera vez que acceder, se te instala automaticamente

2. Cofiguracion basica ansible.cfg
Vamos a crea run fichero de configuracion
Lo vamos a meter en el directori en el que vamos a trabajar

[defaults]
hots_key_checking = False // permite que ssh no haga esa comprobacion de claves, permitiendo entrar a otras maquinas con diferente MAC
inventory = ./ansible_hosts // nombre del fichero de hosts, en el cual vas a trabajar y definir las maquinas en las que Estanos

3. Inventariando los hosts
El fichero tiene un formato como el siguiente

1 parte : asigna el nombre a la maquina y configur aun pa de cosas
[vagrantboxes]
jessie ansible_ssh_port=2222 ansible_ssh_host=127.0.0.1
vamos a acceder por puerto 2222, a la de la maquina estamos accediendi
el host a que maquina queremos acceder
// podemos meter todas las maquinas virtuales que queramos

[vagrantboxes:vars] // si se refiere a una sola MV
Vagrant te genera una Mv y te genera una clave privada --> mete la clave privada
ansible_ssh_user=vagrant
ansible_ssh_private_key_file

// Todo esto es paraq ue se puede conectar a la maquina por el puesto SSG

4. Comprobamos basicos

ansible all -m ping // comprobar que tenemos acceso con nuestras credenciales
// ansible all // vamos a trabajar con todas las maqinas virtuales definidas en el fichero hosts
ansible all -m ping -vvv // si añadimos v te va diciendo lo que hacemos --> para depurar la conexion

Ansible se esta conectando a la MV, esta ejecutando algo en esa MV y esta capturando el momento.

Para trabajar con muchas MV a la vez

Estamos definiendo otras MVs:

Vagrant.configure("2") do |config|
  config.vm.define "m1" do |m1|
    m1.mv.box = "debian/jessie64"
  end
end

5. Ahora tenemos que configurar de nuevo

[vagrantboxes]
jessie
m1
m2

Todas las maquinas utilizan el mismo puerto? No,

Hay que cambiar la configuracion

Cada maquina va a tener su propia claves

[vagrantboxes:vars]
ansible_ssh_host=127.0.0.1
ansible_ssh_user= vagrant


ansible jessie -a "ls a" // ejecta la orden solo en jessie


6. Asible provisiona --> descirbir con docigo lo que queremos instalar

Se usar playbook

--- dice que e suna pagina

- hosts: all // - array
  become:yes // si vamos a necesitar privilegios de superusuario
  tasks: // el estado que tiene que alcanzar la maquina sobre la que va a instalar
    - name: Instala git
      apt: pkg = git state=present  // queremos que el paquete git este en un estado presente

Para alcanzar
ansible-playbokk basico.yaml // lo estoy instalando en las tres maquinas

No esta diciendo que instale apt, sino que este presente. HAy dos tipos de herramientas de Provisionamiento:
proceduraleS: dicen loas pasos a seguir
no proceduraleS: el estado que queremos conseguir

SO que trabajan bien: Ubuntu, debian

¿Por qué no usar script?


7. Instalando gemas

-hots: jessie // y no all
become : yes
tasks:
  - name:Instala Ruby
  apt: pkg=ruby-full state=present
  - name: Instala sinatra
    apt: pkg=ruby-sinatra state=present
    - gem
      name: httparty // instaar una gema que es hhtparty la ultima version
      state: latest

8. Adonde ir desde aqui

- Roles:
- Plantillas Jinja
-Orquetsacion con vagrant
-


Infraestructira como código
