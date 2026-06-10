# *Azure CLI alapműveletek megismerése és használata*

 

Az Azure elsőszámú, platform független parancssori eszköze.

Minden platfomon futtatható: Windows, MacOS, Linux, Unix, Docker


## Az Azure CLI telepítéséről itt tudhatsz meg többet:

[![Az Azure Command-Line Interface (CLI) dokumentációja](https://learn.microsoft.com/hu-hu/cli/azure/)

### Windowsra telepítem:

	https://learn.microsoft.com/hu-hu/cli/azure/install-azure-cli-windows?view=azure-cli-latest&tabs=azure-cli&pivots=msi

### macOS-re telepítem:

	https://learn.microsoft.com/hu-hu/cli/azure/install-azure-cli-macos?view=azure-cli-latest


### Ubuntu, Linux-ra telepíteném:

	https://learn.microsoft.com/hu-hu/cli/azure/install-azure-cli-linux?view=azure-cli-latest&pivots=apt


## Telepítés után az Azure verziót így ellenőrízhetjük:

	az version
vagy

	az -v


## Kapcsolódás az Azure Tenant-hoz:

Jelentkezzünk be az Azure előfizetésünkbe az alábbi módon:
	
	az login --tenant TENANT_ID 
	az login --tenant xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx




Az előfizetéseid az alábbi módon tudod ellenőrízni:

		az account list -o table

A jelenleg használatban lévőt a:

	Is Default oszlop - True értéke jelöli

	

Ha a nem megfelelő előfizetést használod, az alábbi módon tudsz váltani az előfizetések között:

 	subsription ID-ra hivatkozunk
		az account set -s 'xxxx-xxxx-xxxx-xxxx'

Előfizetésem ellenőrzését így végezheted el:

		az account show --output table




 ** Hozz létre egy új erőforráscsoportot az Azure CLI segítségével **
	Két kérdés:
1. Milyen eddigi eroforráscsoportjaim vannak:
	
		az group list --output table
	
2. Milyen lokációk vannak?
	
		az account list-locations --output table
	
		az group create --name <név> --location <pl:swedencentral>

	
**Hozz létre egy tárfiókot az erőforráscsoportban**
	Kérdés:
	Milyen típusú storage-ot hozzunk létre?
	
		az storage sku list --output table
	
	
		az storage account create --name "tarfiok neve" --resource-group "resource-group neve" --location <pl:swedencentral>  --sku "tárhely típusa"


**Hozz létre egy tárolót a tárfiókban**

		az storage container create --name <TárolóNeve> --account-name <TárfiókodNeve>


**Tölts fel fájlokat a tárolóba**

		az storage blob upload --container-name <TárolóNeve> --account-name <TárfiókodNeve> --name "proba.pdf" --file "fájl pontos helye pl C:\Users\ ... ..."

	ha hitelesítést kérne:
		az storage blob upload --container-name <TárolóNeve> --account-name <TárfiókodNeve> --name "proba.pdf" --file "fájl pontos helye pl C:\Users\ ..." --auth-mode login
	

**Fájlok megtekintése a tárolóban**

		az storage blob list --container-name <TárolóNeve> --account-name <TárfiókodNeve> --output table


**Fájlok letöltése a tárolóból**

		az storage blob download --container-name <TárolóNeve> --account-name <TárfiókNeve> --name <FájlNeveAzAzure-ban> --file <HelyiMentésHelyeÉsNeve>
	

**Fájlok törlése a tárolóból**

		az storage blob delete --container-name <TárolóNeve> --account-name <TárfiókNeve> --name <FájlNeveAzAzure-ban>
