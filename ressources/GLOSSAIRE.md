# 📖 Glossaire Git

Les termes essentiels expliqués simplement.

---

## A

### Add (git add)
**Commande** qui ajoute des fichiers à la zone de staging. C'est comme mettre des articles dans un panier avant de passer en caisse.

```bash
git add fichier.md    # Ajoute un fichier
git add .             # Ajoute tout
```

---

## B

### Branch (Branche)
Une **ligne de développement indépendante**. Permet de travailler sur une fonctionnalité sans affecter le code principal. Par défaut, vous travaillez sur la branche `main`.

> 💡 Analogie : C'est comme un brouillon parallèle de votre document.

### Bug
Une erreur dans le code. Git permet de retrouver quand et par qui un bug a été introduit.

---

## C

### Clone
**Copier un dépôt distant** vers votre ordinateur (ou Codespaces). Vous obtenez tous les fichiers ET tout l'historique.

```bash
git clone https://github.com/user/repo.git
```

### Codespaces
**Environnement de développement en ligne** fourni par GitHub. Fonctionne dans votre navigateur, pas besoin d'installer Git !

### Commit
Une **sauvegarde datée** de vos modifications avec un message explicatif. Chaque commit a un identifiant unique (ex: `abc1234`).

```bash
git commit -m "Description de mes modifications"
```

> 💡 Analogie : C'est comme faire une photo de votre projet à un instant T.

### Conflit
Situation où **deux personnes ont modifié la même partie d'un fichier**. Git ne sait pas quelle version garder et demande de choisir manuellement.

---

## D

### Diff
**Affiche les différences** entre deux versions. Montre ce qui a été ajouté (vert) et supprimé (rouge).

```bash
git diff              # Modifications non commitées
git diff --staged     # Modifications prêtes à être commitées
```

---

## F

### Fetch
**Télécharge les nouveautés** depuis GitHub sans les appliquer automatiquement (contrairement à `pull`).

### Fork
**Copie d'un dépôt** sur votre propre compte GitHub. Utilisé pour contribuer à des projets open source.

---

## G

### Git
**Logiciel de gestion de versions** créé en 2005 par Linus Torvalds (créateur de Linux). Fonctionne en local sur votre ordinateur.

### GitHub
**Plateforme web** qui héberge des dépôts Git et ajoute des fonctionnalités collaboratives (issues, pull requests, etc.).

> 💡 Git ≠ GitHub : Git est l'outil, GitHub est un service qui utilise Git.

---

## H

### HEAD
**Pointeur vers le commit actuel**. Indique "où vous êtes" dans l'historique.

### Historique
La **liste de tous les commits** d'un projet, du plus récent au plus ancien.

```bash
git log --oneline
```

---

## I

### Issue
Sur GitHub : **ticket pour signaler un bug** ou proposer une amélioration.

---

## L

### Local
Tout ce qui est **sur votre machine** (ou Codespaces), par opposition à "remote" (GitHub).

### Log
**Commande pour afficher l'historique** des commits.

```bash
git log
git log --oneline    # Version compacte
```

---

## M

### Main
**Branche principale** d'un projet (anciennement appelée "master"). C'est la version "officielle" du code.

### Merge
**Fusionner deux branches**. Combine les modifications de deux lignes de développement.

### Message (de commit)
**Texte qui décrit les modifications** d'un commit. Doit être clair et explicite !

---

## O

### Origin
**Nom par défaut** du dépôt distant (GitHub). Quand vous faites `git push origin main`, vous envoyez vers le dépôt GitHub.

---

## P

### Pull
**Télécharger et appliquer** les modifications depuis GitHub vers votre machine.

```bash
git pull
```

### Push
**Envoyer vos commits** locaux vers GitHub.

```bash
git push
```

### Pull Request (PR)
Sur GitHub : **demande de fusion** de vos modifications dans un autre dépôt ou une autre branche.

---

## R

### Remote
**Dépôt distant**, généralement sur GitHub. Votre code local peut être synchronisé avec un remote.

```bash
git remote -v    # Voir les remotes configurés
```

### Repository (Repo / Dépôt)
**Dossier de projet** géré par Git, contenant tous les fichiers ET l'historique complet.

### Reset
**Annuler des modifications**. Peut être dangereux, à utiliser avec précaution !

---

## S

### Staging Area (Zone de staging)
**Zone intermédiaire** entre vos modifications et le commit. Les fichiers ajoutés avec `git add` sont "en staging".

> 💡 Analogie : C'est le panier avant la caisse. Vous choisissez ce que vous voulez inclure dans le prochain commit.

### Status
**Commande pour voir l'état actuel** : fichiers modifiés, en staging, etc.

```bash
git status
```

---

## T

### Terminal
**Interface en ligne de commande** où vous tapez les commandes Git.

### Track (Suivre)
Un fichier est "tracké" quand Git le surveille. Les nouveaux fichiers doivent être ajoutés avec `git add` pour être trackés.

---

## V

### Version
**État d'un projet à un moment donné**. Chaque commit représente une version.

### Versioning (Gestion de versions)
**Pratique qui consiste à conserver l'historique** de toutes les modifications d'un projet.

---

## W

### Working Directory (Répertoire de travail)
Le **dossier où sont vos fichiers**. C'est ce que vous voyez dans l'explorateur de fichiers.

---

## 🗺️ Schéma récapitulatif

```
┌────────────────────────────────────────────────────────┐
│                    VOCABULAIRE GIT                      │
├────────────────────────────────────────────────────────┤
│                                                        │
│   LOCAL (votre machine)          REMOTE (GitHub)       │
│   ─────────────────────          ──────────────────    │
│                                                        │
│   Working Directory              Origin                │
│         │                           ▲                  │
│         │ git add                   │                  │
│         ▼                           │ git push         │
│   Staging Area                      │                  │
│         │                           │                  │
│         │ git commit                │                  │
│         ▼                           │                  │
│   Local Repository ─────────────────┘                  │
│   (commits, branches, HEAD)                            │
│                                                        │
└────────────────────────────────────────────────────────┘
```

---

## 📚 Pour aller plus loin

- [Documentation officielle Git](https://git-scm.com/doc) (en anglais)
- [GitHub Docs](https://docs.github.com/fr) (en français)
