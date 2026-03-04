# Stratégie de branches

Toutes les parties du projet (core, Syncro backend, Syncro frontend) suivent la même stratégie de branches.

---

## Flux de branches

```
feature/* ──→ dev ──→ main
               │
               └── CI : tests automatisés + QA manuelle
```

| Branche     | Rôle                                                        | Merge vers   |
| ----------- | ----------------------------------------------------------- | ------------ |
| `feature/*` | Travail isolé sur une fonctionnalité                        | `dev` via PR |
| `dev`       | Intégration + CI + QA manuelle — joue le rôle de "staging" | `main` via PR |
| `main`      | Code production-ready, stable à tout moment                 | déployé      |

---

## Workflow de release

1. **Développer** sur `feature/*` (CI tourne sur chaque PR)
2. **Merger dans `dev`** via PR — intégration, CI complet, QA manuelle
3. **Quand `dev` est stable et validé** : PR de `dev` → `main` → déploiement production
4. **Ne jamais développer directement** sur `main`

---

## Convention de nommage des branches

| Type | Format | Exemple |
|------|--------|---------|
| Nouvelle fonctionnalité | `feature/<nom>` | `feature/trust-engine` |
| Correction de bug | `fix/<description>` | `fix/fuzzy-timing-offset` |
| Refactoring | `refactor/<description>` | `refactor/event-queries` |

---

## Règle d'or

> Les feature branches assurent l'isolation. `dev` est le point de validation avant production. `main` est toujours stable.

---

## Voir aussi

- [[Roadmap|Feuille de route]]
