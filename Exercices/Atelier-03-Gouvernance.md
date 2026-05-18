# Atelier 3 — Gouvernance et publication

> Durée : **10 minutes** (intégré au bloc gouvernance) · Format : individuel ou plénière

---

## Mise en situation

Sophie Lambert, responsable communication et pilote du projet « Horizon Numérique », doit présenter au CODIR de l'Association Horizon Solidaire le **cadre de gouvernance** des agents M365 Copilot avant le déploiement à grande échelle. Claire Moreau, DG, lui demande une **politique d'usage en 1 page** et un **plan de revue trimestrielle**.

---

## Objectif

Produire les deux livrables suivants :
1. Une **politique d'usage** des agents M365 Copilot (7 articles)
2. Une **fiche de suivi trimestriel** pour les agents en production

Les deux livrables sont générés à l'aide des **prompts 10 et 9** de la bibliothèque.

---

## Pas-à-pas

### Étape 1 — Politique d'usage (5 min)

1. Ouvrir Microsoft 365 Copilot Chat
2. Coller le **prompt 10** de la bibliothèque (« Rédiger une politique d'usage des agents »)
3. Faire générer la politique
4. Relire et **corriger** :
   - Vérifier que les 7 articles sont présents et numérotés
   - Vérifier que l'article 2 (données interdites) mentionne bien le RGPD bénéficiaires
   - Vérifier que la signature finale cite « Claire Moreau, Directrice générale »
5. Copier la politique dans un document Word et la stocker dans SharePoint `/Gouvernance-IA/Politiques/`

### Étape 2 — Fiche de suivi pour les deux agents créés (5 min)

Pour **chacun** des deux agents créés aux ateliers 1 et 2 :
1. Coller le **prompt 9** de la bibliothèque (« Documenter un agent pour passation »)
2. Renseigner les champs (nom, owner, audience, instructions, sources, actions)
3. Récupérer la fiche générée
4. Stocker dans SharePoint `/Gouvernance-IA/Fiches-Agents/`

---

## Critères de validation

L'atelier est réussi quand :

- ✅ La politique tient en 1 page, comporte 7 articles, est signée Claire Moreau
- ✅ Les deux fiches d'agent existent et contiennent toutes les sections obligatoires
- ✅ Les fiches sont stockées au bon emplacement SharePoint

---

## Réflexion finale (à emporter)

Sur les **deux** agents que vous venez de créer, pour chacun :

| Question | Agent 1 (Tremplin Pro) | Agent 2 (Reporting FSE) |
|----------|------------------------|--------------------------|
| Qui en est le propriétaire métier ? | _____________ | _____________ |
| À qui ouvre-t-on le public au démarrage ? | _____________ | _____________ |
| Quelle métrique de succès dans 3 mois ? | _____________ | _____________ |
| Date de la première revue trimestrielle ? | _____________ | _____________ |

---

# Corrigé Atelier 3

> Réservé au formateur.

## Animation

- Cet atelier est plus **court et plus conceptuel** que les deux précédents
- Le formateur peut choisir de le faire en **plénière** plutôt qu'individuellement, en projetant la génération de la politique en direct
- Insister sur le fait que **la gouvernance n'est pas optionnelle** : un agent sans politique d'usage est un risque RGPD potentiel

## Politique d'usage — attendu

Les 7 articles doivent couvrir :

1. **Qui peut créer un agent** : tout salarié ayant suivi la formation et obtenu validation Sophie Lambert
2. **Données interdites** : données nominatives bénéficiaires, données de santé, données bancaires, identifiants
3. **Validation avant publication** : revue par Sophie + accord de l'owner métier
4. **Périmètre de partage** : interne par défaut, externe sur dérogation Claire Moreau
5. **Transparence** : tout agent doit annoncer sa nature dans son message d'accueil
6. **Revue trimestrielle** : revue d'usage, de pertinence, de conformité
7. **Incidents** : signalement immédiat à Sophie Lambert, escalade DG si données sensibles concernées

Signature : « Validée par Claire Moreau, Directrice générale, le [DATE] ».

## Erreurs courantes

- Politique trop longue (> 1 page) → demander à Copilot de raccourcir
- Articles flous (« être responsable ») → demander à Copilot de rendre chaque article actionnable
- Oubli de la signature → vérifier la dernière section
