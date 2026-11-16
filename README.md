# 🚀 Cours Git & GitHub — Ressources
 
Ressources de la formation **Git & GitHub** de la chaîne YouTube **Hamza Ma** : cours, exercices, conseils dev et infos tech, en français.
 
[![Regarder la vidéo](https://img.youtube.com/vi/KFTOCqokXI8/maxresdefault.jpg)](https://youtu.be/KFTOCqokXI8)
 
📺 **Épisode 0 : Git et GitHub, l'essentiel en moins de 10 minutes**
👉 [Regarder la vidéo sur YouTube](https://youtu.be/KFTOCqokXI8) · [Voir la chaîne](https://www.youtube.com/channel/UCuz8NyuPlJwrh3tHP7tu3tg)
 
---
 
## 📑 Sommaire
 
1. [Git ou GitHub ?](#1-git-ou-github-)
2. [Installer et configurer Git](#2-installer-et-configurer-git)
3. [Les 3 zones de Git](#3-les-3-zones-de-git)
4. [Ton premier dépôt](#4-ton-premier-dépôt)
5. [Voir l'historique](#5-voir-lhistorique)
6. [Les branches](#6-les-branches)
7. [Envoyer ton projet sur GitHub](#7-envoyer-ton-projet-sur-github)
8. [Récupérer un projet](#8-récupérer-un-projet)
9. [Le cycle de tous les jours](#9-le-cycle-de-tous-les-jours)
10. [Exercice](#-exercice)
---
 
## 1. Git ou GitHub ?
 
| | **Git** | **GitHub** |
|---|---|---|
| C'est quoi ? | Un logiciel | Un site web |
| Où ? | Sur ton ordinateur | En ligne |
| Internet ? | Pas besoin | Oui |
| Rôle | Garder l'historique de ton projet | Sauvegarder, partager, collaborer |
 
> 📸 **Git** = l'appareil photo qui prend des photos de ton projet.
> 🖼️ **GitHub** = l'album en ligne où tu les ranges et les partages.
 
---
 
## 2. Installer et configurer Git
 
- **Windows** : télécharge Git sur [git-scm.com](https://git-scm.com) et garde les options par défaut.
- **Mac** : Git est souvent déjà installé. Sinon : `xcode-select --install`.
- **Linux** : `sudo apt install git`.
```bash
# Vérifier l'installation
git --version
 
# Dire à Git qui tu es (une seule fois)
git config --global user.name "Ton Nom"
git config --global user.email "ton@email.com"
```
 
> 💡 Utilise la **même adresse e-mail** que sur ton compte GitHub.
 
---
 
## 3. Les 3 zones de Git
 
```
 ┌────────────────────┐   git add    ┌────────────────────┐  git commit  ┌────────────────────┐
 │ 1. Dossier de      │ ───────────► │ 2. Zone de         │ ───────────► │ 3. Dépôt           │
 │    travail         │              │    préparation     │              │    (historique)    │
 │  tes fichiers      │              │    (staging)       │              │    les commits     │
 └────────────────────┘              └────────────────────┘              └────────────────────┘
```
 
**À retenir : Modifier → `git add` → `git commit`**
 
---
 
## 4. Ton premier dépôt
 
```bash
cd mon-projet                        # se placer dans le dossier du projet
git init                             # créer le dépôt Git (dossier caché .git)
git status                           # voir l'état des fichiers (rouge = pas suivi)
git add .                            # ajouter tous les fichiers à la zone de préparation
git status                           # les fichiers sont en vert : prêts
git commit -m "Premier commit"       # enregistrer
```
 
> 💡 `git status` est la commande que tu utiliseras le plus. En cas de doute, tape-la !
 
---
 
## 5. Voir l'historique
 
```bash
git log               # historique détaillé (identifiant, auteur, date, message)
git log --oneline     # une ligne par commit, plus lisible
```
 
✅ Bon message : `git commit -m "Ajouter le formulaire de contact"`
❌ Mauvais message : `git commit -m "modif"`
 
---
 
## 6. Les branches
 
```bash
git branch                           # lister les branches
git switch -c nouvelle-fonction      # créer une branche et s'y placer
# ... tu modifies, git add, git commit ...
git switch main                      # revenir sur la branche principale
git merge nouvelle-fonction          # fusionner la branche dans main
git branch -d nouvelle-fonction      # supprimer la branche (optionnel)
```
 
```
main               ●───●───────────────●  (merge)
                        \             /
nouvelle-fonction        ●───●───●───
```
 
---
 
## 7. Envoyer ton projet sur GitHub
 
1. Sur GitHub : **+** → **New repository** → donne un nom → **Create repository**.
   ⚠️ Si ton projet existe déjà sur ton ordinateur, **ne coche pas** « Add a README file ».
2. Dans ton terminal :
```bash
git remote add origin https://github.com/TON-PSEUDO/TON-DEPOT.git
git branch -M main
git push -u origin main
```
 
- `origin` = le surnom du dépôt en ligne.
- `-u` mémorise le lien : les fois suivantes, un simple `git push` suffit.
---
 
## 8. Récupérer un projet
 
```bash
git clone https://github.com/TON-PSEUDO/TON-DEPOT.git   # télécharger un dépôt (fichiers + historique)
git pull                                                  # récupérer les nouveaux commits
```
 
| Commande | Sens | Rôle |
|---|---|---|
| `git push` | ⬆️ ordinateur → GitHub | Envoyer tes commits |
| `git pull` | ⬇️ GitHub → ordinateur | Récupérer les commits des autres |
 
---
 
## 9. Le cycle de tous les jours
 
```bash
git pull                         # 1. récupérer les dernières modifications
# ... tu modifies tes fichiers ...
git status                       # 2. voir ce qui a changé
git add .                        # 3. préparer
git commit -m "Message clair"    #    enregistrer
git push                         # 4. envoyer sur GitHub
```
 
> 🌿 Pour chaque nouvelle fonctionnalité : **une branche**, puis **un merge**.
 
---
 
## 🏋️ Exercice
 
Le dossier [`projet-exemple`](./projet-exemple) contient un petit site pour t'entraîner :
 
1. Télécharge le dossier `projet-exemple` (ou clone ce dépôt).
2. Dans ce dossier, lance `git init`, puis fais ton premier commit.
3. Change le titre dans `index.html` et fais un deuxième commit.
4. Crée une branche `couleur`, change la couleur dans `style.css`, commit, puis fusionne-la dans `main`.
5. Crée ton propre dépôt sur GitHub et envoie le projet avec `git push`.
6. Vérifie avec `git log --oneline` : tu dois voir au moins 3 commits.
> 💬 Tu bloques ? Écris ton erreur en commentaire sous la vidéo : la série **« Git : problèmes & solutions »** arrive bientôt !
 
---
 
## 📋 Aide-mémoire
 
| Commande | À quoi ça sert |
|---|---|
| `git init` | Créer un dépôt |
| `git status` | Voir l'état des fichiers |
| `git add .` | Préparer tous les fichiers |
| `git commit -m "..."` | Enregistrer une version |
| `git log --oneline` | Voir l'historique |
| `git switch -c nom` | Créer une branche et y aller |
| `git switch main` | Revenir sur main |
| `git merge nom` | Fusionner une branche |
| `git remote add origin URL` | Relier au dépôt GitHub |
| `git push` | Envoyer sur GitHub |
| `git pull` | Récupérer depuis GitHub |
| `git clone URL` | Télécharger un dépôt |
 
---
 
⭐ **Si ce dépôt t'aide, laisse une étoile !** Et abonne-toi à la chaîne pour ne rater aucune vidéo.
 
Fait avec ❤️ par **Hamza Ma**
 
