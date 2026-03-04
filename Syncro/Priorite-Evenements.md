# Priorité & affichage des événements

## Problème

Un utilisateur peut avoir beaucoup d'événements sur une journée ou une semaine. Si tout s'affiche avec le même poids visuel, rien ne ressort. L'œil ne sait pas où aller.

Il faut un système qui **monte automatiquement ce qui compte le plus**, en tenant compte de deux dimensions :
- **L'importance** de l'événement (son groupe, son contexte)
- **La proximité temporelle** (dans combien de temps il arrive)

---

## Les deux axes de priorité

### 1. Importance — le poids du groupe

Tous les événements ne se valent pas. Un événement appartient toujours à un contexte (un tag, un groupe). Ce contexte détermine son "poids" de base.

**Facteurs qui augmentent l'importance :**
- Le groupe impliqué est **large** (beaucoup de membres) → réunion d'école entière > réunion de classe
- Le groupe est **haut dans la hiérarchie** → un événement au niveau "École" pèse plus qu'un événement au niveau "Classe de Maths"
- Le nombre de **participants confirmés** est élevé
- L'événement est marqué comme **critique** par l'organisateur 
- C'est un événement **avec des invités extérieurs** (contexte pro, formel)

**Héritage et override de l'importance :**
Un événement hérite par défaut de l'importance définie sur son groupe. Deux niveaux peuvent l'écraser :
- Le **créateur de l'événement** peut définir une importance spécifique à la création
- Le **participant** peut personnellement booster ou rétrograder un événement pour lui-même, sans affecter les autres

**Facteurs qui réduisent l'importance :**
- Événement personnel sans participants
- Groupe privé ou silencieux (la personne a choisi de le déprioritiser)
- Rappel / bloqueur léger

### 2. Proximité — l'urgence temporelle

L'importance d'un événement **grandit à mesure qu'il approche**. Un événement important dans 3 semaines pèse moins qu'un événement moyen dans 2 heures.

```
Maintenant ──────────────────────────────→ Futur

  [🔴 Urgent]   [🟠 Proche]   [🟡 Cette semaine]   [⚪ Plus tard]
   < 2h           < 24h           < 7j                > 7j
```

Le score de priorité d'un événement combine les deux :

```
Priorité = Importance × Coefficient de proximité
```

Le coefficient de proximité augmente exponentiellement à l'approche de l'événement — un événement dans 1h "pèse" beaucoup plus qu'un événement dans 2 jours, même si ce dernier est objectivement plus important.

---

## Affichage : Visual Gravity

L'idée est que les événements prioritaires **prennent plus de place visuelle** et sont **stylisés différemment** dans le calendrier. Les événements secondaires sont discrets mais présents.

### Dans la vue Calendrier (Jour / Semaine)

| Niveau | Style visuel |
|--------|-------------|
| **Critique / imminent** | Bloc plus haut, couleur saturée, bordure marquée |
| **Important** | Taille normale, couleur pleine |
| **Standard** | Taille compacte, couleur atténuée |
| **Secondaire** | Ligne fine, texte grisé, rétractable |

Quand le calendrier est **dense**, les événements secondaires peuvent être **regroupés** en un bloc compact ("3 événements mineurs") pour ne pas noyer les prioritaires, ou regroupé par groupe ("3 événements de Work").

### La Focus List

En parallèle du calendrier, une **Focus List** affiche les N événements les plus prioritaires de la journée / semaine, indépendamment de leur position dans le temps.

- Triée par score (importance × proximité)
- Se met à jour en temps réel au fil de la journée
- Un événement disparaît de la liste une fois passé
- Affichée / cachée via un **bouton dédié** — pas visible en permanence pour ne pas encombrer l'interface

## Événements récurrents

Une occurrence récurrente **hérite du score de la série** par défaut. Mais chaque occurrence peut être modifiée indépendamment — si une réunion hebdomadaire est exceptionnellement critique cette semaine, on peut la booster sans toucher aux suivantes.

---

## Cas concrets

**Scénario 1 — Journée chargée**
> Tu as 8 événements ce jour. Une réunion de promo (50 personnes) dans 3h, 5 réunions de petits groupes, et 2 rappels personnels.

→ La réunion de promo s'affiche en grand et apparaît en tête de la Focus List. Les rappels sont compactés en bas.

**Scénario 2 — Événement lointain mais important**
> Présentation finale devant le jury dans 10 jours, 20 participants.

→ Aujourd'hui elle pèse peu. Dans 3 jours elle commence à monter dans la Focus List. La veille, elle devient prioritaire.

**Scénario 3 — Deux événements au même moment**
> Un déjeuner informel et une réunion client au même créneau.

→ La réunion client (groupe pro, participants externes) prime visuellement. Le déjeuner est affiché en secondaire avec une indication de conflit.

---

