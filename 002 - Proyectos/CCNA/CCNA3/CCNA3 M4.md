## Conceptos de ACL

**¿Qué es una ACL?** Una ACL es una serie de comandos del IOS que controlan si un router reenvía o descarta paquetes. 
ACL es una lista secuencial de instrucciones permit (permitir) o deny (denegar), conocidas como “entradas de control de acceso” (ACE).

ACL estándar : Sólo filtran en la capa 3 utilizando únicamente la dirección IPv4 de origen. 

ACL extendidas : filtran en la capa 3 mediante la dirección IPv4 de origen y/o destino. También pueden filtrar en la Capa 4 usando TCP, puertos UDP e información de tipo de protocolo opcional.

_Las ACL no operan sobre paquetes que se originan en el router mismo._

Las ACL de entrada filtran los paquetes que ingresan a una interfaz específica antes de que se enruten a la interfaz de salida. 

ACL de salida filtran los paquetes después de que se enrutan, independientemente de la interfaz de entrada.

Pasos de como funciona una ACL:

1. Un router con una ACL estándar recupera la dirección IPv4 de origen del encabezado del paquete. 
2. El router comienza en la parte superior de la ACL y compara la dirección con cada ACE de manera secuencial. 
3. Cuando encuentra coincidencia, el router realiza la instrucción, que puede ser permitir o denegar el paquete. Las demás entradas en el ACL no son analizadas. 
4. Si la dirección IPv4 de origen no coincide con ninguna ACE de la ACL, el paquete se descarta porque hay una ACE de denegación implícita aplicada automáticamente a todas las ACL.

ACL Standar (1-99 o 1300-1999)
ACL Extendidas  (100-199 o 2000-2699)

ACL ESTANDAR (conf lo mas cerca del destino en la interfaz de salida) Bloquea el origen
ACL EXTENDIDA (conf lo mas cerca del origen en la interfaz de entrada)

#### Configuración

Para un host
`acces-list _#_ permit/deny _ip host_ 0.0.0.0`
Para una red
`acces-list _#_ permit/deny _red_ _wildcard_`
reemplaza la mascara 0.0.0.0
`host`
remplaza la mascara 255.255.255.255
`any`

- #### ACL ESTANDAR 
	
	- ACL numerada 
	`acces-list _#_ remark _descripcion_`
	`acces-list _#_ permit/deny _origen_ _wildcard_`
	
	- ACL nombrada
	`ip acces-list standard _nombre acl_`
	
	Enlazar ACL a interfaz
	`interface _interfaz_`
	`ip acces-group _#/nombre_ in/out`
	
	muestra las ACL aplicadas
	`show acces-list`
	`show run | section access-list`
	`show ip int _interface_ | include access-list`
	Limpia las estadisticas de acl mostradas en show
	`clear access-list counters` 

- #### ACL EXTENDIDA 

- ACL numerada 
`acces-list _#_ remark _descripcion_`
`acces-list _#_ permit/deny _protocol_ _origen__wildcard o_ _destino__wildcard d_ _puerto_`

- ACL nombrada
`ip acces-list extended _nombre acl_`
`remark _descripcion_`
`permit/deny _protocol_ _origen__wildcard o_ _destino__wildcard d_ _puerto_`

Permite el trafico de retorno
`established`