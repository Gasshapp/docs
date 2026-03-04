 # Syncro

> Moteur de disponibilité basé sur le consentement. Tu possèdes ton temps — les autres ne voient que ce que tu leur permets.

Syncro s'adresse aux personnes qui jonglent entre plusieurs sphères de vie (école, travail, famille). Il protège ton temps sans te rendre opaque à ton entourage.

---

## Concepts clés

### Tags — les lentilles contextuelles
Tu segmentes ta vie en tags : **Work**, **School**, **Personal**… Chaque tag a sa couleur et son icône. Le calendrier change visuellement selon le contexte actif.


Tu peux accorder des droits de visibilité **par tag** à chaque contact : ton collègue voit tes réunions pro mais pas ta vie perso.
Chaque Tag sont trié en fonction de la confiance à laquelle on lui donne, certain peuvent être a niveau égal. Si on appartient à un groupe avec un certain tag, les autres personnes de ce groupe peuvent voir notre occupation pour les groupes auquel on n'appartient avec un tag inférieur.

### Hiérarchie de groupes
Les groupes sont imbriqués : École → Promo → Classe.

- Un événement en "Classe de Maths" remonte en **"Occupé"** pour les membres de la Promo ou de l'École — sans le détail.
- Un groupe peut être **privé par défaut** : même un contact de confiance ou un groupe parent ne voit que "Occupé" pour les événements de ce groupe.

### Création d'un event
Avant de choisir une date, le créateur de l'event peut voir une heatmap des disponibilité pour choisir une date avec le plus de personne possible disponible.

### Moteur de confiance & masquage
La confidentialité n'est pas binaire. Pour chaque contact, groupe ou event, tu choisis un niveau :

| Niveau         | Ce que l'autre voit                           |
| -------------- | --------------------------------------------- |
| **Full Trust** | Tout — titres, détails, heures exactes        |
| **Contextual** | Seulement les tags que tu lui accordes        |
| **Masked**     | "Occupé" — sans détail                        |
| **Full Ghost** | Tu apparais disponible même si tu as un event |

Le **Visibility Resolver** calcule automatiquement ce que chaque personne voit.

### Fuzzy Timing
Pour éviter le "pattern stalking", les horaires affichés aux autres peuvent être légèrement décalés (zone tampon ou jitter aléatoire).

### Decision Inbox
Toutes les invitations, demandes de planification et alertes d'urgence sont centralisées dans un seul endroit. Les demandes "critiques" peuvent passer le mode focus.

### Invités vérifiés
Tu peux inviter des personnes sans compte via un lien email sécurisé. Ils peuvent RSVP sans créer de compte. Leurs données sont auto-purgées quand elles ne sont plus utiles.

---

## Voir aussi
- [[Pages|Écrans à concevoir]]
