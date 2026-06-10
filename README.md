# Azure CLI alapműveletek megismerése és használata

[![Azure CLI](https://shields.io)](https://learn.microsoft.com/hu-hu/cli/azure/)

Ez a repository az Azure CLI alapvető használatát és legfontosabb parancsait mutatja be.

## 🚀 Támogatott platformok
Windows, macOS, Linux/Unix és Docker.

---

## 📥 Telepítési útmutatók
Részletes útmutatók a [Microsoft Learn](https://learn.microsoft.com/hu-hu/cli/azure/install-azure-cli?view=azure-cli-latest) oldalán érhetőek el.
Telepítés után verzióellenőrzés:
```bash
az version
```

---

## 🔐 Hitelesítés és Előfizetések
*   **Bejelentkezés:** `az login --tenant TENANT_ID`
*   **Előfizetések listázása:** `az account list -o table`
*   **Váltás előfizetésre:** `az account set -s 'SUBSCRIPTION_ID'`
*   **Aktuális fiók:** `az account show --output table`

---

## 🏗️ Erőforráscsoportok (Resource Groups)
*   **Lista:** `az group list --output table`
*   **Létrehozás:** `az group create --name <név> --location <régió>`

---

## 📦 Tárfiók és Tárolók (Storage Account & Containers)
*   **Tárfiók létrehozása:**
    ```bash
    az storage account create --name <tárfiók_neve> --resource-group <rg_neve> --location <régió> --sku <típus>
    ```
*   **Tároló létrehozása:** `az storage container create --name <név> --account-name <tárfiók>`
*   **Fájl feltöltése:** `az storage blob upload --container-name <tároló> --account-name <tárfiók> --name <fájlnév> --file <helyi_útvonal>`
*   **Listázás:** `az storage blob list --container-name <tároló> --account-name <tárfiók> --output table`
*   **Törlés:** `az storage blob delete --container-name <tároló> --account-name <tárfiók> --name <fájlnév>`
