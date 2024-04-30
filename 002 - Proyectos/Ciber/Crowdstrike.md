Crowdstrike

Todo lo necesario para la instalación del agente/sensor de Falcon Crowdstrike  

En este primer ZIP, encontraran el agente para varios S.O
Linux, Debian, Ubuntu, Windows junto a ellos, encontraran en un TXT el Customer ID lo cual es un código que se debe de colocar para que el sensor pueda funcionar.

https://www.youtube.com/watch?v=DNA4SKIaa98
Este es un video oficial de crowdstrike donde muestra como es la instalación en varios kernel de Linux, Con Windows no hay pierde es arrancar el .exe, poner el CID (customer ID) y siguiente hasta terminar y queda ok.

En caso de tener AV en windows deben de colocarse estas exclusiones en instalacion de Falcon:

	Exclusiones en AV tradicionales para la instalacion de Falcon
	
	C:\Program Files\CSInstallTemp\*
	
	C:\Program Files (x86)\CSInstallTemp\*
	
	C:\Program Files\CrowdStrike\*
	
	C:\Windows\System32\Drivers\CrowdStrike\*
	
	*\CSFalconServiceUninstallTool_x64.exe
	
	C:\Users\All Users\Package Cache\*\CSFalconServiceUninstallTool_64.exe
	
	C:\ProgramData\Package Cache\*\CSFalconServiceUninstallTool_64.exe

Estas url deben de tener salida para que el sensor funcione también (ya sea firewall o proxy)

https://ts01-gyr-maverick.cloudsink.net

https://lfodown01-gyr-maverick.cloudsink.net

https://lfoup01-gyr-maverick.cloudsink.net