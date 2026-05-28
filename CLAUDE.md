@AGENTS.md

## Correction Memory Rule

Si une correction utilisateur révèle une règle durable **propre à ce projet**, proposer de l'ajouter dans `CLAUDE.md` sous forme de pitfall actionnable : symptôme, règle, vérification. Ne pas modifier `CLAUDE.md` pour une préférence temporaire, un contexte de session ou une erreur déjà couverte ailleurs.
---

## Agentic Delivery Layer

Utiliser `.claude/agents/` et `.claude/commands/` comme couche d'exécution spécialisée. Agents disponibles :

- `@feature-planner` → feature/refacto non triviale, cadrage, feature brief, découpage et preuves attendues
- `@debugger` → bug, régression, comportement incohérent, cause racine à isoler
- `@test-engineer` → manque de couverture unit / integration, dette de preuve, non-régression
- `@playwright-e2e` → parcours critique visible, golden path, test flaky, setup e2e
- `@frontend-designer` → nouvel écran, composant, responsive, accessibilité minimale, conformité `DESIGN.md`
- `@devops-ci` → Docker, CI, scripts, env, build, déploiement, diagnostic runner/config
- `@code-reviewer` → revue avant merge ou avant livraison importante
- `@product-guardian` → contrôle de conformité à `spec.md`, `architecture.md`, `roadmap.md`, `DESIGN.md` (si présent)
- `@security-review` → auth, cookies, secrets, uploads, webhooks, permissions, providers IA et exposition de données
- `@docs-maintainer` → synchronisation `README.md`, `spec.md`, `architecture.md`, `roadmap.md`, `.env.example`, `DEPLOY.md`

Commandes utiles : `/plan-feature`, `/review-ready`, `/ship-check`.

---

---

## Mode opératoire Claude Code

Pour une tâche complexe, appliquer le pattern **Plan → Execute → Review → Ship** :

1. **Plan** : `/plan-feature` ou `@feature-planner` pour clarifier le besoin, les hypothèses, les fichiers et les preuves.
2. **Execute** : implémenter petit, par tranches vérifiables ; appeler `@frontend-designer`, `@devops-ci`, `@debugger`, `@test-engineer` ou `@playwright-e2e` uniquement si leur expertise est utile.
3. **Review** : `/review-ready`, puis `@code-reviewer`, `@product-guardian` et/ou `@security-review` selon la surface.
4. **Ship** : `/ship-check`, preuves réelles, roadmap/doc synchronisées, résumé final court.

Ne pas créer une mécanique lourde pour une tâche simple. Pour un changement trivial, appliquer seulement les étapes nécessaires, mais ne jamais supprimer la preuve minimale.

---
