# Atelier 2 — Copilot Studio : Conseiller Reporting FSE+

> Durée : **35 minutes** · Format : binômes · Outil : **Copilot Studio**

---

## Mise en situation

Antoine Roux, coordinateur de programmes chez Horizon Solidaire, doit produire **chaque trimestre** un rapport FSE+ pour le bailleur européen. Aujourd'hui, il :
- ouvre un Excel d'indicateurs,
- copie les chiffres dans un Word,
- relit 8 à 12 bilans bénéficiaires pour en tirer 3 histoires « parlantes »,
- rédige 4 pages, fait valider par Marc, puis publie dans Teams.

Le tout lui prend **6 à 8 heures**.

Vous allez créer un agent qui pré-rédige la trame du rapport et la publie comme brouillon dans Teams.

---

## Objectif

Créer dans **Copilot Studio** un agent **« Conseiller Reporting FSE+ »** :
- avec des **connaissances** (Excel indicateurs + dossier bilans)
- avec une **action** Power Automate qui publie un brouillon dans Teams
- testable en posant une question simple

---

## Préparation avant l'atelier

✅ Compte Copilot Studio actif (essai gratuit ou licence)
✅ Fichier `Dataset-02-Indicateurs-FSE-T1-2026.csv` déposé dans SharePoint `/Formation-Agents-Sandbox/Reporting/`
✅ Fichier `Dataset-03-Bilan-Type-Beneficiaire.md` déposé dans SharePoint `/Formation-Agents-Sandbox/Bilans/`
✅ Un canal Teams **« Reporting FSE — Sandbox »** créé pour la session (le formateur l'a préparé)

---

## Pas-à-pas

### Étape 1 — Créer l'agent (4 min)

1. Aller sur `copilotstudio.microsoft.com`
2. **+ Créer** → **Agent**
3. Choisir **« Configurer »** (pas « Décrire »)
4. Renseigner :
   - **Nom** : `Conseiller Reporting FSE+`
   - **Description** : `Pré-rédige les trames de rapports trimestriels FSE+ à partir des indicateurs et bilans bénéficiaires, et publie un brouillon dans Teams.`
   - **Instructions** : voir étape 2

### Étape 2 — Instructions OSCAR (6 min)

Copiez ce bloc dans la zone instructions :

```
Objectif
Aider les coordinateurs de programmes de l'Association Horizon Solidaire
à produire les rapports trimestriels FSE+ pour le bailleur européen. Ton rôle
est de pré-rédiger la trame du rapport à partir des indicateurs et des bilans,
puis de publier le brouillon dans Teams pour relecture.

Sources
- Le fichier d'indicateurs trimestriels FSE+ (CSV) dans SharePoint
- Les bilans de mi-parcours et de fin de parcours des bénéficiaires
- N'utilise aucune autre source

Contexte
Association Horizon Solidaire, OBNL d'insertion socioprofessionnelle.
Le rapport est destiné à la Région Auvergne-Rhône-Alpes et à l'autorité de
gestion FSE+. Ton institutionnel, factuel, sourcé. Pas de jargon associatif.
Format : 4 sections — Synthèse · Volumétrie · Résultats · Points de vigilance.

Audience
Coordinateurs de programmes (Antoine Roux, ses pairs). Le brouillon sera
relu par le RAF (Marc Dubois) avant envoi au bailleur.

Restrictions
- Ne JAMAIS citer de bénéficiaire par son nom. Anonymise toujours (« une
  jeune de 22 ans », « un bénéficiaire issu de QPV », etc.)
- Cite la source de chaque chiffre (indicateur, ligne CSV)
- Si une donnée manque, écris « DONNÉE À COMPLÉTER » plutôt que d'inventer
- Termine toujours par 3 points de vigilance distincts, factuels
- Longueur cible : 600 à 900 mots
```

### Étape 3 — Ajouter les connaissances (5 min)

1. Onglet **« Knowledge »**
2. **+ Ajouter une connaissance** → **SharePoint**
3. Coller le lien du dossier `Formation-Agents-Sandbox/Reporting/`
4. Répéter pour `Formation-Agents-Sandbox/Bilans/`
5. Cocher **« Sources autorisées uniquement »** pour empêcher l'agent d'aller chercher ailleurs

### Étape 4 — Créer le déclencheur et l'action (10 min)

#### Déclencheur

Dans **Topics** → **+ Add** → **Create from blank** :
- **Nom** : `Publier brouillon`
- **Trigger phrases** : `publie le brouillon`, `publier dans Teams`, `envoyer le brouillon`

#### Action

1. Dans le topic, ajouter un nœud **« Call an action »**
2. Choisir **« Create a flow »** → ouvre Power Automate
3. Configurer le flux ainsi :

| Étape | Action |
|-------|--------|
| Déclencheur | « When invoked from Copilot » — paramètre d'entrée : `BrouillonRapport` (texte) |
| Action 1 | Teams — **Publier un message dans un canal** |
| Équipe | `Reporting FSE` |
| Canal | `Reporting FSE — Sandbox` |
| Message | `🟨 BROUILLON RAPPORT FSE+ — généré par l'agent — à relire par Marc :` puis insérer la variable `BrouillonRapport` |

4. Enregistrer le flux et revenir à Copilot Studio
5. Lier la sortie de l'agent (le texte du brouillon) au paramètre `BrouillonRapport`

### Étape 5 — Tester l'agent (7 min)

Dans le volet **Test** à droite de Copilot Studio, posez **dans l'ordre** :

1. `Bonjour, peux-tu me lister les indicateurs disponibles pour le T1 2026 ?`
2. `Quels écarts par rapport à la cible sont supérieurs à 10 % ?`
3. `Prépare-moi une trame de rapport FSE+ pour le T1 2026 : synthèse, volumétrie, résultats, et 3 points de vigilance.`
4. Une fois la trame produite : `Publie le brouillon dans Teams.`

### Étape 6 — Vérifier dans Teams (3 min)

- Allez dans le canal `Reporting FSE — Sandbox`
- Le brouillon doit y apparaître avec le préfixe `🟨 BROUILLON RAPPORT FSE+`
- Vérifiez qu'aucun nom de bénéficiaire n'apparaît dans le message

---

## Critères de validation

L'atelier est réussi quand :

- ✅ L'agent liste les indicateurs depuis le CSV (preuve qu'il lit la source)
- ✅ L'agent produit une trame de rapport en 4 sections, 600-900 mots
- ✅ Les chiffres cités sont **traçables** au CSV
- ✅ Aucun nom de bénéficiaire n'apparaît (Yasmine M. doit devenir « une jeune de 22 ans »)
- ✅ Le brouillon arrive dans Teams via Power Automate

---

## Pour aller plus loin

- **Variante reporting bailleur privé** : modifier les instructions pour un mécène entreprise (ton plus narratif, plus d'anecdotes anonymisées)
- **Variante alerte d'écart** : ajouter un déclencheur « alerte écart > 15 % » qui notifie Antoine et Marc dans un chat
- **Audit RGPD** : passer en revue les sources et vérifier qu'aucune donnée nominative bénéficiaire n'est indexée par l'agent

---

# Corrigé Atelier 2

> Réservé au formateur.

## Points de vigilance pendant l'animation

- **Étape 4 — Création de flux** : c'est l'étape la plus fragile. Prévoir 5 min de buffer. Si un participant n'arrive pas à créer le flux, il peut utiliser un flux préparé d'avance par le formateur (à exporter en solution Power Platform avant la session)
- **Étape 5 — Q1** : l'agent doit lister une vingtaine d'indicateurs. S'il dit « je n'ai pas accès aux données », vérifier l'étape 3 (sources)
- **Étape 5 — Q3** : si l'agent cite un nom de bénéficiaire, c'est que la restriction d'anonymisation est ignorée → renforcer la restriction et reformuler en mode impératif

## Trame de rapport attendue (résumé)

L'agent doit produire quelque chose comme :

### Synthèse — T1 2026
> Le premier trimestre 2026 confirme une dynamique d'entrée conforme à la cible (94 bénéficiaires entrés sur 95 visés). Les sorties positives restent inférieures à l'objectif trimestriel (42 réalisées contre 57 attendus), principalement portées par un marché de l'emploi tendu en début d'année. La qualité du parcours reste élevée (assiduité 84 %, satisfaction 8,2/10).

### Volumétrie
- Entrées totales : 94 (cible 95, écart -1)
- Femmes : 51 (54 % du flux, surreprésentation T1)
- QPV : 42 (45 % du flux, bon recrutement Marseille)
- Sans diplôme : 58
- Handicap : 11 (partenariat Cap Emploi)

### Résultats
- Sorties positives : 42 (cible 57)
- Sorties emploi durable : 18 (cible 29) — écart -11 lié à un marché tendu
- Sorties formation qualifiante : 16 (conforme)
- Sorties création d'activité : 8 (conforme)
- Sorties négatives : 12 (bon résultat, sous la cible 19)

### Points de vigilance
1. Sourcing entreprises pour stages à Marseille (écart -280 h, plan d'action à présenter en avril)
2. 3 feuilles de temps salariés manquantes au T1 — relance en cours, conformité 97 %
3. Indemnités sous-consommées (-29 500 €) du fait du décalage temporel — à rattraper au T2

DONNÉE À COMPLÉTER : résultats des audits à 6 mois post-sortie (cohorte 2025).

## Erreurs courantes des participants

- Oublier d'autoriser le connecteur SharePoint à Copilot Studio
- Mettre l'instruction d'anonymisation **après** les autres restrictions → la déplacer en tête de section R pour qu'elle soit plus saillante
- Définir le déclencheur Teams avec un canal qui n'existe pas → vérifier l'orthographe exacte du canal
- Tester avec une question trop ouverte (« fais le rapport ») → guider vers une question structurée
