# 🌐 Qu’est-ce qu’un Azure Load Balancer ?

Un **Azure Load Balancer** est un service de répartition de charge **niveau 4 (TCP/UDP)** qui distribue le trafic réseau entrant vers plusieurs ressources backend, comme des **machines virtuelles (VMs)**, en fonction de règles configurées.

Dans notre cas, nous allons créer un **Public Load Balancer** qui répartit le trafic **Internet entrant (externe)** vers les VMs.

---

## 🔁 Composants clés

### 1. Frontend IP Configuration
- IP par laquelle les utilisateurs accèdent au Load Balancer.
- Peut être **publique** (Internet) ou **privée** (interne au réseau).

### 2. Backend Pool
- Liste des ressources cibles : VMs, VM Scale Sets, adresses IP.
- Le trafic est redirigé vers ces ressources.

### 3. Health Probes
- Vérifie la **disponibilité** des instances dans le backend.
- Exemple : **sonde TCP sur le port 80**.
- Si la VM ne répond pas, elle est temporairement exclue du pool.

### 4. Load Balancing Rules
- Définissent **comment le trafic entrant est redirigé** vers les backends.
- Exemple : Requête entrante sur le **port 80** → vers le **port 80** sur les VMs du pool.

---

## ⚙️ Installation et configuration du Load Balancer

1. Rechercher dans le portail Azure le service **Load Balancer**
2. Cliquer sur **Create Load Balancer**
3. Configurer :
   - Le **nom**
   - Le **type** de Load Balancer (Public ou Internal)
4. Configurer le **Frontend IP** :
   - Créer une **nouvelle adresse IP publique**
5. Configurer le **Backend Pool** :
   - Donner un nom au backend
   - Sélectionner le **Virtual Network**
   - Associer le pool aux **VMs** ou **VM Scale Sets**
6. Configurer les **Load Balancing Rules** :
   - Définir le **nom**, le **type**, le **frontend**, le **backend pool**, les **ports**
   - Créer et associer un **Health Probe**
7. Cliquer sur **Create and Review**

---

✅ Une fois le Load Balancer créé, il commence à répartir le trafic selon la configuration définie.
