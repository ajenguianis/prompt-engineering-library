# Guide d'Installation et d'Utilisation - WSL2 & Docker Engine

**Documentation Technique - Version 1.0**

---

## 📌 À propos de ce guide

Ce document détaille la procédure complète d'installation et d'utilisation de Docker Engine sous WSL2 (Windows Subsystem for Linux 2) avec stockage sur disque D:. Il est destiné à être partagé avec l'équipe de développement.

---

## 📋 Table des Matières

1. [Partie 1 : Installation](#partie-1--installation)
2. [Partie 2 : Utilisation Quotidienne](#partie-2--utilisation-quotidienne)
3. [Commandes Docker Utiles](#-commandes-docker-générales-utiles)
4. [Dépannage](#-dépannage)

---

## Partie 1 : Installation

*Cette section documente l'installation complète pour référence future.*

### Étape 1 : Activer WSL 2 et Virtual Machine Platform

Ouvrir **PowerShell en tant qu'administrateur** et exécuter les commandes suivantes :

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

> ⚠️ **Important :** Redémarrer l'ordinateur après ces commandes.

---

### Étape 2 : Installer Ubuntu 22.04 LTS

1. Ouvrir le **Microsoft Store**
2. Rechercher et installer **Ubuntu 22.04 LTS**
3. Lancer l'application Ubuntu
4. Configurer un nom d'utilisateur et un mot de passe

---

### Étape 3 : Configurer WSL 2 comme version par défaut

Dans **PowerShell (administrateur)** :

```powershell
wsl --set-default-version 2
```

Définir Ubuntu 22.04 en version 2 :

```powershell
wsl --set-version Ubuntu-22.04 2
```

> 💡 **Astuce :** Vérifier les distributions installées avec `wsl -l -v`

---

### Étape 4 : Installer Docker Engine dans WSL Ubuntu

Ouvrir l'application **Ubuntu** et exécuter :

```bash
# Mettre à jour les paquets
sudo apt update

# Télécharger et exécuter le script d'installation
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh

# Ajouter l'utilisateur au groupe docker
sudo usermod -aG docker $USER
```

> ⚠️ **Important :** Fermer et rouvrir l'application Ubuntu après cette étape pour que les changements de groupe prennent effet.

---

### Étape 5 : Installer Docker Compose

Dans l'application **Ubuntu** :

```bash
sudo apt install docker-compose-plugin
```

---

### Étape 6 : Configurer Docker pour utiliser le disque D:

**a) Arrêter le service Docker :**

```bash
sudo systemctl stop docker
```

**b) Créer le répertoire sur le disque D: :**

```bash
sudo mkdir -p /mnt/d/docker-data
```

**c) Créer/éditer le fichier de configuration :**

```bash
sudo nano /etc/docker/daemon.json
```

**d) Ajouter le contenu suivant :**

```json
{
  "data-root": "/mnt/d/docker-data"
}
```

**e) Sauvegarder et quitter :** `Ctrl+X`, puis `Y`, puis `Entrée`

**f) Redémarrer Docker :**

```bash
sudo systemctl start docker
```

**g) Vérifier le statut :**

```bash
sudo systemctl status docker
```

Le statut doit afficher `active (running)`

**h) Vérifier le changement de répertoire :**

```bash
docker info | grep "Docker Root Dir"
```

Doit afficher : `/mnt/d/docker-data`

---

### Étape 7 : Vérifier l'installation

Vérifier les versions installées :

```bash
docker --version
docker compose version
```

Lancer un conteneur de test :

```bash
docker run hello-world
```

> ✅ **Succès :** Si vous voyez le message "Hello from Docker!", l'installation est complète et fonctionnelle !

---

## Partie 2 : Utilisation Quotidienne

### 🚀 Au démarrage de votre PC

1. Ouvrir l'application **Ubuntu 22.04**
2. Démarrer le service Docker (si nécessaire) :

```bash
sudo systemctl start docker
```

> 💡 **Démarrage automatique :** Pour tenter de lancer Docker automatiquement à chaque ouverture de WSL, exécuter une seule fois :
>
> ```bash
> sudo systemctl enable docker
> ```
>
> *Note : Cela ne fonctionne pas toujours de manière fiable dans WSL, il est donc prudent de démarrer manuellement si nécessaire.*

---

### 💼 Travailler sur un projet

**1. Naviguer vers votre projet :**

```bash
cd /mnt/d/php-projects/mon-projet-php
```

**2. Lancer les services :**

- **En arrière-plan (détaché) :**
  ```bash
  docker compose up -d
  ```

- **En mode attaché (avec logs) :**
  ```bash
  docker compose up
  ```

**3. Arrêter les services :**

- **Arrêt propre (supprime les conteneurs) :**
  ```bash
  docker compose down
  ```

- **Arrêt simple (conserve les conteneurs) :**
  ```bash
  docker compose stop
  ```

**4. Redémarrer les services :**

```bash
docker compose start
```

**5. Voir l'état des conteneurs :**

```bash
docker compose ps
```

**6. Voir les logs :**

```bash
docker compose logs -f
```

*Le `-f` permet de suivre les logs en temps réel*

---

## 📚 Commandes Docker Générales Utiles

| Commande | Description |
|----------|-------------|
| `docker ps` | Lister les conteneurs en cours d'exécution |
| `docker ps -a` | Lister tous les conteneurs (actifs et arrêtés) |
| `docker images` | Lister toutes les images Docker |
| `docker volume ls` | Lister tous les volumes Docker |
| `docker system df` | Voir l'espace disque utilisé par Docker |
| `docker system prune` | Nettoyer les ressources inutilisées |

---

### 🔧 Accéder à un conteneur

Pour exécuter une commande dans un conteneur en cours d'exécution :

```bash
docker exec -it <nom_du_conteneur> bash
```

**Exemple :**

```bash
docker exec -it mon-projet-php-php-1 bash
```

> 💡 **Astuce :** Le nom exact du conteneur est donné par `docker compose ps` ou `docker ps`

---

### 🧹 Maintenance et Nettoyage

**Supprimer les conteneurs arrêtés :**

```bash
docker container prune
```

**Supprimer les images non utilisées :**

```bash
docker image prune
```

**Supprimer les volumes non utilisés :**

```bash
docker volume prune
```

**Nettoyage complet :**

```bash
docker system prune -a --volumes
```

> ⚠️ **Attention :** Cette commande supprime TOUTES les ressources non utilisées, y compris les images et volumes !

---

## 🆘 Dépannage

### Problème : Docker ne démarre pas

**Solution 1 : Vérifier le statut du service**

```bash
sudo systemctl status docker
```

**Solution 2 : Redémarrer le service**

```bash
sudo systemctl restart docker
```

**Solution 3 : Voir les logs d'erreur**

```bash
sudo journalctl -u docker.service
```

---

### Problème : Permission denied lors de l'utilisation de Docker

**Solution : Vérifier que l'utilisateur est dans le groupe docker**

```bash
groups
```

Si "docker" n'apparaît pas, exécuter :

```bash
sudo usermod -aG docker $USER
```

Puis fermer et rouvrir le terminal Ubuntu.

---

### Problème : Manque d'espace disque

**Solution : Vérifier l'utilisation et nettoyer**

```bash
docker system df
docker system prune -a
```

---

## ✅ Conclusion

Vous êtes maintenant prêt à utiliser Docker avec WSL2 !

Pour toute question ou problème, n'hésitez pas à consulter l'équipe technique.

---

**Documentation Technique** - WSL2 & Docker Engine  
*Dernière mise à jour : Décembre 2025*