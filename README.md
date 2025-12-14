# Agent-AI-Tuto

Ce tuto à pour but d'expliquer comment construire un agent IA. 

# Installer n8n en local sur Windows

Ce guide vous explique comment installer et exécuter l'outil d'automatisation **n8n** sur votre machine Windows.

Il existe deux méthodes principales :

- **Via NPM (Node.js)** : La méthode la plus simple si vous avez déjà Node.js ou si vous voulez éviter Docker.
- **Via Docker (Recommandé)** : La méthode la plus propre et standard pour isoler l'application.

> **NOTE**  
> L'application **"n8n Desktop App"** n'est plus maintenue. Utilisez l'une des méthodes ci-dessous pour une version à jour et sécurisée.

---

## ✅ Méthode 1 : Via NPM (Node.js)

C'est souvent l'option la plus rapide pour tester.

### Prérequis
- Avoir **Node.js** installé (version 16 ou supérieure).
- Vérifiez si Node est installé en ouvrant un terminal (PowerShell ou CMD) et en tapant :
  ```bash
  node -v
  ```

### Installation
Ouvrez votre terminal (PowerShell ou Invite de commandes) et tapez :

- Pour exécuter n8n directement (sans installation permanente) :
  ```bash
  npx n8n
  ```

- Pour l'installer globalement sur votre système (recommandé pour un usage régulier) :
  ```bash
  npm install -g n8n
  ```

### Démarrage
Si vous l'avez installé globalement, lancez-le simplement avec :
```bash
n8n
```

Une fois lancé, appuyez sur **`o`** pour ouvrir le navigateur ou allez manuellement sur :
```
http://localhost:5678
```

---

## ✅ Méthode 2 : Via Docker (Recommandé)

Docker est idéal car il installe n8n dans un conteneur isolé, sans polluer votre système avec des dépendances.

### Prérequis
- Avoir **Docker Desktop** installé et lancé sur Windows.

### Installation et Démarrage
Ouvrez votre terminal (PowerShell ou Invite de commandes) et exécutez :

1. Créez un volume pour sauvegarder vos données (sinon vous perdrez vos workflows à chaque redémarrage) :
   ```bash
   docker volume create n8n_data
   ```

2. Lancez la commande suivante pour télécharger et démarrer n8n :
   ```bash
   docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n n8nio/n8n
   ```

### Accès
Ouvrez votre navigateur et allez sur :
```
http://localhost:5678
```

---

## 💾 Sauvegarder vos données
- **Avec NPM** : Les données sont stockées dans votre dossier utilisateur :
  ```
  C:\Users\VOTRE_NOM\.n8n
  ```
- **Avec Docker** : Les données sont stockées dans le volume Docker créé :
  ```
  n8n_data
  ```

---

## 🔄 Mise à jour
- **Avec NPM** :
  ```bash
  npm install -g n8n@latest
  ```

- **Avec Docker** :
  ```bash
  docker stop n8n
  docker pull n8nio/n8n
  # Relancez ensuite la commande "docker run..." ci-dessus
  ```
