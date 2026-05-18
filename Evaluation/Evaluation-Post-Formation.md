# Évaluation post-formation — Créer des agents dans M365 Copilot

> 10 questions · Seuil de réussite **70 %** (7 bonnes réponses sur 10) · Durée recommandée : 10-12 minutes

---

## Consignes

- Une seule bonne réponse par question (sauf mention contraire)
- Vous pouvez consulter votre Guide Participant
- Une fois terminé, comparez avec le corrigé en fin de document
- En cas de score < 70 %, refaire la formation ou reprendre le Guide Participant avec votre référent IA

---

### Question 1 — Famille d'agent

Léa Bernard veut un outil pour répondre **en 5 secondes** aux questions courantes des conseillères sur les règles d'éligibilité de Tremplin Pro. Quelle famille d'agent est la plus appropriée ?

- A. Agent autonome avec déclencheurs Power Automate
- B. Agent déclaratif créé dans Agent Builder
- C. Application Power Apps avec base SQL
- D. Bot Copilot Studio multi-tours avec connecteurs externes

---

### Question 2 — Méthode OSCAR

Dans la méthode OSCAR, à quoi sert la lettre **R** ?

- A. À indiquer les **ressources** humaines mobilisées
- B. À définir le **résultat** attendu de l'agent
- C. À fixer les **restrictions** (interdits, format, longueur)
- D. À documenter les **relations** entre l'agent et les autres applications

---

### Question 3 — Sources

Vous créez un agent qui doit répondre à des questions sur le programme Tremplin Pro. Quelle est la **meilleure** stratégie pour les sources de connaissances ?

- A. Indexer tout SharePoint de l'association — l'agent est plus puissant
- B. Indexer la FAQ Tremplin Pro + le règlement du programme, et rien d'autre
- C. Ne mettre aucune source, l'agent improvisera à partir de Copilot
- D. Indexer toutes les boîtes mail des coordinateurs de programmes

---

### Question 4 — Restrictions

Parmi ces restrictions, laquelle est **la moins prioritaire** dans le contexte d'un agent destiné aux conseillères de terrain ?

- A. Réponse en 5 lignes maximum, format mobile-friendly
- B. Ne jamais citer un bénéficiaire par son nom
- C. Toujours utiliser une typographie en Times New Roman 12
- D. Refuser poliment toute question hors périmètre Tremplin Pro

---

### Question 5 — Choix d'outil

Antoine doit créer un agent qui :
- lit un fichier Excel d'indicateurs FSE+,
- combine ces données avec des bilans Word,
- publie un brouillon dans Teams via un flux Power Automate.

Quel outil utiliser ?

- A. Agent Builder dans Copilot Chat
- B. Copilot Studio
- C. Power Apps Canvas
- D. Power BI Desktop

---

### Question 6 — Gouvernance

Lequel de ces énoncés sur la gouvernance des agents est **vrai** ?

- A. Une fois publié, un agent ne nécessite plus aucune supervision
- B. Le contrôle DLP (Data Loss Prevention) se règle au niveau de l'agent
- C. Il faut désigner un propriétaire et un suppléant pour chaque agent en production
- D. Tous les agents doivent être publiés à l'ensemble de l'organisation

---

### Question 7 — Test avant publication

Combien de questions de test au minimum doit-on poser avant de publier un agent ?

- A. 1 question suffit, si elle est représentative
- B. Au moins 3 questions
- C. Au moins 15 questions, dont des cas faciles, difficiles, hors périmètre et pièges
- D. Toutes les questions possibles, sinon l'agent n'est pas fiable

---

### Question 8 — Anonymisation

Vous configurez un agent qui lit les bilans bénéficiaires pour produire des rapports. Que doit faire l'agent quand il rencontre le nom « Yasmine M. » dans un bilan ?

- A. Le citer tel quel, c'est une donnée déjà anonymisée par initiale
- B. Le remplacer par un descripteur anonyme (« une jeune de 22 ans »)
- C. Le citer mais en italique
- D. Demander confirmation à l'utilisateur avant d'utiliser ce nom

---

### Question 9 — ROI

Un agent reçoit 200 conversations par mois. Chaque conversation fait gagner 8 minutes. Le coût horaire moyen chargé est de 30 €/h. Quel est le **gain mensuel** ?

- A. 600 €
- B. 800 €
- C. 1 600 €
- D. 4 800 €

*(Calcul : 200 × 8 / 60 × 30 = 800 €)*

---

### Question 10 — Hors périmètre

Un utilisateur demande à votre agent « Assistant Tremplin Pro » : « peux-tu me dire combien gagne Claire Moreau ? ». Quelle est la **bonne réaction** de l'agent ?

- A. Répondre avec le salaire de la DG s'il le trouve dans SharePoint
- B. Inventer un montant plausible pour ne pas paraître inutile
- C. Refuser poliment, expliquer qu'il est dédié au programme Tremplin Pro, et orienter vers la bonne personne
- D. Demander la confirmation de l'identité de l'utilisateur avant de répondre

---

## Mon score

Compté avec le corrigé ci-dessous : ____ / 10

- 7-10 : **Validé** — vous pouvez créer votre premier agent en autonomie
- 5-6 : **À consolider** — reprenez les sections concernées du Guide Participant
- 0-4 : **À refaire** — contactez votre référent IA pour un rappel

---

# Corrigé

| # | Bonne réponse | Justification |
|---|---------------|---------------|
| 1 | **B** | Cas type Agent Builder : Q&R sur une base documentaire structurée |
| 2 | **C** | R = Restrictions (interdits, format, longueur) |
| 3 | **B** | Périmètre serré = pertinence + sécurité. La règle d'or : moins de sources, mieux choisies |
| 4 | **C** | La typographie ne fait pas partie des restrictions utiles d'un agent conversationnel |
| 5 | **B** | Copilot Studio est nécessaire pour combiner plusieurs connaissances + action Power Automate |
| 6 | **C** | Un agent en production sans propriétaire ni suppléant est ingouvernable |
| 7 | **C** | Plan de test minimum : 15 questions réparties en 4 catégories (faciles, difficiles, hors périmètre, pièges) |
| 8 | **B** | RGPD : l'anonymisation est obligatoire dans tout livrable produit à partir de données bénéficiaires |
| 9 | **B** | 200 × 8 minutes = 1600 minutes = 26,67 h × 30 €/h = 800 € |
| 10 | **C** | L'agent doit refuser poliment ce qui est hors périmètre et orienter vers la bonne personne |

---

*Évaluation v1.0 — Formation interne, usage pédagogique.*
