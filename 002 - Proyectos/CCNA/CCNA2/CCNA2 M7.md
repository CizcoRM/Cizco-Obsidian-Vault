### [[DHCPv4]] 

- Servidor-Cliente
	El servidor (escalable y fácil de administrar) asigna direcciones ip dinámicas y otra información de la red durante un periodo limitado designado a los clientes.

	Pasos para arrendamiento de IP:
	1. DHCP Discover - Detección del cliente por msj de difusión capa 2
	2. DHCP Offer - Oferta del servidor al recibir el msj de cliente, crear ARP y envía mensaje de oferta
	3. DHCP Request - Solicitud. Cliente envía un msj de difusión con la aceptación de la por si existe otra oferta.
	4. DHCP Pack - Servidor verifica el request,  hace ping ICMP para verficar que este libre y manda msj Pack, cliente recibe y busca ARP para verificar que no hay respuesta y usar la ip como propia.

	Pasos para Renovar IP:
	1. DHCP Request al servidor que arrienda, en caso que no responda se envía a otro servidor
	2. DHCP Pack - Servidor verifica la info de la request y devuelve el DHCP Pack.

-  Servidor Cisco IOS DHCPv4
	1. Excluir direcciones IPv4  
	`ip dhcp excluded-address _low-address high-address_` 
	1. Defina un nombre de grupo DHCPv4. 
	`ip dhcp pool _pool-name_`
	3. Configure el grupo DHCPv4 
	`ip dhcp pool _pool-name_`
	`network _network-number_ [mask | / prefix-length]`
	`default-router _address_ [ address2….address8]`
	`dns-server _address_ [ address2…address8]`
	`domain-name _domain_`
	`lease {days [hours [ minutes]] | infinite}`
	`netbios-name-server _address_ [ address2…address8]`

- Comandos de verificación DHCPv4
	`show running-config | section dhcp` 
	Muestra los comandos DHCPv4 configurados en el router.
	`show ip dhcp binding`
	Muestra una lista clientes y sus direcciones MAC proporcionados por el servicio DHCPv4.
	`show ip dhcp server statistics`
	Muestra información de conteo con respecto a la cantidad de mensajes DHCPv4 que han sido enviados y recibidos.
	`no service dhcp` 
	Desactivar DHCP
	`service dhcp`
	Activar DHCP
	`interface _interface que retransmitira_`
	`ip helper-address _address_`
	Retransmitir DHCP de una LAN a un servidor

- Configurar un router como cliente DHCPv4
	`interface _interface_`
	`ip address dhcp`
	`no shutdown`







