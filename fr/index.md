---
layout: default
---
# Party Quest

Un framework pour des jeux de fête structurés pour enfants avec un arc narratif de quête.

## Concept

**Idée centrale :** Une série de mini-jeux reliés par une histoire, où chaque gagnant fait avancer un objectif commun (pièces de puzzle, fragments de carte, clés) menant à une récompense finale de groupe.

### Boucle principale

```
Jeu → Gagnant → Gagnant choisit un destinataire → Destinataire reçoit un jeton → Répéter
```

Après que tous les jetons sont distribués, le groupe les assemble pour débloquer le finale (trouver le trésor, ouvrir le coffre, résoudre l'énigme).

### Niveaux de complexité

| Niveau | Système de jetons | Idéal pour |
|--------|------------------|------------|
| **Simple** | Autocollants placés sur une carte pré-faite | 3–5 ans |
| **Moyen** | Pièces de puzzle gagnées par les jeux | 5–7 ans |
| **Avancé** | Pièces de puzzle + l'assemblage révèle un lieu caché | 7+ ans |

## Paramètres du framework

| Paramètre | Description | Plage |
|-----------|-------------|-------|
| Joueurs | Nombre d'enfants | 2–9 |
| Jeux | Nombre de mini-jeux (= joueurs - 1) | 1–8 |
| Jetons | Pièces de puzzle ou autocollants | = joueurs |
| Finale | Récompense de groupe | 1 |

## Navigation

| Section | Description |
|---------|-------------|
| **📖 Docs** | |
| [Design du Framework](docs/design) | Architecture, mécanique de liaison, design d'impression |
| [Catalogue de Jeux](docs/catalogue-jeux) | Collection de jeux indépendante du thème |
| [Personnalisation](docs/personnalisation) | Comment adapter le framework |
| **🎮 Exemples** | |
| [Chats & Souris](examples/chats-et-souris/) | Le chat est en vacances, les souris cherchent le fromage caché |
| **🛠️ Gabarits** | |
| [Gabarit Raquette](../templates/racket-template.html?lang=fr) | Gabarit 1:1 imprimable avec curseur de taille |
| **🌍 Langues** | |
| [Deutsch](../de/) · [English](../en/) | Autres versions linguistiques |
| [← Accueil](../) | Retour à la page d'accueil |
