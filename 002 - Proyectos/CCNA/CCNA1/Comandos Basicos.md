**Configurar nombre al dispositivo**

Switch#configure terminal  
Switch(config)**#**hostname **_[Nombre]_**

**Configuración de Mensaje del día**

Switch#configure terminal  
Switch(config)#banner motd # **Enter TEXT message** #

**No ip domain-lookup (cuando se escribe mal un commando y se queda colgado el ios)**

Switch#configure terminal  
Switch(config)no ip domain-lookup

**Ver los mensajes de log desde consola remota VTY** 

Switch# terminal monitor

**Reiniciar Dispositivo**

Switch#reload

**Configuración** **de contraseñas**

**Enable Password**

Switch#configure terminal  
Switch(config)#enable password **_[password]_**

**Enable Secret**

Switch#configure terminal  
Switch(config)#enable secret **_[password]_**

**Contraseña de Terminal**

Switch#configure terminal  
Switch(config)#line vty **0 15**   
Switch(config-line)#password **_[password]  
_**Switch(config-line)#login  
Switch(config-line)#exec-time **_[minutos] [segundos]_** por defecto viene 5 minutos  
Switch(config-line)#logging synchronous los msj no desplacen los comandos en la consola

**Contraseña de consola**

Switch#configure terminal  
Switch(config)#line console 0  
Switch(config-line)#password **_[password]  
_**Switch(config-line)#login  
Switch(config-line)#exec-time **_[minutos] [segundos]  
_**Switch(config-line)#logging synchronous

**Contraseña de consola con usuario local**

Switch(config)#line console 0  
Switch(config-line)#logical local  
Switch(config-line)#exit  
Switch(config)#username **_[user]_** password **_[password]  
_**Switch(config)#exit

**Encriptar todas las contraseñas**

Switch#configure terminal  
Switch(config)#service password-encryption

**Configuracion de SSH**

Switch>enable  
Switch#config terminal  
Switch(config)#hostname **_R1  
_**Switch(config)#ip domain-name **cisco.com  
**

Switch(config)#username **cisco** secret **cisco  
**Switch(config)#crypto key generate rsa

Switch(config)# login block-for 180 attempts 4 within 120 bloqueo por tres minutos, 4 intentos en dos minutos

Switch(config) #ip ssh version 2 (se necesita un cifrado de 768 minimo)

Switch(config)#line vty 0 15

Switch(config-line)#transport input ssh

Switch(config-line)#login local 

**Guardar Cambios**

Switch>enable  
Switch#copy running-config startup-config  
Switch#copy run start  
Switch#wr

**Eliminar configuración del switch**

Switch#erase startup-config las vlan se guardan en otro archivo  
Switch#delete flash:vlan.dat  
Switch#reload

**Configuración de interfas**

Router#configure terminal  
Router(config)#interface **_fastethernet 0/0  
_**Router(config-if)#ip address **_[dirección] [máscara]  
_**Router#config-if)#no shutdown (activa las interfaces)  
Router(config-if)#description **_[descripción]_** coloca una descripción a la interface

Router#configure terminal  
Router(config)#interface **_gigabitEthernet 0/0/0  
_**Router(config-if)#ip address **_[dirección] [máscara]  
_**Router#config-if)#no shutdown (activa las interfaces)  
Router(config-if)#description **_[descripción]_**

Router#configure terminal  
Router(config)#interface loopback **_number  
_**Router(config-if)#ip address **_[dirección] [máscara]_**