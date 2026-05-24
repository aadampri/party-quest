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

## Mécanique de Liaison des Jetons

La **boucle principale** est : Jeu → Gagnant → Gagnant choisit Destinataire → Destinataire reçoit Jeton → Répéter. Mais *comment* le jeton relie un enfant à la récompense finale est un choix de design avec plusieurs variantes :

### Stratégies de Liaison

| Stratégie | Quand la liaison se fait | Préparation du trésor | Idéal pour |
|-----------|--------------------------|----------------------|------------|
| **Liaison à la réception** | Le destinataire marque le jeton avec son symbole personnel à la réception | Trésors non marqués ; correspondance des symboles à la fin | Flexible — aucune préparation par enfant nécessaire |
| **Jetons pré-liés** | Les jetons sont marqués de symboles *avant* la fête | Chaque trésor est pré-étiqueté avec un symbole correspondant | Moins de travail pendant la fête ; effet de surprise |
| **Positionnel** | Jeton = pièce de puzzle ; la position sur la carte assemblée indique le trésor | Trésors cachés aux emplacements révélés par la carte | Le plus immersif ; nécessite un puzzle spatial |

### Comment ça fonctionne (détail)

```
┌─────────────────────────────────────────────────────────────┐
│              LIAISON À LA RÉCEPTION                          │
│                                                             │
│  1. L'enfant reçoit une pièce de puzzle vierge             │
│  2. L'enfant la marque avec son symbole (autocollant/dessin)│
│  3. À la finale : le puzzle assemblé révèle l'emplacement  │
│  4. Chaque enfant trouve le trésor marqué de son symbole   │
│                                                             │
│  Attribution des symboles : au début de la fête (choisir)   │
│  Préparation trésor : N trésors identiques, étiqueter à la │
│                        fin OU pré-étiqueter et associer     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│              JETONS PRÉ-LIÉS                                │
│                                                             │
│  1. Avant la fête : marquer chaque pièce avec un symbole   │
│  2. Avant la fête : marquer chaque trésor avec le symbole  │
│  3. Le destinataire reçoit une pièce au hasard (symbole =  │
│     destin)                                                 │
│  4. À la finale : l'enfant associe le symbole de sa pièce  │
│     à un trésor — « quel trésor est le TIEN ? »            │
│                                                             │
│  Pro : Zéro effort pendant la fête, surprise               │
│  Contra : Préparer N trésors distincts à l'avance          │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│              POSITIONNEL                                     │
│                                                             │
│  1. Les pièces assemblées forment une carte/image           │
│  2. La carte révèle UN emplacement commun                  │
│  3. Le groupe y va ensemble pour trouver TOUS les trésors   │
│  4. Liaison individuelle via étiquettes ou autocollants     │
│     sur chaque trésor à l'emplacement                       │
│                                                             │
│  Pro : Révélation la plus dramatique, moment de groupe fort │
│  Contra : Tous les trésors doivent être au même endroit     │
└─────────────────────────────────────────────────────────────┘
```

### Symboles plutôt que Couleurs

Utiliser des **symboles thématiques** plutôt que des couleurs pour les marqueurs personnels :
- Les couleurs semblent arbitraires et déclenchent des conflits « Je voulais le bleu ! »
- Les symboles thématiques font partie de l'histoire (types de fromage, empreintes d'animaux, icônes de planètes)
- Les symboles fonctionnent en niveaux de gris (important pour les impressions)
- Les enfants ressentent la propriété de « leur » symbole pendant toute la fête

### Exemples d'Instances

| Thème | Symboles | Stratégie de liaison |
|-------|----------|---------------------|
| Chats & Souris | Types de fromage (Emmental, Gouda, Brie…) | Liaison à la réception (autocollant sur pièce de puzzle) |
| Pirates | Variantes de crâne (chapeau, bandeau, perroquet…) | Pré-lié (pièces pré-estampillées) |
| Espace | Icônes de planètes (Saturne, Mars, Lune…) | Positionnel (carte stellaire révèle les coordonnées) |
