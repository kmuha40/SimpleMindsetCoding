SPDX-License-Identifier: CC-BY-4.0

# Codex Prompt Application and Scoring Guide / Guide d’application et de notation

This guide explains what’s added beyond a basic system prompt: methodology, required deliverables, the anti‑complecting checklist, and the simplicity scoring system. Below you will find the English version first, followed by the French translation.

---

## English

### Required Deliverables
- ASCII architecture diagram and module list.
- Public signatures, invariants, and contracts.
- Per‑module code, readable and minimal.
- Dependency graph (expected to be acyclic).
- Completed anti‑complecting checklist.
- Simplicity score and decision (refactor or accept).
- Refactoring plan if needed.

### Methodology (7‑step summary)
1. Define abstractions via the 5Ws (Who/What/When/Where/Why).
2. Split into independent modules, compose to connect them.
3. Isolate IO/persistence/frameworks behind ports/adapters.
4. Encapsulate state, prefer immutable values.
5. Verify simplicity objectively (acyclic graph, single responsibilities, no entanglement).
6. Test pure logic with unit tests; test ports with contract tests.
7. Evaluate with the anti‑complecting checklist and produce a score.

### Anti‑complecting Checklist (tick each)
- Acyclicity: no circular dependencies between modules.
- Single responsibility: each module has a clear, narrow purpose.
- Separation of concerns: no logic/IO mixing.
- Immutability by default: local, justified mutations only.
- Minimal interfaces: reduced, explicit, stable contracts.
- Composition over inheritance: assemble capabilities rather than inherit.
- Encapsulated state: no shared global state.
- Directed dependencies: from outside to inside (ports/adapters).
- Testability: logic testable in isolation; ports covered by contracts.
- Local readability: each artifact understood in under 3 minutes.

Tip: tune this checklist for your context, but keep it consistent and explicit.

### Scoring System (Simplicity Score)
- Scale: 10 criteria × 1 point each → score out of 10.
- Threshold: score < 8 → refactor immediately; score ≥ 8 → acceptable.
- Optional: use half‑points for partial compliance, but document why.

Quick example:
- Acyclicity: 1
- Single responsibility: 0.5 (module X does two things)
- Separation of concerns: 1
- Immutability: 0.5 (structure Y mutated globally)
- Minimal interfaces: 1
- Composition: 1
- Encapsulated state: 1
- Directed dependencies: 1
- Testability: 1
- Local readability: 1
Total: 9 → Acceptable (track the two gaps in a refactor backlog).

### Team Workflow
- Pre‑implementation: draft the checklist to guide design.
- PR/MR: include ASCII architecture, checklist, score, and if < 8, a refactor plan.
- Review: challenge any item < 1 and aim for ≥ 8 before merge, unless justified technical debt.

### Relation to `codex-prompt.md`
- `codex-prompt.md` contains the prompt text and hard requirements.
- This guide explains practical application to make evaluation reproducible and auditable.

### License
- Same scope and license as the prompt: CC BY 4.0 (see `LICENSE-prompt.md`).

---

## Français

### Livrables imposés
- Architecture ASCII et liste des modules.
- Signatures publiques, invariants, contrats.
- Code par module, lisible et minimal.
- Graphe des dépendances (acyclique attendu).
- Checklist anti‑complecting complétée.
- Score de simplicité et décision (refactoriser ou accepter).
- Plan de refactoring si nécessaire.

### Méthodologie (résumé en 7 points)
1. Définir les abstractions selon les 5W (Who/What/When/Where/Why).
2. Découper en modules indépendants, reliés par composition.
3. Isoler l’IO/persistance/frameworks derrière des ports/adaptateurs.
4. Encapsuler l’état, privilégier des valeurs immuables.
5. Vérifier la simplicité objectivement (graphe acyclique, responsabilités unitaires, pas d’entrelacement).
6. Tester la logique pure (unitaires) et les ports (contrats).
7. Évaluer via la checklist anti‑complecting et produire un score.

### Checklist anti‑complecting (à cocher)
- Acyclicité: aucune dépendance circulaire entre modules.
- Responsabilité unique: chaque module a un but clair et limité.
- Séparation des préoccupations: pas de mélange logique/IO.
- Immutabilité par défaut: mutations locales, explicitement motivées.
- Interfaces minimales: contrats réduits, explicites, stables.
- Composition > héritage: préférer l’assemblage de capacités.
- État encapsulé: pas d’états globaux partagés.
- Dépendances dirigées: de l’extérieur vers l’intérieur (ports/adaptateurs).
- Testabilité: logique testable isolément, ports testés par contrat.
- Lisibilité locale: chaque artefact compréhensible < 3 minutes.

Astuce: adaptez/affinez cette checklist selon votre contexte, mais restez cohérent et explicite.

### Système de notation (score de simplicité)
- Barème: 10 critères ci‑dessus × 1 point chacun → score /10.
- Seuil: score < 8 → refactoriser immédiatement; score ≥ 8 → acceptable.
- Optionnel: notez les écarts (demi‑points) si partiellement satisfait, mais documentez le pourquoi.

Exemple de grille rapide:
- Acyclicité: 1
- Responsabilité unique: 0.5 (module X fait 2 choses)
- Séparation préoccupations: 1
- Immutabilité: 0.5 (structure Y mutée globalement)
- Interfaces minimales: 1
- Composition: 1
- État encapsulé: 1
- Dépendances dirigées: 1
- Testabilité: 1
- Lisibilité locale: 1
Total: 9 → Acceptable (suivre les 2 écarts en backlog de refactor).

### Usage recommandé dans un flux d’équipe
- Avant implémentation: remplir grossièrement la checklist pour guider le design.
- PR/MR: inclure l’architecture ASCII, la checklist, le score et, si < 8, le plan de refactor.
- Revue: challenger les points < 1 et viser ≥ 8 avant fusion, sauf exception motivée (tech‑debt tracée).

### Relation avec `codex-prompt.md`
- `codex-prompt.md` contient le texte du prompt et les exigences.
- Ce guide explicite la mise en œuvre concrète, afin de rendre l’évaluation reproductible et auditable.

### Licence
- Même périmètre et licence que le prompt: CC BY 4.0 (voir `LICENSE-prompt.md`).
