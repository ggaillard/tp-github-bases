# 📋 Aide-mémoire Git

Les commandes essentielles pour ce TP.

---

## 🔧 Configuration (une seule fois)

```bash
# Configurer votre nom (visible dans les commits)
git config --global user.name "Prénom Nom"

# Configurer votre email
git config --global user.email "votre.email@exemple.com"

# Vérifier la configuration
git config --list
```

---

## 📊 Vérifier l'état du dépôt

```bash
# Voir l'état actuel (fichiers modifiés, en staging, etc.)
git status

# Version courte
git status -s
```

**Comprendre git status :**
- 🔴 **Rouge** = fichiers modifiés, pas encore en staging
- 🟢 **Vert** = fichiers prêts à être commités

---

## 📝 Faire un commit (sauvegarder une version)

### Étape 1 : Ajouter au staging

```bash
# Ajouter UN fichier spécifique
git add nom_du_fichier.md

# Ajouter TOUS les fichiers modifiés
git add .
```

### Étape 2 : Créer le commit

```bash
# Commit avec message
git commit -m "Description de ce que vous avez fait"
```

### Raccourci (add + commit en une commande)

```bash
# Seulement pour les fichiers DÉJÀ suivis par Git
git commit -am "Message du commit"
```

---

## 📜 Consulter l'historique

```bash
# Historique complet
git log

# Historique compact (une ligne par commit)
git log --oneline

# Historique avec graphe des branches
git log --oneline --graph

# Les 5 derniers commits
git log -5
```

---

## 🔍 Voir les modifications

```bash
# Voir ce qui a changé (avant git add)
git diff

# Voir ce qui va être commité (après git add)
git diff --staged
```

---

## 🌐 Travailler avec GitHub (remote)

```bash
# Voir les dépôts distants configurés
git remote -v

# Changer l'URL du remote
git remote set-url origin https://github.com/USERNAME/DEPOT.git

# Envoyer vos commits vers GitHub
git push

# Premier push (définit la branche par défaut)
git push -u origin main

# Récupérer les modifications depuis GitHub
git pull
```

---

## 🆘 Commandes de secours

```bash
# Annuler les modifications d'un fichier (avant git add)
git checkout -- nom_du_fichier

# Retirer un fichier du staging (après git add, avant commit)
git reset nom_du_fichier

# Modifier le dernier message de commit
git commit --amend -m "Nouveau message"
```

---

## 📊 Schéma du workflow Git

```
┌─────────────────────────────────────────────────────────────────┐
│                        VOTRE ORDINATEUR                         │
├─────────────────┬─────────────────┬─────────────────────────────┤
│  Working Dir    │  Staging Area   │     Local Repository        │
│  (vos fichiers) │  (zone de tri)  │     (historique local)      │
│                 │                 │                             │
│    [fichier]    │                 │                             │
│        │        │                 │                             │
│        ▼        │                 │                             │
│   git add ──────┼──▶ [fichier]    │                             │
│                 │        │        │                             │
│                 │        ▼        │                             │
│                 │   git commit ───┼──▶ [commit abc123]          │
│                 │                 │          │                  │
└─────────────────┴─────────────────┴──────────┼──────────────────┘
                                               │
                                          git push
                                               │
                                               ▼
┌─────────────────────────────────────────────────────────────────┐
│                          GITHUB                                 │
│                   Remote Repository                             │
│                                                                 │
│                    [commit abc123]                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## ✅ Checklist du bon commit

Avant chaque commit, vérifiez :

- [ ] J'ai sauvegardé mes fichiers dans l'éditeur
- [ ] `git status` montre les bons fichiers
- [ ] Mon message décrit ce que j'ai fait
- [ ] Mon message est en français et compréhensible

### Exemples de bons messages

| ✅ Bon message | ❌ Mauvais message |
|----------------|-------------------|
| "Ajout de la section parcours scolaire" | "update" |
| "Correction de la faute dans le titre" | "fix" |
| "Complétion des informations personnelles" | "modif" |
| "Ajout du README de présentation" | "readme" |

---

## 🔑 Résumé : les 4 commandes essentielles

1. `git status` → Voir où j'en suis
2. `git add` → Sélectionner les fichiers
3. `git commit -m` → Sauvegarder une version
4. `git push` → Envoyer sur GitHub
