### Protocolos de Redundancia de Primer Salto - FHRP

- FHRP
	Son mecanismos que proporcionan puertas de enlace predeterminadas alternativas en redes conmutadas donde 2 o más routers se conecta a una misma VLAN. (Redundancia de Gateways)
	
	## Pasos para la Conmutación por Falla del Router:	
	1. El router de reserva deja de recibir los mensajes de saludo del router de reenvío.
	2. El router de reserva asume la función del router de reenvío.
	3. Debido a que el nuevo router de reenvío asume tanto la dirección IPv4 como la dirección MAC del router virtual, los dispositivos host no perciben ninguna interrupción en el servicio.

- HSRP
	Es el protocolo FHRP exclusivo de Cisco diseñado para permitir la conmutación por falla transparente de los dispositivos IPv4 de primer salto.
	Se selecciona un dispositivo activo y un dispositivo de reserva. 
	
	Para determinar el router activo se usa un parametro de prioridad en un rango de 0-255, por defecto es 100. **El activo será el que tenga la prioridad más alta.**
	
	**Configurar HSRP en cada Router que queremos redundancia**
	
	`interface _interface_`
	interfaz donde se configurará (la que apunta a las PCs)
	`stanby version 2`
	es la version mas reciente
	`stanby 1 ip _default-gateway_`
	ponemos direccion ip virtual que queremos que conmute, el 1 es que pertenece al grupo de hsrp que queremos  
	`stanby 1 priority _0-250_`
	//definimos la prioridad, el de más alta es el activo
	`standby 1 preempt`
	/para que conmute nuevamente a un router activo anterior
	`show standby`
	muestra la info de HSRP configurada
	
	_Para que funcione la redundacia hay que colocar el ip virtual que configuramos en hsrp_






