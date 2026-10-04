# Retour 0001 — Bootstrap de `mon-garage-cars`

Date : 2026-10-04
Source : [PR de bootstrap publique](https://github.com/jeremyraffin/mon-garage-cars/pull/9)

## Contexte

Le premier usage réel du workflow a transformé un dépôt documentaire en socle React, Supabase local, CI, sécurité et déploiement statique. Le bootstrap était HIGH-RISK et séparait implémentation, review indépendante et validation humaine.

Ce retour documente les signaux qui ont changé le guide. Le template reste indépendant de la stack, des fournisseurs et des versions de ce projet.

## Signaux observés

| Signal | Conséquence générale |
|---|---|
| Une variable distante Cloudflare a pris le pas sur la version Node du dépôt et provoqué plusieurs échecs de preview. | Effectuer un preflight de compatibilité et de priorité de configuration avant de figer versions et dépendances. |
| Les commandes locales, les checks GitHub et le déploiement Cloudflare validaient des surfaces différentes. | Séparer explicitement les preuves locales, CI et distantes dans la clôture. |
| La review indépendante avait été conduite dans une autre conversation d’agent, puis seulement résumée par l’implémenteur. | Considérer les rapports locaux comme des brouillons et publier le rapport du reviewer dans la PR. |
| Le retrait de `BOOTSTRAP_REQUIRED` dépendait de la review, des corrections et d’une autorisation humaine. | Rendre les états du bootstrap et le double human gate observables. |
| Le bootstrap comportait de nombreux commits logiques avant la vérification finale complète. | Exiger un contrôle falsifiable adapté à chaque commit non-WIP et nommer les contrôles reportés. |

## Limites de la généralisation

Le guide ne reprend ni React, ni Supabase, ni Cloudflare, ni leurs versions comme choix par défaut. Il généralise seulement les frontières de preuve et les gates révélés par leur intégration. Un autre projet remplace ces outils dans `workflow.md` tout en conservant la même matrice locale, CI, distante et humaine.
