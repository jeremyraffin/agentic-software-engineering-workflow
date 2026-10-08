## Summary

<!-- Résultat observable, pourquoi ce changement existe et issue liée. -->

## Evidence

| Layer | Status | Evidence |
|---|---|---|
| Local | `<PASS / FAIL / N/A>` | `<commandes, point fixe, résultats>` |
| CI | `<PASS / FAIL / N/A>` | `<checks sur le même point fixe>` |
| Remote | `<PASS / FAIL / N/A>` | `<réglages, preview ou smoke tests>` |

## Independent review

- Reviewer and independence: `<À_ADAPTER / N/A avec raison>`
- Fixed point reviewed: `<commit ou plage de diff>`
- Findings and dispositions: `<lien vers la review durable>`

## Risks

<!-- Risques résiduels, limites connues, rollback et éléments hors périmètre. -->

## Handoff

- Next phase and role: `<phase et rôle attendus selon docs/agents/phases.md>`
- Expected action: `<ce que le rôle suivant doit faire>`
- Open decisions: `<décisions ouvertes / aucune>`

## Merge Danger

**Door:** `<one-way / two-way>`

**Blast Radius:** `<surface affectée>`

## Human gate

- Requirement: `<required / not required avec raison>`
- Decision: `<lien vers la décision explicite / pending / N/A>`

## Closure

- [ ] le commit candidat est identifié ;
- [ ] les preuves locales couvrent ce commit ;
- [ ] les checks CI requis couvrent ce commit ;
- [ ] les surfaces distantes sont vérifiées ou justifiées `N/A` ;
- [ ] les findings `BLOCKING` et `IMPORTANT` sont résolus ;
- [ ] le human gate requis est enregistré ;
- [ ] le smoke test post-merge possède un contrôle et un responsable nommés.
