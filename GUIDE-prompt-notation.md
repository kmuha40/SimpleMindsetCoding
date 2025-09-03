# Guide d’application et de notation du Codex Prompt

Ce document explique ce qui est ajouté par rapport à un simple « system prompt » : la méthodologie, les livrables attendus, la checklist anti‑complecting et le système de notation (score de simplicité).

## Livrables imposés
- Architecture ASCII et liste des modules.
- Signatures publiques, invariants, contrats.
- Code par module, lisible et minimal.
- Graphe des dépendances (acyclique attendu).
- Checklist anti‑complecting complétée.
- Score de simplicité et décision (refactoriser ou accepter).
- Plan de refactoring si nécessaire.

## Méthodologie (résumé en 7 points)
1. Définir les abstractions selon les 5W (Who/What/When/Where/Why).
2. Découper en modules indépendants, reliés par composition.
3. Isoler l’IO/persistance/frameworks derrière des ports/adaptateurs.
4. Encapsuler l’état, privilégier des valeurs immuables.
5. Vérifier la simplicité objectivement (graphe acyclique, responsabilités unitaires, pas d’entrelacement).
6. Tester la logique pure (unitaires) et les ports (contrats).
7. Évaluer via la checklist anti‑complecting et produire un score.

## Checklist anti‑complecting (à cocher)
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

## Système de notation (score de simplicité)
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

## Usage recommandé dans un flux d’équipe
- Avant implémentation: remplir grossièrement la checklist pour guider le design.
- PR/MR: inclure l’architecture ASCII, la checklist, le score et, si < 8, le plan de refactor.
- Revue: challenger les points < 1 et viser ≥ 8 avant fusion, sauf exception motivée (tech‑debt tracée).

## Relation avec `codex-prompt.md`
- `codex-prompt.md` contient le texte du prompt et les exigences.
- Ce guide explicite la mise en œuvre concrète, afin de rendre l’évaluation reproductible et auditable.

## Licence
- Même périmètre et licence que le prompt: CC BY 4.0 (voir `LICENSE-prompt.md`).
