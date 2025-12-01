# **Cours Git pour Débutants**

## **1. Qu’est-ce que Git ?**

Git est un **système de contrôle de version**.
Il permet de :

* Suivre les modifications de fichiers dans un projet.
* Travailler à plusieurs sur le même projet sans se marcher sur les pieds.
* Revenir à des versions précédentes si quelque chose casse.
* Gérer différentes versions du projet en parallèle (branches).

### **Différence Git vs GitHub**

* **Git** : logiciel installé sur ton ordinateur (local), qui gère les versions.
* **GitHub / GitLab / Bitbucket** : services en ligne pour héberger des projets Git et collaborer.

---

## **2. Installer Git**

### Sur Windows :

1. Télécharger Git : [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. Installer avec les options par défaut.
3. Vérifier l’installation :

```bash
git --version
```

### Sur macOS :

```bash
brew install git
git --version
```

### Sur Linux :

```bash
sudo apt update
sudo apt install git
git --version
```

---

## **3. Configurer Git**

Avant de commencer à utiliser Git, configure ton nom et ton email (utilisés dans les commits) :

```bash
git config --global user.name "Ton Nom"
git config --global user.email "ton.email@example.com"
```

Tu peux vérifier :

```bash
git config --list
```

---

## **4. Concepts de base**

### 4.1. Dépôt Git (Repository)

Un **dépôt** est un projet suivi par Git.

Deux types :

* **Local** : sur ton ordinateur.
* **Distant** : sur GitHub, GitLab, etc.

### 4.2. Étapes de Git

Git a 3 zones principales :

1. **Working Directory** (dossier de travail) : tes fichiers actuels.
2. **Staging Area** (index / zone de préparation) : fichiers prêts à être enregistrés.
3. **Repository** (dépôt local) : historique des commits.

Schéma simplifié :
              +----------------------+
              |    Dépôt distant     |
              |   (GitHub/GitLab)   |
              +----------------------+
                        ^
                        |  git push / git pull
                        |
              +----------------------+
              |   Repository local   |
              |      (commits)      |
              +----------------------+
                        ^
                        | git commit
                        |
              +----------------------+
              |    Staging Area      |
              |   (zone de préparation) |
              +----------------------+
                        ^
                        | git add
                        |
              +----------------------+
              | Working Directory    |
              |  (dossier projet)   |
              +----------------------+
---

## **5. Commandes de base**

### 5.1. Créer un dépôt

Dans un projet existant :

```bash
git init
```

* Crée un dépôt Git dans le dossier actuel.

### 5.2. Vérifier l’état

```bash
git status
```

* Montre les fichiers modifiés, ajoutés ou non suivis.

### 5.3. Ajouter des fichiers à la zone de staging

```bash
git add nom_fichier
git add .   # ajouter tous les fichiers
```

### 5.4. Faire un commit

```bash
git commit -m "Message expliquant la modification"
```

* Enregistre les modifications dans le dépôt local.

### 5.5. Voir l’historique des commits

```bash
git log
```

* Affiche la liste des commits avec leur auteur, date et message.

---

## **6. Branches**

Une **branche** est une version parallèle du projet.

* La branche par défaut s’appelle **main** ou **master**.

### Commandes utiles

* Créer une branche :

```bash
git branch nom_branche
```

* Passer sur une branche :

```bash
git checkout nom_branche
```

* Créer et passer sur une branche en même temps :

```bash
git checkout -b nom_branche
```

* Fusionner une branche dans une autre :

```bash
git checkout main
git merge nom_branche
```

---

## **7. Travailler avec un dépôt distant**

### 7.1. Ajouter un dépôt distant

```bash
git remote add origin https://github.com/utilisateur/projet.git
```

### 7.2. Envoyer les commits sur GitHub

```bash
git push -u origin main
```

### 7.3. Récupérer les modifications d’un dépôt distant

```bash
git pull
```

---

## **8. Gérer les conflits**

Quand deux personnes modifient le même fichier :

* Git ne peut pas fusionner automatiquement → **conflit**.
* Il faut ouvrir le fichier, résoudre le conflit, puis refaire un commit.

---

## **9. Bonnes pratiques**

1. Faire des commits fréquents et clairs.
2. Toujours tirer (`pull`) avant de pousser (`push`).
3. Utiliser des branches pour les nouvelles fonctionnalités.
4. Écrire des messages de commit explicites :

   ```
   git commit -m "Ajouter fonctionnalité X"
   ```
5. Ne jamais commiter des fichiers sensibles (mots de passe) → utiliser `.gitignore`.

---

## **10. Fichier `.gitignore`**

Permet d’ignorer certains fichiers ou dossiers pour ne pas les suivre avec Git.
Exemple :

```
node_modules/
.env
*.log
```

---

## **11. Résumé des commandes essentielles**

| Action                  | Commande                      |
| ----------------------- | ----------------------------- |
| Vérifier version Git    | `git --version`               |
| Initialiser dépôt       | `git init`                    |
| Vérifier statut         | `git status`                  |
| Ajouter fichiers        | `git add fichier`             |
| Commit                  | `git commit -m "message"`     |
| Voir historique         | `git log`                     |
| Créer branche           | `git branch nom_branche`      |
| Changer de branche      | `git checkout nom_branche`    |
| Créer + changer branche | `git checkout -b nom_branche` |
| Fusionner branche       | `git merge nom_branche`       |
| Ajouter dépôt distant   | `git remote add origin url`   |
| Envoyer sur distant     | `git push -u origin main`     |
| Récupérer du distant    | `git pull`                    |
