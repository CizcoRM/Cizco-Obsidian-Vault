### Inter-VLAN

- Enrutamiento entre VLAN heredado: Se tenia una 1 interfaz del router dedicada a cada vlan
- Router-on-a-stick: Se utilizan subinterfaces
- Switch capa 3: Se utilizan Interfaces Virtuales SVI paras las vlans

- Router-on-a-stick	  
	Configurar Inter-vlan en router
	`interface _interfaz.subinterfaz_`
	`description _descripción_`
	`encapsulation dot1q _numero de subinterfaz_`
	`ip address _gateway de vlan_ _mask_`
	
	VLAN nativa
	`interface _interfaz.subinterfaz_`
	`encapsulation dot1q _numero de subinterfaz_ native`
	`ip address _gateway de vlan_ _mask_`
	
	Levantar la interfaz donde estan las subinterfaces
	`interface _interfaz_`
	`no shut` 

 - En Switch capa 3
	`interface _vlan-id_`
	`ip address _gateway de vlan_ _mask_`
	`no shut`
	Para que el switch funcione como router
	`ip routing`