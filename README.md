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

5. Trouvez le commit où une **clé API** a été ajoutée par erreur. Quel est son identifiant (hash court) ? 

6. Quel commit a ensuite corrigé cette erreur ?  

7. Trouvez le commit où le **titre de la page d'accueil** a été corrigé.  

8. Quel est le message du commit qui a **ajouté le fichier `CHANGELOG.md`** et quelle commande avez-vous utilisé ?

### Partie 4 — Branches et fusions

9. Quelles branches ont été fusionnées dans `main` ?  
10. Quelle branche **n'a pas été fusionnée** ? Pourquoi, selon vous ? 

### Partie 5 — Analyse du contenu

11. Quelle est la **différence principale** entre les fichiers `index.html` dans les versions `v0.1` et `v0.2` et quelle commande permet de le voir rapidement ?  
12. Que contient la branche `feature/login` ?  
13. Dans quelle branche a été ajouté le code pour le **mode sombre** ?  
14. Quelle bonne pratique de sécurité est évoquée dans les commits du fichier `config.js` ?

### Partie 6 — Réflexion

15. Pourquoi est-il important de **taguer** des versions dans un projet ?  
16. Que peut-on déduire du style de travail de l'équipe à partir de cet historique GIT ?  

Bonne chance, et surtout... **ne vous perdez pas dans le log !** 😉