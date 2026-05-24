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

## Structure

```
fr/
├── README.md          ← ce fichier
├── docs/
│   ├── design.md      ← philosophie du framework
│   ├── catalogue-jeux.md ← catalogue de jeux thème-indépendant
│   └── personnalisation.md ← guide d'adaptation
└── examples/
    └── chats-et-souris/  ← exemple complet thématique
```

## Démarrage rapide

1. Lire `docs/design.md` pour la philosophie
2. Parcourir `docs/catalogue-jeux.md` pour les jeux disponibles
3. Voir `examples/chats-et-souris/` pour un exemple complet
4. Utiliser `../templates/` pour les gabarits partagés
