### VLAN

- Beneficios:
	1. Dominios de difusión más pequeños
	2. Seguridad al solo los equipos en vlan puedan comunicarse
	3. Mejor rendimiento
	4. Reducción de costos
	5. Gestión simple

- Tipos 
	1. VLAN Predeterminada (VLAN 1 por default)
	2. VLAN Nativa (Viajan los datos que generan los switchs)
	3. VLAN Administrativa
	4. VLAN Datos (modo acceso)
	5. VLAN Voz

Los puertos pueden estar asignados solo a 1 vlan, excepto la vlan de voz
Los puertos en Modo Access son desde el Swtich a las pcs y permiten el paso de datos solo de 1 vlan 
Los puertos en Modo Trunk son entre Switches y se configuran para que pasen todos los datos de todas las vlans

- Comandos VLAN
	  
	Crear vlan
	`vlan _vlan-id_`
	`name _vlan name_`
	
	Asignar vlan a puerto
	`interface _interfaz_`
	`switchport mode access`
	`switchport access vlan _vlan-id_`
	
	Asignar vlan de voz y datos
	interface _interfaz_`
	`switchport mode access`
	`switchport access vlan _vlan-id_`
	`mls qos trust cos`
	`switchport voice vlan _vlan-id_ `
	
	Eliminar un puerto de una vlan
	`interface _interfaz a eliminar_`
	`no switchport access vlan`
	
	Eliminar vlan
	`no vlan _vlan-id_`
	`delete flash:vlan.dat`  elimina TODAS las vlans
	
	Vlan en modo trunk
	`interface _interfaz_`
	`switchport mode trunk`
	`switchport trunk native vlan _vlan-id_`
	`switchport trunk allowed vlan _vlan-list_`
	
	Ver configuraciones de VLAN
	`show vlan brief`




