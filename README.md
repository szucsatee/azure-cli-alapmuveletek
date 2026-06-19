# ☁️ Azure CLI Alapműveletek

Ez a dokumentáció az **Azure CLI** alapvető használatát, környezeti beállításait és a legfontosabb felhőalapú parancsokat mutatja be.

---

## 🔑 Első lépések & Hitelesítés

*   **Verzió ellenőrzése:** `az version` vagy `az -v`
*   **Bejelentkezés:** `az login --tenant "TenantID"`
*   **Előfizetések listázása:** `az account list -o table`
*   **Előfizetés váltása:** `az account set -s ' "SubscriptionID"'`

---

## 📂 Erőforráscsoportok (Resource Groups)

*   **Meglévők istázás:** `az group list --output table`
*   **Létrehozás:** `az group create --name "EROFORRASCSOPORT_NEVE" --location "pl: swedencentral"`

---

## 📦 Tárfiók (Storage Account) és Tároló (Container)

# Tárfiók létrehozása
```bash
az storage account create --name "TARFIok_NEVE" --resource-group "EROFORRASCSOPORT_NEVE" --location "pl:swedencentral" --sku Standard_LRS
```
# Tároló létrehozása
```bash
az storage container create --name "TAROLO_NEVE" --account-name "TARFIok_NEVE"
```

---

## 💾 Blob fájlműveletek (Feltöltés, Letöltés, Törlés)

*   **Feltöltés:**
*       `az storage blob upload --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM" --file "helyi_elérési_út" --auth-mode login`
*   **Listázás:**
*       `az storage blob list --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --output table`
*   **Letöltés:**
*       `az storage blob download --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM" --file "helyi_cél"`
*   **Törlés:**
*       `az storage blob delete --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM"`
