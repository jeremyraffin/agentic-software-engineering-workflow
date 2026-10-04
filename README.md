# Agentic Software Engineering Workflow

Workflow expérimental pour faire collaborer des agents de spécification, d’architecture, d’implémentation, de review et de sécurité avec des validations humaines explicites.

## Statut

Version `v0.1.0`. Cette version constitue la base initiale, avant intégration des retours d’expérience obtenus sur des projets réels.

## Principes

- classer chaque tâche en `FAST`, `STANDARD` ou `HIGH-RISK` avant d’agir ;
- maintenir des human gates pour les décisions difficiles à inverser ;
- séparer spécification, implémentation et review ;
- travailler par petites tranches verticales démontrables ;
- exiger un Verification Harness adapté au risque ;
- conserver les décisions durables dans des ADR ;
- utiliser un vocabulaire métier explicite et stable.

## Contenu

Le dossier [`templates/project`](templates/project) contient les fichiers à copier dans un nouveau projet :

- `AGENTS.md` : règles communes aux agents ;
- `CLAUDE.md` : pointeur vers la source de vérité commune ;
- `docs/agents/workflow.md` : adaptation du workflow au projet ;
- `docs/agents/models.md` : rôles et affectation des modèles ;
- `docs/agents/phases.md` : phases, critères de sortie et passages de relais ;
- `docs/agents/issue-tracker.md` : conventions GitHub Issues ;
- `docs/agents/triage-labels.md` : correspondance des labels de triage ;
- `docs/agents/domain.md` : consommation des documents métier et ADR.

Les marqueurs `<À_ADAPTER>` sont intentionnels. Le bloc `BOOTSTRAP_REQUIRED` empêche l’implémentation produit tant que le plan de bootstrap n’a pas été validé puis exécuté.

## Démarrage d’un projet

1. Installer séparément les skills nécessaires, notamment celles de [`mattpocock/skills`](https://github.com/mattpocock/skills), selon leurs instructions amont.
2. Copier le contenu de `templates/project` à la racine du nouveau dépôt.
3. Adapter l’issue tracker et les labels.
4. Mener la discovery avec la skill user-invoked `$grill-with-docs`.
5. Produire puis faire valider humainement la spec et le plan de bootstrap.
6. Suivre `docs/agents/phases.md` pour chaque changement de rôle et exécuter le bootstrap sans fonctionnalité produit.
7. Remplacer les marqueurs `<À_ADAPTER>` seulement à partir de commandes et contraintes vérifiées.
8. Retirer `BOOTSTRAP_REQUIRED` lorsque les critères du bootstrap sont satisfaits.

## Licence

MIT. Les skills tierces ne sont pas incluses dans ce dépôt et conservent leurs propres licences.
