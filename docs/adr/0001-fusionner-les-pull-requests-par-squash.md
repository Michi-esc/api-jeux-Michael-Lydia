# 1. Fusionner les Pull Requests par squash

- **Date** : 2026-10-07
- **Statut** : Proposée

## Contexte

L'équipe collabore sur plusieurs branches de fonctionnalités et de correctifs (comme la PR #6 des statistiques du catalogue). Au cours du développement, les branches de travail accumulent des commits intermédiaires, des essais ou des corrections de linting. Sans convention claire, la branche principale `main` devient difficile à lire et à maintenir. L'équipe doit donc définir une méthode de fusion standardisée sur GitHub pour intégrer les modifications.

## Options envisagées

1. **Merge commit (Créer un commit de fusion).**
   - *Pour* : Préserve l'intégralité de l'historique et la chronologie précise de tous les commits d'une branche.
   - *Contre* : Pollue l'historique de `main` avec des commits intermédiaires sans valeur ajoutée ("fix typo", "wip") et génère un graphe de branches complexe.

2. **Rebase and merge (Rebaser et fusionner).**
   - *Pour* : Conserve un historique parfaitement linéaire sans commit de fusion parasite.
   - *Contre* : Conserve chaque commit individuel même mineur, réécrit les empreintes SHA-1 et complique la résolution des conflits qui doit se faire commit par commit.

3. **Squash and merge (Écraser et fusionner).**
   - *Pour* : Condense l'ensemble des commits de la PR en un unique commit atomique sur `main`, génère un message clair référençant la PR (ex: `#6`), et simplifie grandement les retours en arrière (`git revert`) ou la recherche de bugs (`git bisect`).
   - *Contre* : Fait perdre la granularité et les étapes chronologiques détaillées du développement au sein de la branche.

## Décision

Toutes les Pull Requests vers la branche `main` sont fusionnées en utilisant la méthode **Squash and merge**.

## Conséquences

- L'historique de la branche `main` reste propre, linéaire et lisible : chaque commit correspond à une unité logique complète (une fonctionnalité ou un correctif).
- Les détails et micro-commits réalisés pendant le développement sur la branche ne sont plus visibles dans l'historique de `main`.
- À revoir si l'équipe développe des fonctionnalités très volumineuses nécessitant de conserver plusieurs sous-étapes significatives et autonomes dans l'historique principal.
