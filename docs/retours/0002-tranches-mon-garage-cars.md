# Retour 0002 — Premières tranches de `mon-garage-cars`

Date : 2026-10-08
Sources : PR publiques [#9](https://github.com/jeremyraffin/mon-garage-cars/pull/9), [#14](https://github.com/jeremyraffin/mon-garage-cars/pull/14), [#21](https://github.com/jeremyraffin/mon-garage-cars/pull/21), [#22](https://github.com/jeremyraffin/mon-garage-cars/pull/22) et issue [#18](https://github.com/jeremyraffin/mon-garage-cars/issues/18)

## Contexte

Après le bootstrap, le projet a livré une Vitrine publique, un smoke test post-merge, puis deux tranches backend HIGH-RISK (modèle de données, matrice RLS et stockage privé des photos) avec le workflow v0.3.0. L’implémentation était confiée à Claude Code / Sonnet 5.5 et la review à Codex.

Ce retour relit ces PR et issues a posteriori pour vérifier ce que le guide a réellement produit, et ce qu’il n’a pas obtenu.

## Ce qui a fonctionné

- L’issue #18 porte un handoff complet avant l’implémentation : source approuvée, résultat attendu, preuves exigées, décisions ouvertes, risques, prochain rôle et modèle. Un agent sans accès à la conversation d’origine pouvait reprendre la tâche.
- Les labels d’état ont servi de repère : #18 est passée de `blocked` à `ready-for-agent` lorsque sa dépendance #17 a été livrée.
- La boucle review-corrections a fonctionné sur #22 : quatre passes de review publiées, avec des findings classés `BLOCKING`, `IMPORTANT` et `SUGGESTION` et une réponse à chacun. Plusieurs findings portaient sur des affirmations du README et de la description de PR, pas seulement sur le code.

## Signaux observés

| Signal | Conséquence générale |
|---|---|
| #14, #21 et #22 ont été mergées alors que leur description indiquait encore `Decision: pending` ; #9 annonce la validation du Propriétaire sans la consigner. Le merge par le Propriétaire a tenu lieu de décision. | Le merge ne vaut pas human gate : publier la décision avant le merge, en nommant le commit candidat. |
| Le handoff complet de #18 venait de `phases.md`, mais la fin de tâche de `AGENTS.md`, lue en premier par les agents, ne demandait ni prochain rôle ni action attendue. | Aligner la fin de tâche sur le handoff et porter la suite dans le gabarit de PR. |
| Les labels `type:*`, `risk:*` et de triage coexistaient dans deux fichiers sans règle reliant un label d’état au prochain intervenant. | Documenter les labels d’état, leur signification et le prochain intervenant. |
| Le reviewer est nommé « Codex (GPT-5.6 Sol) » sur #9 et #14, mais seulement « Codex (OpenAI) » sur #21. | Exiger l’environnement et le modèle effectif dans le rapport de review. |

## Limites

Ce retour porte sur un seul projet, mené par une seule personne, sur quelques jours. Les conséquences restent des ajustements du guide, à confirmer sur d’autres tâches. Les PR concernées ne sont pas réécrites ; leur décision humaine peut être consignée a posteriori, en l’indiquant comme telle.
