# ☁️ Azure CLI Alapműveletek

A dokumentáció az **Azure CLI** alapvető használatát, környezeti beállításait és a legfontosabb felhőalapú parancsokat mutatja be, írja le.

---

## 🔑 Első lépések:

*   **Verzió ellenőrzését így tudod elvégezni:** `az version` vagy `az -v`
*   **Bejelentkezéshez használd ezt:** `az login --tenant "TenantID"`
*   **Előfizetéseid listázását így csináld:** `az account list -o table`
*   **Előfizetés váltásához:** `az account set -s "SubscriptionID"' `

---

## 📂 Erőforráscsoportok (Resource Groups)

*   **Meglévő erőforráscsoportok listázása:** `az group list --output table`
*   **Új erőforráscsoport létrehozása:** `az group create --name "EROFORRASCSOPORT_NEVE" --location "pl: swedencentral"`  

---

## 📦 Tárfiók (Storage Account) és Tároló (Container)

# Új tárfiók létrehozás
```bash
az storage account create --name "TARFIok_NEVE" --resource-group "EROFORRASCSOPORT_NEVE" --location "pl:swedencentral" --sku Standard_LRS
```

## Tárfiókjaid listázása
```bash
az storage account list --query "[].name" --output table
```

# Új tároló létrehozása
```bash
az storage container create --name "TAROLO_NEVE" --account-name "TARFIok_NEVE"
```

---

## 💾 Blob fájlműveletek (Feltöltés, Letöltés, Törlés)

*   **Új elem feltöltése:**
*       `az storage blob upload --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM" --file "helyi_elérési_út" --auth-mode login`
*   **Elemek listázása:**
*       `az storage blob list --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --output table`
*   **Letöltése:**
*       `az storage blob download --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM" --file "helyi_cél"`
*   **Törlése:**
*       `az storage blob delete --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM"`
