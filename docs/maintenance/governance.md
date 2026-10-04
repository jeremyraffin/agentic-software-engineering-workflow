# Gouvernance des évolutions du guide

Ce document concerne la maintenance de ce dépôt. Le contenu de `templates/project/` est le produit distribué ; ses changements sont évalués comme ceux de tout autre livrable. Les commandes ci-dessous s’exécutent depuis la racine du dépôt.

## 1. Fixer la release gouvernante

À l’intake, enregistrer la date et l’heure UTC de démarrage de la tâche, puis consulter les releases publiées :

```sh
gh api --paginate repos/jeremyraffin/agentic-software-engineering-workflow/releases --jq '.[] | select(.draft == false and .prerelease == false) | {tag_name, published_at, html_url}'
```

Retenir la release stable dont `published_at` est la plus récente parmi celles publiées au plus tard au démarrage. Charger son tag et résoudre son commit :

```sh
git fetch origin tag <TAG_GOUVERNANCE>
git rev-parse <TAG_GOUVERNANCE>^{commit}
```

L’issue porte la date de démarrage, le lien de release, le tag et le SHA complet. La sélection est terminée lorsque ces quatre éléments sont enregistrés et que le commit est lisible localement. En cas de release introuvable, d’accès impossible ou de tag incohérent, suspendre le démarrage et faire résoudre l’incertitude ; une branche courante n’est pas une baseline implicite.

Le **SHA de gouvernance** reste fixe jusqu’à la clôture. Les lectures suivantes utilisent ce SHA, jamais un tag susceptible de bouger ni les fichiers modifiés de la branche :

```sh
git show <SHA_GOUVERNANCE>:AGENTS.md
git show <SHA_GOUVERNANCE>:docs/maintenance/governance.md
```

Les pointeurs de ces documents se résolvent eux aussi dans le même commit. Une nouvelle règle de maintenance ne devient applicable qu’aux tâches démarrées après la publication d’une release qui la contient. Une nouvelle release pendant la tâche ne change ni ses gates ni sa review.

### Amorçage depuis v0.2.0

La release `v0.2.0` ne contient pas de règles de maintenance racine. Pour la première adoption, l’issue approuvée fixe l’adaptation au guide et ses affectations de rôles avant l’implémentation. Elle s’appuie sur les quatre fichiers ci-dessous au SHA de cette release. Le document proposé dans la branche est évalué contre cette adaptation, sans gouverner sa propre review.

Les instructions de bootstrap produit, les placeholders et la matrice d’affectation des projets utilisateurs restent du contenu distribué. Ils ne sont ni exécutés ni réécrits pour configurer le dépôt du guide. L’évolution du guide et de ses règles est précisément le livrable autorisé par l’issue ; la règle du template interdisant de changer le workflow pendant une implémentation produit protège ici le point fixe de gouvernance.

## 2. Charger les règles utiles au point fixe

Ces sources évitent de recopier le workflow. Lire le fichier indiqué intégralement depuis le SHA de gouvernance au déclencheur correspondant :

| Déclencheur | Source à lire avec `git show <SHA_GOUVERNANCE>:<CHEMIN>` | Usage pour le guide |
|---|---|---|
| Intake et classification | `templates/project/AGENTS.md` | niveaux de risque, escalade après deux échecs, gates, conventions Git et review |
| Démarrage ou changement de phase | `templates/project/docs/agents/phases.md` | critères de sortie et handoffs |
| Affectation ou substitution d’un rôle | `templates/project/docs/agents/models.md` | capacités et contrats des rôles ; la matrice distribuée reste celle des projets utilisateurs |
| Commit non-WIP, review ou clôture | `templates/project/docs/agents/evidence.md` | preuves durables, couches de vérification et clôture |

Les chemins destinés à la racine d’un projet utilisateur, par exemple `docs/agents/workflow.md` dans le template `AGENTS.md`, se consultent ici sous `templates/project/` au même SHA. Ils décrivent le template, pas une configuration locale de maintenance.

Les adaptations propres à ce dépôt sont définies ci-dessous. Toute autre exception est une décision humaine explicite enregistrée dans l’issue puis la PR ; l’implémenteur ne peut pas modifier les critères qui évaluent sa propre branche.

## 3. Classer et affecter les rôles

Les évolutions du template et des règles de maintenance sont **STANDARD** par défaut. Une correction locale évidente, telle qu’une coquille ou un lien cassé sans changement de règle, peut être **FAST**, avec justification. Une surface sensible ou une décision structurante suit **HIGH-RISK** selon la source figée.

Chaque passage de relais inscrit dans l’issue, puis dans la PR dès son ouverture :

- le rôle, l’identité de l’agent et son environnement ;
- le modèle réellement utilisé, ou `humain` pour une intervention humaine ;
- le SHA de gouvernance, la source approuvée et le point fixe du travail examiné ;
- le résultat, les preuves, les décisions ouvertes et le prochain rôle.

Le **SHA candidat** désigne le contenu implémenté ou revu ; il est distinct du SHA de gouvernance. Une review nomme aussi la base de son diff. Avant le premier commit, identifier explicitement le travail comme non commité ; fixer ensuite le SHA candidat avant la review durable.

Pour STANDARD et HIGH-RISK, Implementation et Review utilisent des agents distincts et, lorsque disponibles, des modèles différents. Les affectations effectives sont enregistrées avant le dispatch. Toute substitution ou impossibilité de diversité de modèle est documentée avec sa raison et sa validation humaine avant de poursuivre. La séparation des agents reste requise. La matrice distribuée n’est pas modifiée pour refléter ces affectations temporaires.

### Handoff entre outils

L’affectation définie dans `models.md` au SHA de gouvernance est le chemin par défaut. Si l’agent courant ne peut pas lancer l’environnement ou le modèle attendu, il prépare le handoff puis s’arrête avant d’exécuter le rôle cible :

1. publier dans l’issue la source approuvée, le SHA de gouvernance, la base de travail, le scope, les preuves disponibles et le rôle, l’environnement et le modèle attendus ;
2. faire ouvrir par l’humain une session dans l’environnement cible avec ce paquet, sans dépendre de la conversation source ;
3. faire confirmer par l’agent cible les points fixes, son identité et son modèle avant d’exécuter le rôle cible, y compris une review ;
4. rendre le résultat par une branche, un commit ou une PR, accompagné des preuves et décisions ouvertes ;
5. confier la phase suivante à l’agent prévu par la matrice.

Le handoff est terminé lorsque l’agent cible a confirmé le paquet dans l’issue ou la PR. Une indisponibilité ne vaut pas autorisation de remplacement : toute substitution est décidée explicitement par l’humain et enregistrée avant la reprise.

## 4. Vérifier et faire revoir

Pour un changement documentaire, le contrôle local minimal est :

```sh
git diff --check <BASE_DIFF>...<SHA_CANDIDAT>
```

Examiner aussi chaque nouveau pointeur : un lien relatif doit résoudre dans le livrable, un chemin de gouvernance dans le commit figé et une commande Git avec les valeurs enregistrées. Vérifier les scénarios affectés par les règles, dont une branche qui modifie ses propres instructions. Ajouter les contrôles appropriés si la tâche change des scripts, une CI ou une autre surface exécutable. Les commandes produit `<À_ADAPTER>` du template ne sont pas des contrôles du guide.

La PR rassemble les preuves locales, CI, distantes, de review et de validation humaine selon `evidence.md` au point fixe. Toute couche non applicable porte `N/A` et sa raison ; un contrôle impossible reste une limite explicite.

La review STANDARD/HIGH-RISK couvre les standards figés et la spec approuvée. Le reviewer reçoit et lit la source approuvée, le diff, les règles au SHA de gouvernance et les preuves sur le SHA candidat. Il publie son identité, rôle, environnement, modèle, plage examinée et findings `BLOCKING`, `IMPORTANT` ou `SUGGESTION`. Après correction, les preuves et la review couvrent le nouveau candidat.

## 5. Merge et release

Le merge STANDARD/HIGH-RISK requiert une validation humaine explicite dans la PR après traitement des findings. Le rôle Release reste humain : créer ou publier une release nécessite un human gate distinct du merge. Publier la release ne requalifie pas rétroactivement la gouvernance des tâches déjà commencées.
