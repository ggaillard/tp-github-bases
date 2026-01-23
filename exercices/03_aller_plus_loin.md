# Exercice 03 - Aller plus loin avec Git et GitHub

> 🚀 **Objectif** : Maîtriser les commandes avancées pour travailler efficacement en équipe et gérer son historique Git.

---

## Prérequis

Avant de commencer cet exercice, vous devez avoir :
- ✅ Complété l'exercice 01 (presentation.md)
- ✅ Créé votre dépôt personnel (exercice 02)
- ✅ Fait au moins 5 commits

---

## Partie A - Explorer l'historique comme un pro

### A1. Visualiser l'historique graphique

```bash
# Historique avec graphe des branches
git log --oneline --graph --all

# Historique avec détails des modifications
git log --stat

# Historique d'un seul fichier
git log --oneline -- exercices/01_presentation.md
```

📝 **À faire** : Exécutez ces 3 commandes et observez les différences.

**Question** : Combien de fichiers ont été modifiés dans votre dernier commit ?

> Réponse : [À compléter]

---

### A2. Voir les modifications d'un commit précis

```bash
# Trouver l'identifiant d'un commit
git log --oneline

# Voir le contenu d'un commit spécifique (remplacez abc1234)
git show abc1234
```

📝 **À faire** : Affichez le contenu de votre premier commit.

**Question** : Quel était le message de votre premier commit ?

> Réponse : [À compléter]

---

### A3. Comparer deux versions

```bash
# Voir les différences entre deux commits
git diff abc1234 def5678

# Voir les différences entre un commit et maintenant
git diff abc1234 HEAD
```

📝 **À faire** : Comparez votre premier et dernier commit.

```bash
# Commit après cet exercice
git add exercices/03_aller_plus_loin.md
git commit -m "Complétion partie A - exploration historique"
```

---

## Partie B - Annuler et corriger ses erreurs

### B1. Modifier le dernier message de commit

Vous avez fait une faute dans votre message ? Pas de panique !

```bash
# Modifier le message du DERNIER commit uniquement
git commit --amend -m "Nouveau message corrigé"
```

⚠️ **Attention** : Ne jamais utiliser `--amend` sur un commit déjà pushé !

📝 **À faire** : Créez un commit avec une faute volontaire, puis corrigez-le.

```bash
# 1. Créez un fichier test
echo "fichier test" > test_amend.txt
git add test_amend.txt
git commit -m "Ajot du fichier test"  # Faute volontaire

# 2. Corrigez le message
git commit --amend -m "Ajout du fichier test"

# 3. Vérifiez
git log -1
```

---

### B2. Retirer un fichier du staging

Vous avez fait `git add` par erreur ?

```bash
# Retirer UN fichier du staging (avant commit)
git restore --staged nom_du_fichier

# Retirer TOUS les fichiers du staging
git restore --staged .
```

📝 **À faire** : Testez cette commande.

```bash
# 1. Ajoutez un fichier au staging
echo "test" > fichier_erreur.txt
git add fichier_erreur.txt
git status  # Le fichier est en vert

# 2. Retirez-le du staging
git restore --staged fichier_erreur.txt
git status  # Le fichier est en rouge (non suivi)

# 3. Supprimez le fichier test
rm fichier_erreur.txt
```

---

### B3. Annuler les modifications d'un fichier

Vous avez modifié un fichier et voulez revenir à la version du dernier commit ?

```bash
# Annuler les modifications (ATTENTION : irréversible !)
git restore nom_du_fichier
```

⚠️ **Danger** : Cette commande supprime définitivement vos modifications non commitées !

📝 **À faire** : Testez prudemment.

```bash
# 1. Modifiez le README
echo "Ligne de test à supprimer" >> README.md
cat README.md  # Voir la modification

# 2. Annulez la modification
git restore README.md
cat README.md  # La ligne a disparu
```

```bash
# Commit après cet exercice
git add exercices/03_aller_plus_loin.md
git commit -m "Complétion partie B - annuler et corriger"
```

---

## Partie C - Les branches (introduction)

### C1. Comprendre les branches

Une branche permet de travailler sur une fonctionnalité sans affecter le code principal.

```
main:        A───B───C───D
                    \
feature:             E───F
```

```bash
# Voir toutes les branches
git branch

# Voir la branche actuelle
git branch --show-current
```

---

### C2. Créer et utiliser une branche

```bash
# Créer une nouvelle branche
git branch ma-branche

# Se déplacer sur cette branche
git switch ma-branche

# Raccourci : créer ET se déplacer
git switch -c ma-nouvelle-branche
```

📝 **À faire** : Créez une branche pour expérimenter.

```bash
# 1. Créer une branche "experimentation"
git switch -c experimentation

# 2. Vérifier qu'on est sur la bonne branche
git branch

# 3. Créer un fichier dans cette branche
echo "# Mes expérimentations" > EXPERIENCES.md
git add EXPERIENCES.md
git commit -m "Ajout fichier expérimentations"

# 4. Revenir sur main
git switch main

# 5. Vérifier que EXPERIENCES.md n'existe pas sur main
ls  # Le fichier n'apparaît pas !
```

**Question** : Pourquoi le fichier EXPERIENCES.md n'apparaît-il pas sur main ?

> Réponse : [À compléter]

---

### C3. Fusionner une branche

```bash
# Depuis main, fusionner une autre branche
git switch main
git merge experimentation
```

📝 **À faire** : Fusionnez votre branche experimentation dans main.

```bash
# 1. S'assurer d'être sur main
git switch main

# 2. Fusionner
git merge experimentation

# 3. Vérifier
ls  # EXPERIENCES.md apparaît maintenant !
git log --oneline --graph
```

---

### C4. Supprimer une branche

```bash
# Supprimer une branche locale (après fusion)
git branch -d experimentation

# Forcer la suppression (même si non fusionnée)
git branch -D nom-branche
```

```bash
# Commit après cet exercice
git add exercices/03_aller_plus_loin.md
git commit -m "Complétion partie C - introduction aux branches"
```

---

## Partie D - Collaborer avec GitHub

### D1. Le fichier .gitignore

Certains fichiers ne doivent **jamais** être versionnés :
- Fichiers de configuration locaux
- Mots de passe et clés API
- Fichiers compilés
- Dossiers node_modules, __pycache__, etc.

📝 **À faire** : Créez un fichier `.gitignore`

```bash
# Créer le fichier .gitignore
cat > .gitignore << 'EOF'
# Fichiers système
.DS_Store
Thumbs.db

# Éditeurs
.vscode/
.idea/
*.swp

# Python
__pycache__/
*.pyc
.env

# Node.js
node_modules/
npm-debug.log

# Fichiers sensibles
*.secret
*.key
passwords.txt
EOF

# Ajouter et commiter
git add .gitignore
git commit -m "Ajout du fichier .gitignore"
```

---

### D2. Les Issues GitHub

Les **Issues** permettent de :
- 🐛 Signaler des bugs
- 💡 Proposer des améliorations
- 📋 Créer une liste de tâches

📝 **À faire** : Créez une Issue sur votre dépôt GitHub.

1. Allez sur votre dépôt GitHub
2. Onglet **Issues** → **New issue**
3. Titre : "Améliorer le README"
4. Description : "Ajouter une section avec mes projets futurs"
5. Cliquez **Submit new issue**

**Astuce** : Vous pouvez fermer une issue automatiquement depuis un commit :

```bash
git commit -m "Ajout section projets futurs - Closes #1"
```

---

### D3. Synchroniser avec GitHub

```bash
# Récupérer les modifications depuis GitHub
git pull

# Envoyer vos modifications vers GitHub
git push

# Voir l'état de synchronisation
git status
```

📝 **À faire** : Synchronisez tout votre travail.

```bash
# Pousser tous vos commits
git push

# Vérifier sur GitHub que tout est à jour
```

---

### D4. Créer un bon README avec des badges

Les **badges** donnent des informations visuelles rapides.

📝 **À faire** : Ajoutez des badges à votre README.

```markdown
# Mon Portfolio BTS SIO

![GitHub last commit](https://img.shields.io/github/last-commit/VOTRE-USERNAME/VOTRE-REPO)
![GitHub repo size](https://img.shields.io/github/repo-size/VOTRE-USERNAME/VOTRE-REPO)

...
```

Remplacez `VOTRE-USERNAME` et `VOTRE-REPO` par vos informations.

**Autres badges utiles** :
- `https://img.shields.io/badge/BTS-SIO-blue` → ![BTS SIO](https://img.shields.io/badge/BTS-SIO-blue)
- `https://img.shields.io/badge/Option-SLAM-green` → ![Option SLAM](https://img.shields.io/badge/Option-SLAM-green)
- `https://img.shields.io/badge/Option-SISR-orange` → ![Option SISR](https://img.shields.io/badge/Option-SISR-orange)

```bash
# Commit final
git add .
git commit -m "Ajout badges et complétion exercice 03"
git push
```

---

## Partie E - Quiz d'auto-évaluation

Répondez sans regarder l'aide-mémoire !

### Questions

1. **Quelle commande affiche l'historique compact sur une ligne ?**
   > Réponse : [À compléter]

2. **Comment retirer un fichier du staging sans perdre les modifications ?**
   > Réponse : [À compléter]

3. **Quelle commande crée une branche ET s'y déplace en une seule fois ?**
   > Réponse : [À compléter]

4. **À quoi sert le fichier `.gitignore` ?**
   > Réponse : [À compléter]

5. **Comment fermer automatiquement une Issue GitHub depuis un commit ?**
   > Réponse : [À compléter]

6. **Quelle est la différence entre `git restore` et `git restore --staged` ?**
   > Réponse : [À compléter]

---

## 🏆 Récapitulatif des nouvelles commandes

| Commande | Description |
|----------|-------------|
| `git log --oneline --graph` | Historique graphique |
| `git show <commit>` | Détail d'un commit |
| `git diff <a> <b>` | Comparer deux commits |
| `git commit --amend` | Modifier le dernier commit |
| `git restore --staged <file>` | Retirer du staging |
| `git restore <file>` | Annuler modifications |
| `git branch` | Lister les branches |
| `git switch -c <name>` | Créer et changer de branche |
| `git merge <branch>` | Fusionner une branche |
| `git branch -d <name>` | Supprimer une branche |

---

## ✅ Checklist finale

Avant de terminer, vérifiez :

- [ ] Partie A complétée (exploration historique)
- [ ] Partie B complétée (annuler/corriger)
- [ ] Partie C complétée (branches)
- [ ] Partie D complétée (collaboration GitHub)
- [ ] Quiz rempli
- [ ] Fichier .gitignore créé
- [ ] Au moins une Issue créée sur GitHub
- [ ] Tous les commits pushés

```bash
# Vérification finale
git log --oneline  # Devrait montrer plusieurs nouveaux commits
git status         # Devrait être "nothing to commit"
```

---

## 🎯 Pour aller encore plus loin

Si vous avez terminé en avance :

1. **Explorez Git Graph** : Extension VS Code pour visualiser l'historique
2. **Créez une Pull Request** : Forkez un dépôt et proposez une modification
3. **Découvrez GitHub Actions** : Automatisez des tâches sur vos dépôts
4. **Apprenez le rebase** : Alternative au merge pour un historique linéaire

---

*Exercice complété le [date] - TP GitHub BTS SIO*
