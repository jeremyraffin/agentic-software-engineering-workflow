# Changelog

## Unreleased

## v0.4.0 — 2026-10-08

- rendre la version du guide indépendante de celle de la matrice de modèles dans le template ;
- exiger la prochaine phase, le rôle attendu et l’action attendue dans la fin de tâche et le gabarit de PR ;
- documenter les labels d’état et le prochain intervenant ;
- compléter les labels minimaux avec les labels d’état ;
- préciser qu’un merge ne vaut pas human gate et exiger le modèle effectif du reviewer ;
- accepter la réponse à la demande comme trace durable d’une tâche FAST sans issue ni PR ;
- consigner le retour 0002 sur les premières tranches de `mon-garage-cars` ;
- créditer les fichiers adaptés de `mattpocock/skills` ;
- exposer dans le README le statut expérimental, les limites actuelles et des exemples vérifiables.

## v0.3.0 — 2026-10-04

- faire gouverner chaque évolution du guide par la dernière release stable antérieure à la tâche ;
- distinguer le SHA de gouvernance du SHA candidat soumis à review ;
- rendre visibles les rôles, agents, modèles, points fixes et substitutions dans les issues et PR ;
- formaliser le handoff manuel entre outils lorsque l’environnement prévu ne peut pas être lancé directement ;
- conserver les règles de maintenance du guide séparées du template distribué.

## v0.2.0 — 2026-10-04

- ajouter une carte des phases, critères de sortie et rôles conducteurs ;
- formaliser les handoffs et la boucle review-corrections ;
- préciser les états et la séquence de retrait de `BOOTSTRAP_REQUIRED` ;
- supprimer les cartes de workflow concurrentes des templates ;
- distinguer les preuves locales, CI, distantes et humaines dans la clôture ;
- exiger un contrôle adapté à chaque commit non-WIP et un preflight des services externes ;
- fournir un gabarit de PR qui rend reviews et human gates durables ;
- documenter l’invocation user-invoked de `$grill-with-docs` ;
- consigner le retour du bootstrap `mon-garage-cars` sans imposer sa stack.

## v0.1.0 — 2026-10-04

- première version publique du workflow ;
- classification FAST, STANDARD et HIGH-RISK ;
- human gates, Verification Harness et review indépendante ;
- templates pour Codex et Claude Code ;
- matrice v0.1 des rôles et modèles ;
- conventions GitHub Issues, triage et documentation métier.
