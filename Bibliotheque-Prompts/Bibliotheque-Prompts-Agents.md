# Bibliothèque de prompts OSCAR — Créer des agents dans M365 Copilot

> 12 prompts documentés en méthode **OSCAR** pour préparer, construire et maintenir des agents Microsoft 365 Copilot. Tous les prompts utilisent le fil rouge Association Horizon Solidaire.

---

## Comment lire un prompt OSCAR

Chaque fiche suit la même structure :

- **O — Objectif** : ce que produit le prompt
- **S — Sources** : d'où vient l'information
- **C — Contexte** : organisation, audience, ton
- **A — Audience** : qui reçoit / lit le résultat
- **R — Restrictions** : longueur, format, interdits

Le **prompt prêt à l'emploi** est encadré et peut être copié-collé dans Copilot Chat, Agent Builder ou Copilot Studio.

---

## Phase 1 — Cadrage avant de créer l'agent

### Prompt 1 — Qualifier un cas d'usage

- **O** : Décider si un cas d'usage justifie de créer un agent dédié plutôt que d'utiliser Copilot Chat
- **S** : Description orale ou écrite du cas par le demandeur
- **C** : Association Horizon Solidaire, équipe pilote « Horizon Numérique » animée par Sophie Lambert
- **A** : Sophie et le sponsor du cas d'usage
- **R** : Réponse en moins de 200 mots, structure imposée, pas de jargon technique

```
Tu es un consultant en transformation numérique chargé de qualifier les cas
d'usage d'agents M365 Copilot pour l'Association Horizon Solidaire.

Le cas d'usage proposé est :
« [DÉCRIRE LE CAS EN 2-3 PHRASES] »

Évalue ce cas selon 5 critères :
1. Fréquence — la tâche revient-elle au moins une fois par semaine ?
2. Audience — combien de personnes en bénéficieraient ?
3. Sources — les documents de référence existent-ils déjà dans M365 ?
4. Risque — la tâche manipule-t-elle des données sensibles (RGPD bénéficiaires) ?
5. Gain estimé — combien de minutes par occurrence ?

Rends une décision : AGENT RECOMMANDÉ / À RAFFINER / RESTER SUR COPILOT CHAT.
Justifie en 3 phrases.
```

---

### Prompt 2 — Choisir la bonne famille d'agent

- **O** : Recommander entre Agent Builder, Copilot Studio simple ou Copilot Studio avec actions
- **S** : Description du cas qualifié à l'étape 1
- **C** : 3 familles d'agents disponibles dans M365
- **A** : Sophie Lambert et l'owner métier du cas
- **R** : Tableau comparatif obligatoire, recommandation finale en 1 phrase

```
Pour le cas d'usage suivant : « [CAS] »,
compare les trois options suivantes sous forme de tableau :

| Option | Force principale | Limite | Recommandé si |
|--------|------------------|--------|---------------|
| Agent Builder (dans Copilot Chat) |  |  |  |
| Copilot Studio — agent déclaratif |  |  |  |
| Copilot Studio — agent avec actions Power Automate |  |  |  |

Termine par une recommandation en une seule phrase qui commence par
« Je recommande... » et justifie en 2 points.
```

---

### Prompt 3 — Rédiger les instructions OSCAR d'un agent

- **O** : Produire un bloc d'instructions structuré OSCAR prêt à coller dans Agent Builder ou Copilot Studio
- **S** : Description du cas, public visé, sources connues
- **C** : Méthode OSCAR enseignée chez Horizon, ton sobre et précis
- **A** : Le créateur de l'agent (qui va le coller dans l'outil)
- **R** : Maximum 1500 caractères, sections obligatoires, vouvoiement

```
Tu es un expert en rédaction d'instructions d'agents M365 Copilot.
Rédige les instructions pour un agent qui doit :
« [DÉCRIRE LA FONCTION DE L'AGENT EN 2 PHRASES] »

Ses utilisateurs cibles sont : [PROFILS].
Les sources documentaires sont : [LISTER SOURCES].

Structure ta réponse exactement comme ceci :

**Objectif**
[1-2 phrases : but unique de l'agent]

**Sources**
[Liste à puces des sources à consulter]

**Contexte**
[Organisation, mission, ton attendu]

**Audience**
[Qui pose les questions, niveau de maîtrise]

**Restrictions**
- [Interdits explicites, ce que l'agent ne doit JAMAIS faire]
- [Format de réponse attendu]
- [Que faire si la question sort du périmètre]

Maximum 1500 caractères au total. Vouvoiement.
```

---

## Phase 2 — Construction de l'agent

### Prompt 4 — Générer une description publique d'agent

- **O** : Rédiger le champ « description » que verront les utilisateurs dans le store d'agents
- **S** : Nom de l'agent, fonction principale
- **C** : La description s'affiche dans une carte de 200 caractères dans Microsoft 365
- **A** : Les utilisateurs finaux qui cherchent un agent
- **R** : Maximum 200 caractères, commence par un verbe, pas de jargon

```
Rédige une description publique pour l'agent suivant :
- Nom : [NOM]
- Fonction : [FONCTION]
- Audience : [AUDIENCE]

Contraintes :
- 200 caractères maximum (espaces inclus)
- Commencer par un verbe d'action à l'infinitif
- Citer concrètement ce que l'agent fait, pas ce qu'il « est »
- Pas de mot creux (innovant, performant, intelligent)
- Vouvoiement implicite (ne pas dire « vous »)

Propose 3 versions et indique laquelle tu recommandes et pourquoi.
```

---

### Prompt 5 — Construire la base de connaissances

- **O** : Identifier précisément les documents SharePoint à indexer pour l'agent
- **S** : Arborescence SharePoint existante de l'Association Horizon Solidaire
- **C** : Limiter le périmètre pour éviter le bruit et les confusions
- **A** : Le créateur de l'agent
- **R** : Liste structurée, justifier chaque source incluse et chaque source exclue

```
L'agent « [NOM DE L'AGENT] » doit répondre à des questions sur :
« [SUJET] ».

Voici l'arborescence SharePoint disponible :
[COLLER LA LISTE DES DOSSIERS / SITES]

Identifie :
1. Les 3 à 7 sources à INCLURE en priorité — pour chacune : chemin exact +
   justification en 1 phrase
2. Les sources à EXCLURE explicitement même si elles semblent pertinentes —
   pour chacune : chemin + raison (obsolète, sensible, redondant, etc.)
3. Une recommandation pour 1 source à CRÉER si elle manque (par exemple
   une FAQ consolidée)

Présente sous forme de 3 listes distinctes.
```

---

### Prompt 6 — Lister les questions de test (jeux de Q&R)

- **O** : Préparer une batterie de questions pour valider l'agent avant publication
- **S** : Description de l'agent et de son audience
- **C** : Tests systématiques : faciles, difficiles, hors périmètre, pièges
- **A** : Le testeur (souvent le créateur ou un binôme)
- **R** : Exactement 15 questions, 4 catégories, format tableau

```
Génère un plan de test pour l'agent « [NOM] » dont la fonction est :
« [FONCTION] ».

Produis exactement 15 questions de test réparties ainsi :
- 5 questions FACILES (cas standard, dans le périmètre)
- 4 questions DIFFICILES (formulations floues, plusieurs sources à croiser)
- 3 questions HORS PÉRIMÈTRE (l'agent doit refuser poliment)
- 3 questions PIÈGES (questions sensibles, RGPD, formulations ambiguës)

Présente sous forme de tableau :

| # | Catégorie | Question | Réponse attendue (résumé) | Critère de réussite |
|---|-----------|----------|---------------------------|---------------------|

Les questions doivent venir d'un utilisateur réel (Léa Bernard, conseillère
en insertion sur le terrain), donc rester naturelles et concrètes.
```

---

## Phase 3 — Utilisation et amélioration

### Prompt 7 — Diagnostiquer un agent qui répond mal

- **O** : Identifier la cause d'une mauvaise réponse et proposer un correctif
- **S** : Question posée, réponse de l'agent, instructions actuelles, sources indexées
- **C** : L'agent est en production, des utilisateurs se plaignent
- **A** : Le créateur ou administrateur de l'agent
- **R** : Hypothèses classées par probabilité, plan d'action en 3 étapes

```
Mon agent M365 Copilot a donné une réponse insatisfaisante.

QUESTION POSÉE :
« [QUESTION] »

RÉPONSE DE L'AGENT :
« [RÉPONSE] »

INSTRUCTIONS ACTUELLES DE L'AGENT :
« [COLLER LE BLOC OSCAR] »

SOURCES INDEXÉES :
- [SOURCE 1]
- [SOURCE 2]
- ...

Diagnostique :
1. Liste les 3 causes les plus probables du problème, par ordre de
   probabilité décroissante (avec un score de 0 à 100 %).
2. Pour la cause la plus probable, propose un correctif précis (modifier
   les instructions ? changer les sources ? désactiver une réponse type ?).
3. Décris un test rapide pour valider le correctif en moins de 5 minutes.
```

---

### Prompt 8 — Reformuler les instructions pour réduire les réponses trop longues

- **O** : Resserrer les instructions pour que l'agent produise des réponses courtes
- **S** : Instructions actuelles
- **C** : Les utilisateurs terrain (Léa Bernard) veulent des réponses en moins de 5 lignes
- **A** : Le créateur de l'agent
- **R** : Garder la structure OSCAR, ajouter une restriction explicite de longueur

```
Voici les instructions actuelles d'un agent M365 Copilot :

« [COLLER LES INSTRUCTIONS] »

Les utilisateurs trouvent les réponses trop longues. Reformule les
instructions en :
1. Conservant la structure OSCAR
2. Ajoutant une restriction explicite : « réponse en 5 lignes maximum,
   structurée en 3 puces » dans la section RESTRICTIONS
3. Ajoutant à la section CONTEXTE que les utilisateurs sont sur le
   terrain et lisent souvent sur smartphone
4. Renforçant l'instruction « si tu manques d'information, dis-le en
   1 phrase plutôt que d'inventer »

Rends les nouvelles instructions intégrales, prêtes à coller.
```

---

### Prompt 9 — Documenter un agent pour passation

- **O** : Produire une fiche technique d'agent pour qu'un autre référent puisse en assurer la maintenance
- **S** : Configuration de l'agent dans Agent Builder ou Copilot Studio
- **C** : Continuité de service, Center of Excellence d'Horizon
- **A** : Le futur propriétaire / mainteneur de l'agent
- **R** : Fiche standardisée en 1 page, sections obligatoires

```
Rédige la fiche de passation pour l'agent suivant :
- Nom : [NOM]
- Owner actuel : [PERSONNE]
- Audience cible : [AUDIENCE]
- Instructions : [COLLER OSCAR]
- Sources : [LISTE]
- Actions (Power Automate, connecteurs) : [LISTE OU AUCUNE]

Structure la fiche exactement comme suit :

# Fiche agent — [NOM]

## Identité
- Owner, propriétaire de secours, date de création, dernière revue

## À quoi sert cet agent
- 2 phrases maximum, ton concret

## Périmètre
- Ce qu'il fait / ce qu'il ne fait pas

## Sources de connaissances
- Pour chaque source : chemin, fréquence de mise à jour, responsable

## Configuration technique
- Plateforme (Agent Builder / Copilot Studio)
- Environnement Power Platform
- Connecteurs et flux Power Automate associés

## Métriques de suivi
- Volume d'utilisation, satisfaction, incidents connus

## Plan de revue
- Fréquence de revue, points à vérifier
```

---

## Phase 4 — Gouvernance et adoption

### Prompt 10 — Rédiger une politique d'usage des agents

- **O** : Produire une politique interne courte qui cadre la création et l'usage des agents M365 Copilot
- **S** : Réglementation RGPD, charte numérique de l'association, principes de l'AI Act européen
- **C** : Association Horizon Solidaire, 82 salariés, données bénéficiaires sensibles
- **A** : Tous les salariés et bénévoles équipés Copilot
- **R** : 1 page maximum, format article par article, ton accessible

```
Rédige une politique interne d'usage des agents M365 Copilot pour
l'Association Horizon Solidaire.

Contraintes :
- 1 page maximum (≈ 600 mots)
- Structure en 7 articles courts numérotés
- Ton accessible, pas de jargon juridique inutile
- Adressée aux salariés et bénévoles, pas aux experts IT

Les articles doivent couvrir :
1. Qui peut créer un agent (rôle, formation requise)
2. Données interdites (RGPD bénéficiaires, données de santé)
3. Validation avant publication (qui valide, sur quels critères)
4. Périmètre de partage (interne uniquement, sauf accord DG)
5. Transparence (les utilisateurs doivent savoir qu'ils parlent à un agent)
6. Revue trimestrielle obligatoire
7. Que faire en cas d'incident

Finis par une signature « Validée par Claire Moreau, Directrice générale,
le [DATE] ».
```

---

### Prompt 11 — Préparer une présentation d'adoption au CODIR

- **O** : Pitcher au comité de direction le déploiement des agents M365 Copilot
- **S** : Premiers retours d'usage, cas pilotes, ROI estimé
- **C** : Réunion de CODIR mensuelle, 45 minutes, 6 personnes autour de la table
- **A** : Claire Moreau (DG), Marc Dubois (RAF), 4 autres dirigeants
- **R** : 10 slides maximum, 1 message par slide, finir par 3 décisions à prendre

```
Tu prépares une présentation de 15 minutes au CODIR de l'Association
Horizon Solidaire pour annoncer le déploiement des agents M365 Copilot.

Contexte :
- 3 agents pilotes en production depuis 6 semaines
- Données pilotes : [INSÉRER MÉTRIQUES OU « À COLLECTER »]
- 45 utilisateurs sous licence Copilot

Produis un plan de présentation en 10 slides, 1 message par slide.
Pour chaque slide, donne :
- Titre (court, factuel)
- Message-clé en 1 phrase
- 2-3 puces de contenu
- Visuel ou donnée à montrer

Les 10 slides doivent couvrir :
1. Pourquoi maintenant
2. Ce qu'est un agent M365 Copilot
3. Les 3 cas pilotes
4. Résultats premiers retours
5. Gouvernance mise en place
6. Risques identifiés et parades
7. Plan de déploiement T+3 mois
8. Budget et ressources nécessaires
9. Indicateurs de succès
10. Décisions attendues du CODIR (3 décisions explicites)
```

---

### Prompt 12 — Mesurer le ROI d'un agent

- **O** : Calculer le retour sur investissement d'un agent après 3 mois d'usage
- **S** : Données d'usage Microsoft Admin Center, sondage utilisateurs, temps avant/après
- **C** : Mesure standard pour tout agent en production chez Horizon
- **A** : Sophie Lambert et la DG
- **R** : Calcul transparent, hypothèses explicites, conclusion en 1 phrase

```
Calcule le ROI de l'agent « [NOM] » sur la base des données suivantes :

DONNÉES D'USAGE (3 derniers mois) :
- Nombre d'utilisateurs actifs uniques : [N]
- Nombre de conversations totales : [N]
- Tâches accomplies (taux de complétion) : [%]

GAIN ESTIMÉ PAR TÂCHE :
- Temps avant agent : [X] minutes par tâche
- Temps avec agent : [Y] minutes par tâche
- Coût horaire moyen utilisateur (chargé) : [Z] €/h

COÛTS :
- Temps de création de l'agent : [H] heures
- Maintenance trimestrielle estimée : [H] heures
- Licence Copilot M365 (déjà payée, à mentionner mais ne pas réimputer)

Présente le calcul ainsi :
1. Gain horaire mensuel = nb conversations × (X - Y) minutes / 60
2. Gain financier mensuel = gain horaire × coût horaire
3. Coût d'investissement = (heures de création + maintenance) × coût horaire
4. ROI à 3 mois = (gain cumulé - coût investissement) / coût investissement
5. Point mort (break-even) en mois

Conclus en une phrase : « L'agent [X] est rentabilisé en [N] mois, avec
un gain net annualisé de [M] € ».

Si une donnée manque, indique explicitement « DONNÉE MANQUANTE »
plutôt que d'inventer.
```

---

## Annexe — Gabarit OSCAR vide

Garder ce gabarit sous la main pour rédiger vos propres prompts.

```
**Objectif**
[Ce que je veux obtenir, en 1-2 phrases]

**Sources**
[D'où vient l'information : documents, conversation, données]

**Contexte**
[Organisation, audience, ton, contraintes externes]

**Audience**
[Qui va lire ou utiliser le résultat]

**Restrictions**
[Longueur, format, interdits explicites]
```

---

*Bibliothèque versionnée v1.0 — accompagne la formation « Créer des agents dans M365 Copilot ».*
