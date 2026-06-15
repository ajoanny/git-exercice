Voici un README structuré pour les élèves.

# Atelier Git — Travail collaboratif et gestion des branches

## Objectifs

À l'issue de cet atelier, vous devrez être capables de :

* Travailler à plusieurs sur un même dépôt Git
* Créer des commits de manière régulière
* Récupérer les modifications des autres membres de l'équipe
* Utiliser des branches pour isoler votre travail
* Fusionner une branche dans la branche principale

---

# Partie 1 — Travail collaboratif sans branches

## Cheat Sheet
```bash
git status #Affiche les fichiers modifiés, ajoutés ou en attente de commit.

git add .  #Ajoute tous les fichiers en staging (sélectionne les fichiers pour le prochain commit)
git commit -m "Mon message de commit" #Créer une commit avec le message "Mon message de commit"

git pull #Récupère les modifications présentes sur le dépôt distant et les intègre dans votre branche locale.

git log #Voir l'historique de la branche courante
```

## Introduction à l’exercice

Vous allez travailler sur un projet e-commerce simplifié organisé autour d’un backlog de User Stories et de tâches techniques.

L’objectif est de simuler un travail en équipe de développement logiciel, où plusieurs personnes interviennent en parallèle sur les mêmes éléments de projet.

Vous allez manipuler un dépôt Git contenant :
- un backlog de fonctionnalités (User Stories et taches techniques) backlog.md
- un fichier de sprint représentant le travail en cours sprint.md
- Les tâches sont priorisée de 1 à 3 => 1 étant plus prioritaire que 3. 
---

## Principe de l’exercice

Vous allez progressivement faire évoluer le projet en :
- sélectionnant des User Stories dans le backlog
- les ajoutant dans le sprint
- travaillant en parallèle avec les autres membres du groupe

---

## Objectif pédagogique

Cet exercice a pour but de vous faire pratiquer :
- les commits réguliers
- la synchronisation avec un dépôt distant
- le travail collaboratif sur des fichiers partagés
- la gestion de modifications concurrentes

---

## Organisation

Vous travaillez en groupes de 3 personnes sur un même repository GitHub.

Chaque membre contribue au projet en parallèle des autres.

---

## Consigne importante

Avant de commencer, il faut définir sur des conventions de nommage de commit et de description.

Travaillez de manière incrémentale :
- faites de petits commits réguliers
- synchronisez souvent votre travail
- lisez les modifications des autres avant de continuer

L’objectif n’est pas d’aller vite, mais de comprendre comment Git aide à organiser un travail collectif.

---

## Débrief (10 min)

Questions :

* Qu'est-ce qui a été simple ?
* Qu'est-ce qui a été difficile ?
* Comment vous êtes-vous organisés ?
* Quels problèmes avez-vous rencontrés ?
* Comment pourrait-on améliorer ce mode de travail ?

---

# Partie 2 — Travail avec des branches

## Cheat Sheet

### Créer une branche

```bash
git switch -c feature/us-001 #Crée une branche et s'y positionne.
git checkout -b feature/us-001 #Crée une branche et s'y positionne.

git switch main #Changer de branche
git checkout main #Changer de branche

git merge feature/us-001 #Fusionne les modifications de la branche indiquée dans la branche courante.

git branch -d feature/us-001 #Supprime une branche fusionnée.

git branch #Vérifier les branches existantes
```

---

## Exercice

Reprenez le même projet.

Cette fois-ci :

* Une User Story = une branche
* Chaque membre travaille sur sa propre branche
* Les modifications sont réalisées sur cette branche
* Une fois le travail terminé, la branche est fusionnée dans `main`

### Déroulement

1. Créez une branche pour votre User Story
2. Réalisez les modifications nécessaires
3. Faites vos commits
4. Revenez sur `main`
5. Fusionnez votre branche
6. Supprimez la branche devenue inutile
7. Recommencez avec une nouvelle User Story

---

## Débrief (10 min)

Questions :

* Qu'est-ce qui a changé par rapport à l'exercice précédent ?
* Quels avantages avez-vous observés ?
* Quels inconvénients avez-vous rencontrés ?
* Dans quels cas préféreriez-vous utiliser des branches ?

---

# Les workflows Git

## Trunk-Based Development — Description

Le Trunk-Based Development est un modèle d’organisation Git basé sur une branche principale unique et un travail très fréquent d’intégration.

C’est aujourd’hui l’un des modèles les plus utilisés dans les équipes qui livrent souvent et rapidement.

---

### Principe général

Le principe est simple :

- une branche principale unique : `main`
- des branches courtes pour les fonctionnalités (optionnelles mais fréquentes)
- des intégrations fréquentes dans `main`

---

### Schéma simplifié

```
main
 │
 ├── feature/login ───┐
 │────────────────────┘
 ├── feature/cart  ───┐
 │────────────────────┘
 │── feature/payment ─┐
 │────────────────────┘
 │
```

---
# GitFlow — Description

GitFlow est un modèle d’organisation des branches Git qui structure le développement autour de plusieurs branches ayant des rôles précis.

Il est souvent utilisé dans des projets où plusieurs versions du logiciel doivent coexister (développement, test, production).

---

## Principe général

GitFlow repose sur plusieurs types de branches :

- une branche principale de production (`main`)
- une branche d’intégration (`develop`)
- des branches de fonctionnalités (`feature/*`)
- des branches de préparation de release (`release/*`)
- des branches de correction urgente (`hotfix/*`)

---

## Schéma simplifié

```
main
 │
 ├── hotfix/urgent-bug
 │        │
 │        └─── merge ─────► main
 │
 ├──────────── release/v1.0
 │                 │
 │                 └──────► main
 │
 └──── develop
          │
          ├── feature/login
          ├── feature/cart
          └── feature/payment
```

Avantages :

* Organisation claire des versions
* Gestion facilitée des releases

Inconvénients :

* Plus complexe
* Plus de branches à maintenir

---

# Pull Requests

Une Pull Request (PR) permet de demander l'intégration d'une branche dans une autre.

Exemple :

```text
feature/us-001
      │
      ▼
Pull Request
      │
      ▼
main
```

Une Pull Request permet généralement :

* De relire le code
* De discuter des modifications
* De lancer des tests automatiques
* De valider le travail avant intégration

Étapes classiques :

1. Créer une branche
2. Réaliser les modifications
3. Pousser la branche sur GitHub
4. Ouvrir une Pull Request
5. Faire relire son travail
6. Fusionner la Pull Request

Dans de nombreuses équipes, les modifications passent systématiquement par une Pull Request avant d'être intégrées.
