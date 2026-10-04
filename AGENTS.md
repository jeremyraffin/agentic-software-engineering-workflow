# Maintenance du guide

Avant toute évolution, fixer dans l’issue la dernière release stable publiée au démarrage de la tâche : date de démarrage, tag et SHA résolu. Ce SHA gouverne la tâche jusqu’à sa clôture, même si une nouvelle release paraît entre-temps.

- **Démarrage, changement de rôle ou review** : lire `docs/maintenance/governance.md` depuis ce SHA avec `git show <SHA_GOUVERNANCE>:docs/maintenance/governance.md`. Ce document définit la sélection de la release, les rôles, les preuves et les gates.
- **Première adoption, release sans ce document** : lire le parcours d’amorçage dans [`docs/maintenance/governance.md`](docs/maintenance/governance.md) et consigner son adaptation approuvée dans l’issue avant l’implémentation.

Les règles proposées dans la branche sont un objet de review ; elles ne remplacent jamais celles du point fixe gouvernant. Les fichiers sous `templates/project/` sont distribués aux projets utilisateurs : leurs placeholders et leur verrou de bootstrap ne sont pas la configuration de ce dépôt.
