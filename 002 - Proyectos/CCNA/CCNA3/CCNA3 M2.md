- ### Configuración de OSPF

- ### Router ID de OSPF 

	Router ID con un valor en rango de 1 a 65535
	`router ospf _process-id_` 
	
	##### Orden de selección de Router ID
	1. Configurando el router-id manualmente, el id es similar a una IPv4
	   `router-id _rid_`
	1. El router elige la IP más alta de las interfaces loopback
	   `interface Loopback 1`
	   `ip address 1.1.1.1 255.255.255.255`
	3. El router elige la IP más alta de cualquier interfaz
	
	Después de agregar un router-id, el router OSPF no modificara este id hasta que se reinicie el proceso con:
	`clear ip ospf process`

- ### Redes punto a punto OSPF
	
	- #### Configurar OSPF por network 
		Se configuran todos las redes vecinas en cada R con los comandos: 
		`router ospf _process-id_`
		`network _network-address_ _wildcard-mask_ area _area-id_` 
		// El área-id por lo general será área 0
	
	- #### Configurar OSPF por interfaces
		`interface _interfaz_`
		`ip ospf _process-id_ area _area-id_``
	
	- #### Configurar interfaces pasivas
		Se configuran como pasivas interfaces conectadas hacia redes LAN
		`passive-interface _interfaz_
	
	- #### Configurar Redes OSPF punto a punto
		Cuando solo hay 2 routers no es necesario que exista BD o BDR por lo que se configura 
		`interface _interfaz_`
		`ip ospf network point-to-point`

`show ip ospf interface`

- ### Hello OSPFv2 de área única
	Los paquetes Hello se transmiten a la multicast 224.0.0.5 cada 10 segundos predeterminadamente. No se envían en las interfaces pasivas.
	
	El intervalo Dead es el tiempo de espera para un paquete Hello antes de declarar al vecino como inactivo. Si el intervalo Dead caduca OSPF elimina ese vecino de su LSDB. El R satura la LSDB con información acerca del vecino inactivo por todas las interfaces con OSPF habilitado. 
	
	Los intervalos Hello y Dead pueden configurarse por interfaz
	
	Para verificar los intervalos de la interfaz 
	`comando show ip ospf interface _interfaz_`
	  
	Para ver el intervalo Dead contando atrás desde 40 segundos
	`show ip ospf neighbor`

- ### Modifique los intervalos OSPFv2
	Los intervalos de Hello y Dead de OSPF pueden modificarse manualmente, es recomendable no poner el dead-interval 4 veces mas que el hello-interval:
	`ipospf hello-interval _segundos_`
	`ip ospf dead-interval _segundos_`
	
	Para restablecer los intervalos al valor predeterminado
	`no ip ospf hello-interval`
	`no ip ospf dead-interval`
   
- ## Propagación de la ruta predeterminada 
 
	Se crea la Ruta y se comparte //falta 
	`ip route 0.0.0.0 0.0.0.0 [next-hop-address | exit-intf]`
	`default-information originate`
	
	Para verifica usamos `show ip route` 
 
- ### Verifique OSPFv2 de área única.
	  
	`show ip interface brief` 
	Verifica que las interfaces deseadas estén activas con el 
	direccionamiento IP correcto. 
	`show ip route`
	Verifica que la tabla de enrutamiento contiene todas las rutas esperadas
	`show ip ospf neighbor`
	
	Para verificar que el router haya formado una adyacencia con los routers vecinos
	  Dos routers pueden no formar una adyacencia si: 
	  • Las máscaras de subred no coinciden, esto hace que los routers se encuentren en redes separadas.
	  • Los temporizadores de tiempo de Hello y Dead del protocolo OSPFv2 no coinciden.
	  • Los tipos de redes OSPFv2 no coinciden.
	  • Falta un comando de red OSPFv2 o es incorrecto
	`show ip protocols`
	Verificar información vital de configuración de OSPF
	`show ip ospf`
	se puede usar para examinar la ID del proceso OSPFv2 y el router ID
	`show ip ospf interface`
	Proporciona una lista detallada de cada interfaz habilitada para OSPF
	`show ip ospf interface brief`
	Para obtener un resumen rápido de las interfaces habilitadas para OSPF