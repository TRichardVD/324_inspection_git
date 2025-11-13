# Challenge - Inspection et Analyse d'un Repository GIT

## Consignes générales

Ce challenge a pour but d'évaluer votre capacité à **explorer, comprendre et analyser l'historique d'un projet GIT**.

### Règles

- **Aucune interface graphique n'est autorisée**, vous devez travailler **exclusivement en ligne de commande** (sauf pour le FORK depuis Github)
- **L'utilisation d'outils d'intelligence artificielle est strictement interdite.**
- Vous pouvez utiliser la documentation à l'adresse suivante: https://git-scm.com/book/fr/v2
- **Objectif : comprendre l'évolution du code et reconstituer les décisions prises.**

## Travail à effectuer

Le dépôt d'origine à utiliser est disponible à l'adresse suivante :
```bash
https://github.com/ETML-RRY/324_inspection_git.git
```

### Partie 1 - Préparation

1. Faites un *FORK* du dépôt sur votre compte GitHub (Attention il faut copier toutes les branches donc il faut **décocher** la case "Copy the main branch only" sur l'interface de Github)
2. Ajoutez votre enseignant comme collaborateur à votre dépôt forké.
3. Vous trouverez une réplique de ces instructions dans le fichier README.md de votre dépôt.
4. Répondez directement aux questions dans le fichier README.md qui est au format **Markdown**
5. Pour chaque points, veuillez noter la ou les commandes `git` utilisées vous permettant de répondre à la question.
6. Pour chaque partie, effectuez au minimum un commit et un push lorsque vous avez complété les réponses de la partie correspondante.

> Le format Markdown: [https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/)


### Partie 2 — Exploration de base

1. Combien de branches existent dans le dépôt ? Citez-les.

```bash
$ git branch --all
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/experiment/dark-mode
  remotes/origin/feature/header
  remotes/origin/feature/login
  remotes/origin/hotfix/typo
  remotes/origin/main
```

2. Quels sont les **tags** disponibles ? A quoi correspondent-ils ?
```bash
$ git tag --list
v0.1
v0.2
```

3. Quelle est la **branche principale** du projet ?
```bash
git remote show origin | grep 'HEAD branch'
```

### Partie 3 — Historique et commits

4. Quel est le message du **premier commit** du projet ?  
```bash
$ git log --reverse
```

5. Trouvez le commit où une **clé API** a été ajoutée par erreur. Quel est son identifiant (hash court) ? 

```bash
$ git log --grep="api" -i --oneline
1b682c9 chore(config): retire la clé API et documente la bonne pratique
bea2d1a chore(config): AJOUT TEMPORAIRE d'une clé API (à retirer)

```
⇒ c'est `bea2d1aeaecd11e9c0af36cf6f052f65e82d36c5`

6. Quel commit a ensuite corrigé cette erreur ?  

=> C'est `bea2d1aeaecd11e9c0af36cf6f052f65e82d36c5` 

7. Trouvez le commit où le **titre de la page d'accueil** a été corrigé.  

```bash
$ git log --grep="titre" -i --oneline
6317c07 (origin/hotfix/typo) hotfix: corrige la typo 'Wolrd' dans le titre

```

8. Quel est le message du commit qui a **ajouté le fichier `CHANGELOG.md`** et quelle commande avez-vous utilisé ?

```bash
$ git log --grep="CHANGELOG" -i --pretty=short
commit ed62890417d8c8fb880e55a2b8933b80b00ea1bd
Author: Romain Rosay <romain.rosay@eduvaud.ch>

    docs: ajoute un changelog de base

```

### Partie 4 — Branches et fusions

9. Quelles branches ont été fusionnées dans `main` ?  

```bash
git branch --all --merged

git log --graph --oneline
```

10. Quelle branche **n'a pas été fusionnée** ? Pourquoi, selon vous ? 

```bash
git branch --all --no-merged
```

Parce que clairement on a indiqué dans le nom de la branche que c'est une "experiment". Comme le nom de la branche est "experiment/dark-mode"

### Partie 5 — Analyse du contenu

11. Quelle est la **différence principale** entre les fichiers `index.html` dans les versions `v0.1` et `v0.2` et quelle commande permet de le voir rapidement ? 
```bash
git diff v0.1 v0.2 -- index.html
```
12. Que contient la branche `feature/login` ?  
```bash
git branch -a -v
```
13. Dans quelle branche a été ajoutée le code pour le **mode sombre** ?

```bash
 git log --all --grep="sombre"
```

14. Quelle bonne pratique de sécurité est évoquée dans les commits du fichier `config.js` ?

```bash
 git log --online -- config.js
 git diff 1b682c91ef14cda333419e2e387a53033ae575a1 4d28bc59eee6c8f52277bf505642a0e8e3595674
```
On a retirer la clé API.

### Partie 6 — Réflexion

15. Pourquoi est-il important de **taguer** des versions dans un projet ? 
Cela permet d'identifier clairement les versions.
16. Que peut-on déduire du style de travail de l'équipe à partir de cet historique GIT ?  
Chauque fonctionnalité à sa branche dédié avec un préfix : `feature/` (ou pour d'autre type de `mofification experiment/`, `hotfix/` etc.) si c'est une fonctionnalité etc. Ils utilisent les convenions de commit conventionnel


Bonne chance, et surtout... **ne vous perdez pas dans le log !** 😉