Azure CLI alapműveletek megismerése és használata

Ebben a feladatban az Azure CLI-t kell használnod.


**Jelentkezz be azure előfizetésedbe az Azure CLI segítségével**
	
	az login --tenant TENANT_ID 
	az login --tenant xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx

	Kérdést vet fel:
	Hány előfizetésem van?
	az account list -o table

	Melyiket is használjuk? - Is Default - True

	Ha váltani szeretnénk elöfizetések közöttr:
	- subsription ID-ra hivatkozunk
	az account set -s 'xxxx-xxxx-xxxx-xxxx'

	Melyik elofizetest is használjuk?
	az account show --output table


- **Hozz létre egy új erőforráscsoportot az Azure CLI segítségével**
	Két kérdés:
	1. Milyen eddigi eroforráscsoportjaim vannak:
	az group list --output table
	2. Milyen lokációk vannak?
	az account list-locations --output table
	
	az group create --name <név> --location <pl:swedencentral>

	
- **Hozz létre egy tárfiókot az erőforráscsoportban**
	Kérdés:
	Milyen típusú storage-ot hozzunk létre?
	az storage sku list --output table

	
	az storage account create --name "tarfiok neve" --resource-group "resource-group neve" --location <pl:swedencentral>  --sku "tárhely típusa"


- **Hozz létre egy tárolót a tárfiókban**
	az storage container create --name <TárolóNeve> --account-name <TárfiókodNeve>


- **Tölts fel fájlokat a tárolóba**

	az storage blob upload --container-name <TárolóNeve> --account-name <TárfiókodNeve> --name "proba.pdf" --file "fájl pontos helye pl C:\Users\ ... ..."

	ha hitelesítést kérne:
	az storage blob upload --container-name <TárolóNeve> --account-name <TárfiókodNeve> --name "proba.pdf" --file "fájl pontos helye pl C:\Users\ ... ..." --auth-mode login
	

- **Fájlok megtekintése a tárolóban**
	az storage blob list --container-name <TárolóNeve> --account-name <TárfiókodNeve> --output table


- **Fájlok letöltése a tárolóból**
	az storage blob download --container-name <TárolóNeve> --account-name <TárfiókNeve> --name <FájlNeveAzAzure-ban> --file <HelyiMentésHelyeÉsNeve>
	

- **Fájlok törlése a tárolóból**
	az storage blob delete --container-name <TárolóNeve> --account-name <TárfiókNeve> --name <FájlNeveAzAzure-ban>
