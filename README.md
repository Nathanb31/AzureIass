# 🌐 Formation Azure - Guide d'installation & premières commandes

## 🔗 Accès au Portail Azure

- **URL :** [https://portal.azure.com/#home](https://portal.azure.com/#home)  
- **Utilisateur :** `training-user-15@soatformation.onmicrosoft.com`

---

## 🛠️ Installation du client Azure pour PowerShell

### 1. Lancer PowerShell en tant qu'administrateur

Autoriser l'exécution de scripts :

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### 2. Installer et mettre à jour le module Azure PowerShell

```powershell
Install-Module -Name Az -Repository PSGallery -Force
Update-Module -Name Az -Force
```

> 💡 Cela active les commandes Azure PowerShell (`Connect-AzAccount`, etc.), **différentes** des commandes AZ CLI utilisées sur Linux ou CMD.

---

## 🔧 Installation de l’interface AZ CLI

- **Téléchargement :** [https://aka.ms/installazurecliwindowsx64](https://aka.ms/installazurecliwindowsx64)

> Cela permet d’utiliser des commandes comme `az login`, `az provider list`, etc.

---

## 🔐 Connexion à Azure

### Avec PowerShell

```powershell
Connect-AzAccount -UseDeviceAuthentication
```

### Avec AZ CLI

```bash
az login --use-device-code
```

---

## 🔍 Vérifier la connexion actuelle

```bash
az account show
```

Affiche l’état de connexion et les informations du compte.

---

## 📚 Commandes & ressources utiles

- **Commandes AZ CLI :**  
  [https://learn.microsoft.com/en-us/cli/azure/reference-index?view=azure-cli-latest](https://learn.microsoft.com/en-us/cli/azure/reference-index?view=azure-cli-latest)

- **Commandes PowerShell (exemple) :**

```powershell
Get-Help Get-AzVM -Full
```

- **Templates de déploiement Azure :**  
  [https://github.com/renauddahou/azure-quickstart-templates](https://github.com/renauddahou/azure-quickstart-templates)

---

## 💻 Utilisation de Microsoft Azure

Deux méthodes principales :

- **Console Web**
- **Ligne de commande** (PowerShell ou AZ CLI)

---

## ⚙️ Création de ressources Azure

### Exemple : création d’un groupe de ressources

```bash
az group create --name training-Beauquier-rg2 --location westeurope
```

---

## 🧮 Utilisation de variables dans PowerShell

Définir des variables pour les réutiliser plus facilement :

```powershell
$RESOURCE_GROUP = "training-Beauquier-rg"
$AVAILABILITY_SET_NAME = "MyAvailabilitySet"
$LOCATION = "westeurope"
$AZUREUSER = "azureuser"
```

Afficher toutes les variables :

```powershell
Get-Variable
```

---

## 🚀 Création d'une machine virtuelle

### En ligne de commande :

```bash
az vm create \
  --resource-group $RESOURCE_GROUP \
  --name MyVM \
  --image Ubuntu2204 \
  --admin-username $AZUREUSER \
  --generate-ssh-keys
```

---

## 🔐 Connexion SSH à la VM

### Étapes : 
Quand on utilise --generate-ssh-keys , Azure stock la clé public et privé dans c:/users/nathan/.ssh

### En ligne de commande :
On peut donc ce connecter directement a la vm par le biais de cette commande par exemple :
```bash
  ssh -i ~/.ssh/id_rsa.pem azureuser@IPPUBLICVM
```

1. **Télécharger Putty** :  
   [https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

2. **Récupérer la clé publique générée** (lors de la création de la VM)

3. **Utiliser Putty** avec la **clé privée** de votre machine pour vous connecter à la VM

---


> 🧠 Pensez à bien configurer votre groupe de sécurité réseau pour autoriser la connexion SSH (port 22).
