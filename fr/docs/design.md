# Design du Framework Party Quest

## Philosophie

Party Quest transforme une série de mini-jeux déconnectés en une aventure cohérente. Chaque jeu fait partie d'une histoire plus grande, ce qui maintient l'engagement des enfants entre les activités.

## Principes fondamentaux

1. **Chaque enfant gagne quelque chose** — le système « gagnant choisit le destinataire » garantit l'inclusion
2. **Progression visible** — les jetons/pièces s'accumulent visiblement
3. **Finale de groupe** — pas de gagnant unique, tous trouvent le trésor ensemble
4. **Modulaire** — les jeux sont interchangeables, le thème est un habillage

## Architecture

```
Thème (habillage narratif)
  └── Jeux (mécaniques indépendantes du thème)
       └── Boucle principale (gagnant → destinataire → jeton)
            └── Finale (assemblage collectif → récompense)
```

## Adaptabilité

- **Nombre de joueurs** : N joueurs = N-1 jeux (le dernier enfant reçoit automatiquement)
- **Durée** : ~10 min par jeu, ajustable
- **Espace** : intérieur, extérieur, ou mixte
- **Âge** : adapter la complexité des jetons (voir niveaux)
