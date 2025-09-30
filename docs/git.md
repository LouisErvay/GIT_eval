## Introduction

Ce document explique les méthodes d'utilisation de Git dans notre projet qui combine un frontend React et un backend FastAPI.

## Structure des branches

Notre projet utilise un workflow de type "feature branching" avec les branches principales suivantes :

- **dev** : Branche de développement intégrée, contenant toutes les fonctionnalités validées
- **front** : Branche dédiée au développement frontend (React).
- **core** : Branche dédiée au développement backend (FastAPI).
- **tests** : branche dédiée aux tests des features.
- **docs** : branche dédiée aux mise à jours des documentations.

## Workflow GitFlow

Nous suivons un workflow de type GitFlow adapté à notre organisation :

### Développement de nouvelles fonctionnalités

1. **Frontend** :

   - Pour ajouter une nouvelle feature React, créez une branche à partir de la branche `front`
   - Exemple : `git checkout -b feature/nouveau-composant front`

2. **Backend** :
   - Pour ajouter une nouvelle route ou fonctionnalité backend, créez une branche à partir de la branche `core`
   - Exemple : `git checkout -b feature/nouvelle-route core`

### Cycle de vie d'une fonctionnalité

1. **Création de la branche** :

   - Frontend :

     - Pour ajouter une nouvelle feature React, créez une branche à partir de la branche `front`
     - Exemple : `git checkout -b feature/nouveau-composant front`

   - Backend :
     - Pour ajouter une nouvelle route ou fonctionnalité backend, créez une branche à partir de la branche `core`
     - Exemple : `git checkout -b feature/nouvelle-route core`

2. **Développement** :

   - Effectuez vos modifications
   - Commitez régulièrement avec des messages clairs et descriptifs

   ```
   git commit -m "Description précise des modifications"
   ```

3. **Mise à jour avec la branche parent** :

   ```
   git fetch origin
   git rebase origin/branch-parent
   ```

   ou

   ```
   git merge origin/branch-parent
   ```

4. **Soumission de la fonctionnalité** :
   ```
   git push origin feature/nom-de-la-feature
   ```

## Pull Requests et Intégration

1. **Création de Pull Request** :

   - Une fois la fonctionnalité terminée, créez une Pull Request (PR) vers la branche appropriée (`front` ou `core`)
   - Décrivez clairement les modifications apportées et leur objectif

2. **Validation par le Tech Lead** :

   - Toutes les PR doivent être validées par le Tech Lead avant d'être mergées
   - Le Tech Lead vérifiera la qualité du code, les tests et la conformité aux standards du projet

3. **Merge vers la branche de développement (`dev`)** :
   - Une fois la fonctionnalité validée sur sa branche respective (`front` ou `core`), une PR doit être créée pour merger vers `dev`
   - Cette PR doit également être approuvée par le Tech Lead

## Gestion des dépendances entre fonctionnalités

Certaines fonctionnalités dépendent d'autres et ne peuvent pas être mergées tant que leurs dépendances ne sont pas finalisées.

**Procédure recommandée** :

1. Identifiez clairement les dépendances entre les fonctionnalités au début du développement
2. Mentionnez ces dépendances dans la description de votre Pull Request
3. Assurez-vous que les fonctionnalités dont dépend votre travail sont déjà mergées dans la branche cible avant de soumettre votre PR

## Bonnes pratiques

1. **Commits atomiques** :

   - Faites des commits petits et cohérents qui concernent une seule modification logique
   - Utilisez des messages clairs et descriptifs

2. **Branches à jour** :

   - Synchronisez régulièrement votre branche avec sa branche parent pour éviter les conflits majeurs
   - Résolvez les conflits rapidement

3. **Nommage des branches** :

   - Frontend : `feature/front-nom-fonctionnalite`
   - Backend : `feature/core-nom-fonctionnalite`
   - Corrections : `fix/description-du-probleme`

4. **Code review** :
   - Examinez attentivement les commentaires reçus lors des reviews
   - Répondez à tous les commentaires, soit en apportant les modifications demandées, soit en expliquant votre approche

## Résolution de problèmes courants

### Conflit lors d'un merge/rebase

- Identifiez les fichiers en conflit
  - `git status`
  - Résolvez les conflits manuellement dans les fichiers concernés
- Marquez les fichiers comme résolus
  - `git add fichiers-resolus`
- Finaliser le merge ou le rebase :
  - `git commit `
  - **ou** `git rebase --continue`

### Annuler des modifications locales

- Annuler les modifications d'un fichier spécifique
  - `git checkout -- fichier`
- Annuler toutes les modifications non commitées
  - `git reset --hard HEAD`

---

Pour toute question supplémentaire concernant le workflow Git, n'hésitez pas à contacter le Tech Lead ou à consulter cette documentation.
