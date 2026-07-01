# ☁️ Azure CLI alapműveletek

A dokumentáció az **Azure CLI** alapvető használatát, környezeti beállításait és a legfontosabb felhőalapú parancsokat mutatja be.

---

## 🔑 Első lépések:

*   **Verzió ellenőrzését így tudod ellenőrízni:** 
``` bash
  az version vagy az -v
```
*   <img width="805" height="198" alt="image" src="https://github.com/user-attachments/assets/f8ce7e35-064a-43b6-9f83-8ad25e781435" />

*   **Bejelentkezéshez ezt használd:**  
```bash
az login --tenant "TenantID" 
```
*   **Előfizetéseid így tdod ellenőrízni:** 
```bash
az account list -o table 
```
*   **Előfizetés váltásához:** 
```
az account set -s "SubscriptionID"
```

---

## 📂 Erőforráscsoportok (Resource Groups)

*   **Meglévő erőforráscsoportok listázása:** 
  ``` bash
az group list --output table
```
*   **Új erőforráscsoport létrehozása:**
  ``` bash
az group create --name "EROFORRASCSOPORT_NEVE" --location "pl: swedencentral"
```

<img width="1383" height="733" alt="image" src="https://github.com/user-attachments/assets/b421e638-37c7-41bf-9a0c-9298d73f322c" />


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
<img width="1190" height="464" alt="image" src="https://github.com/user-attachments/assets/195d49a6-6deb-4333-8a6c-f2f56a15c8e4" />

---

## 💾 Blob fájlműveletek (Feltöltés, Letöltés, Törlés)

*   **Új elem feltöltése:**
*       az storage blob upload --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM" --file "helyi_elérési_út" --auth-mode login
*   **Elemek listázása:**
*       az storage blob list --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --output table
*   **Letöltése:**
*       az storage blob download --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM" --file "helyi_cél"
*   **Törlése:**
*       az storage blob delete --container-name "TAROLO_NEVE" --account-name "TARFIok_NEVE" --name "DOKUMENTUM"
