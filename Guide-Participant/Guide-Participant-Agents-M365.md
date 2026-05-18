# Guide Participant
## Créer des agents dans Microsoft 365 Copilot

> Formation interactive — 120 minutes
> Fil rouge : Association Horizon Solidaire (OBNL)
> Méthode : OSCAR

---

## Bienvenue

Ce guide vous accompagne pendant la formation **et** après. Vous y trouverez la théorie, les fiches d'atelier, la méthode OSCAR, un gabarit imprimable et un plan d'action personnel.

**Comment l'utiliser** :
- Pendant la session, suivez le plan général et notez vos questions
- Pendant les ateliers, utilisez les fiches dédiées comme support pas-à-pas
- Après la session, gardez ce guide à portée de main pour vos premiers agents en autonomie

---

## Sommaire

1. Comprendre les agents M365 Copilot
2. La méthode OSCAR
3. Atelier 1 — Agent Builder
4. Atelier 2 — Copilot Studio
5. Gouvernance, sécurité, ROI
6. Gabarit OSCAR imprimable
7. Glossaire
8. Plan d'action personnel

---

## 1. Comprendre les agents M365 Copilot

### 1.1 Qu'est-ce qu'un agent ?

Un **agent** est un Copilot spécialisé que vous configurez pour un usage précis. Là où Copilot Chat répond à tout, un agent :

- a un **but unique** que vous définissez
- s'appuie sur **les sources que vous lui donnez** (et pas le web entier)
- s'adresse à une **audience identifiée** (votre équipe, votre service, vos partenaires)
- respecte des **règles** que vous écrivez (ce qu'il doit faire, ce qu'il ne doit jamais faire)

En une image : Copilot Chat est un assistant généraliste, un agent est un assistant spécialisé.

### 1.2 Les trois familles d'agents

| Famille | Outil | Idéal pour | Compétences requises |
|---------|-------|------------|----------------------|
| Agent déclaratif | **Agent Builder** dans Copilot Chat | Questions-réponses sur un ensemble de documents | Aucune compétence technique |
| Agent conversationnel avancé | **Copilot Studio** | Dialogues multi-tours, connecteurs, données structurées | Bonne connaissance métier |
| Agent autonome | **Copilot Studio** + déclencheurs | Actions exécutées sans intervention humaine | Compétences Power Platform |

> **Règle de choix simple** : commencez toujours par Agent Builder. Passez à Copilot Studio quand vous avez besoin de connecteurs externes, de déclencheurs ou d'actions.

### 1.3 Trois cas concrets chez Horizon Solidaire

| Cas | Famille recommandée | Pourquoi |
|-----|---------------------|----------|
| Léa demande « est-ce qu'un service civique peut entrer dans Tremplin Pro ? » | Agent déclaratif | Question-réponse sur une FAQ documentaire |
| Antoine veut un rapport trimestriel FSE+ pré-rédigé à partir des indicateurs Excel et des bilans Word | Conversationnel avancé | Combiner plusieurs sources + dialogue itératif |
| Marc veut une alerte automatique 48 h avant chaque échéance de feuille de temps non signée | Agent autonome | Déclenchement sur événement, sans utilisateur |

---

## 2. La méthode OSCAR

OSCAR est la grille que vous utiliserez pour **rédiger les instructions** de tous vos agents (et pour structurer vos prompts dans Copilot Chat).

### 2.1 Les cinq lettres

| Lettre | Question à se poser | Exemple Horizon |
|--------|---------------------|-----------------|
| **O — Objectif** | Quel est le but unique de cet agent ? | Répondre aux questions des conseillères sur les règles d'éligibilité Tremplin Pro |
| **S — Sources** | Sur quels documents s'appuyer ? | FAQ Tremplin Pro v2026-04 + règlement du programme |
| **C — Contexte** | Quelle organisation, quel ton, quelles contraintes ? | Association Horizon Solidaire, ton professionnel et bienveillant, vouvoiement |
| **A — Audience** | Qui pose les questions ? | Conseillères en insertion, profil non technique, souvent sur smartphone |
| **R — Restrictions** | Que ne doit-il jamais faire ? | Pas de conseil juridique, pas de données personnelles bénéficiaires, refus poli hors périmètre |

### 2.2 Avant / après

**Instructions floues** :
> Tu es un assistant qui aide les conseillères de l'association sur le programme Tremplin Pro. Réponds aux questions qu'on te pose.

**Instructions OSCAR** :
> **Objectif** — Répondre aux questions des conseillères en insertion sur les règles d'éligibilité, les pièces à fournir et les indemnités du programme Tremplin Pro.
>
> **Sources** — Te référer uniquement à la FAQ Tremplin Pro 2026-04 et au règlement interne du programme déposé dans SharePoint.
>
> **Contexte** — Association Horizon Solidaire, OBNL d'insertion socioprofessionnelle. Ton professionnel et bienveillant, vouvoiement. Réponses concrètes et courtes (5 lignes maximum).
>
> **Audience** — Conseillères en insertion sur le terrain, profil non technique, consultent souvent sur smartphone.
>
> **Restrictions** — Ne donne jamais de conseil juridique personnalisé. Ne mentionne aucune donnée nominative d'un bénéficiaire. Si la question sort du périmètre, indique-le en une phrase et oriente vers Antoine Roux, coordinateur de programmes.

La version OSCAR produit des réponses bien plus utiles, parce qu'elle resserre l'agent sur sa mission.

### 2.3 Erreurs fréquentes à éviter

- **Trop large** : « réponds à toutes les questions sur l'association » → l'agent devient incohérent
- **Trop court** : 3 lignes d'instructions → l'agent improvise
- **Trop long** : 3 pages d'instructions → l'agent perd le fil
- **Pas de R** : sans restrictions explicites, l'agent répond à tout, y compris hors sujet
- **Sources implicites** : « tu sais tout sur l'association » → non, il ne sait que ce que vous indexez

---

## 3. Atelier 1 — Agent Builder (25 min)

### Objectif

Créer un agent **« Assistant Tremplin Pro »** qui répond aux questions des conseillères sur les règles d'éligibilité, les pièces à fournir et les indemnités du programme.

### Étapes pas-à-pas

1. **Ouvrir** Copilot Chat dans votre navigateur (copilot.microsoft.com → Copilot M365)
2. **Cliquer** sur « Agent Builder » dans le panneau latéral (icône +)
3. **Saisir** le nom de l'agent : `Assistant Tremplin Pro`
4. **Décrire** l'agent en 200 caractères (utilisez le prompt 4 de la bibliothèque pour générer 3 versions)
5. **Coller** les instructions OSCAR fournies dans la fiche d'atelier
6. **Ajouter** la source : SharePoint → `Formation-Agents-Sandbox/Tremplin-Pro/FAQ`
7. **Choisir** une icône (proposée par défaut ou personnalisée)
8. **Sauvegarder** et tester avec les 5 questions de la fiche d'atelier
9. **Partager** avec votre binôme via le bouton « Partager »

### Critères de réussite

- L'agent répond correctement aux 5 questions de test
- Il refuse poliment une question hors périmètre
- Le binôme peut l'utiliser depuis son propre Copilot Chat

### Questions de test à poser

1. « Un jeune de 17 ans peut-il entrer dans Tremplin Pro ? »
2. « Quelles pièces faut-il pour un dossier d'entrée ? »
3. « Combien touche un bénéficiaire par mois ? »
4. *(piège)* « Quel est le numéro de téléphone personnel de Léa Bernard ? »
5. *(piège)* « Quelle est la météo aujourd'hui à Lyon ? »

---

## 4. Atelier 2 — Copilot Studio (35 min)

### Objectif

Créer un agent **« Conseiller Reporting FSE+ »** capable de pré-rédiger un rapport trimestriel à partir des indicateurs Excel et des bilans bénéficiaires, et de publier un brouillon dans Teams.

### Étapes pas-à-pas

1. **Ouvrir** Copilot Studio (`copilotstudio.microsoft.com`)
2. **Créer** un nouvel agent → « Construire à partir d'une description »
3. **Décrire** l'agent en langage naturel (un paragraphe), Copilot Studio génère un brouillon
4. **Affiner** les instructions générées en y appliquant OSCAR (suivre la fiche d'atelier)
5. **Ajouter** les **connaissances** :
   - Fichier Excel `Indicateurs-FSE-T1-2026.csv`
   - Dossier SharePoint `/Programmes/Tremplin-Pro/Bilans-mi-parcours`
6. **Créer** une **action** Power Automate :
   - Déclencheur : quand l'agent reçoit « publie le brouillon »
   - Action : Teams — Publier un message dans le canal « Reporting FSE »
7. **Tester** dans le volet « Test » de Copilot Studio
8. **Publier** vers Microsoft 365 Copilot (canal de test)

### Critères de réussite

- L'agent produit une trame de rapport trimestriel structurée
- Il cite ses sources (indicateurs et bilans utilisés)
- Le brouillon est publié dans le canal Teams au bon endroit
- Aucune donnée nominative n'apparaît dans la trame

### Question de test à poser

> « Prépare-moi une trame de rapport FSE+ pour le T1 2026 : synthèse des entrées, sorties positives, écarts par rapport à la cible, et 3 points de vigilance à présenter au bailleur. »

---

## 5. Gouvernance, sécurité, ROI

### 5.1 Cinq questions à se poser avant de publier

1. **Qui peut consommer cet agent ?** — restreindre à un groupe Azure AD pertinent, pas à toute l'organisation par défaut
2. **Quelles données voit cet agent ?** — vérifier que les sources indexées ne contiennent pas de données sensibles non protégées
3. **Que se passe-t-il si l'agent se trompe ?** — prévoir un message d'orientation vers un humain
4. **Qui maintient cet agent ?** — désigner un propriétaire et un suppléant
5. **Quand sera-t-il revu ?** — planifier une revue trimestrielle

### 5.2 Les garde-fous M365

| Niveau | Contrôle | Qui le gère |
|--------|----------|-------------|
| Tenant | Quels utilisateurs peuvent créer / publier des agents | Admin M365 |
| Environnement | Environnements Power Platform dédiés au pilote, à la prod | Admin Power Platform |
| Données | Politiques DLP, classification, sensibilité | Admin sécurité |
| Agent | Public cible, instructions, sources, actions | Propriétaire de l'agent |

### 5.3 Mesurer le ROI

Un agent rentable suit la logique simple suivante :

```
Gain mensuel = nb de conversations × temps gagné par conversation × coût horaire
Coût agent  = heures de création + maintenance trimestrielle
ROI à 3 mois = (gain cumulé - coût) / coût
```

Le **prompt 12** de la bibliothèque fait ce calcul automatiquement.

---

## 6. Gabarit OSCAR imprimable

Découpez ou photocopiez cette page. À utiliser pour préparer chaque agent.

```
┌─────────────────────────────────────────────────────────┐
│  AGENT : ........................................        │
│  AUTEUR : .....................  DATE : ............    │
├─────────────────────────────────────────────────────────┤
│  O — OBJECTIF (1-2 phrases, but unique)                 │
│  ...................................................   │
│  ...................................................   │
├─────────────────────────────────────────────────────────┤
│  S — SOURCES (chemins exacts, version)                  │
│  □ ............................................        │
│  □ ............................................        │
│  □ ............................................        │
├─────────────────────────────────────────────────────────┤
│  C — CONTEXTE (organisation, ton, contraintes)          │
│  ...................................................   │
│  ...................................................   │
├─────────────────────────────────────────────────────────┤
│  A — AUDIENCE (profil, niveau, support de lecture)      │
│  ...................................................   │
├─────────────────────────────────────────────────────────┤
│  R — RESTRICTIONS (interdits, format, longueur)         │
│  □ Ne jamais : ..................................      │
│  □ Format : .....................................      │
│  □ Hors périmètre → ............................       │
└─────────────────────────────────────────────────────────┘
```

---

## 7. Glossaire

| Terme | Définition |
|-------|------------|
| Agent | Copilot spécialisé avec instructions, sources, actions et public limités |
| Agent Builder | Interface simplifiée de création d'agent intégrée à Copilot Chat |
| Copilot Studio | Plateforme complète de création d'agents, ex-Power Virtual Agents |
| Connecteur | Pont entre Copilot Studio et un service externe (Dynamics, Salesforce, etc.) |
| Déclencheur | Événement qui démarre une action automatique de l'agent |
| DLP | Data Loss Prevention — règles d'empêchement de fuite de données |
| FSE+ | Fonds Social Européen Plus, principal cofinanceur de Tremplin Pro |
| Knowledge source | Document ou jeu de données indexé pour fournir des réponses à l'agent |
| Power Automate | Plateforme d'automatisation Microsoft, utilisée pour les actions d'agent |
| Tenant | Instance Microsoft 365 d'une organisation |

---

## 8. Plan d'action personnel

À remplir avant de quitter la salle.

**Mon premier agent post-formation**

- Nom de l'agent : __________________________________
- Famille (Agent Builder / Copilot Studio) : __________________
- Audience : __________________________________
- Sources principales : __________________________________
- Première date de test : __________________________________
- Date de mise en production prévue : __________________________________

**Mes deux questions à poser au référent IA**

1. __________________________________
2. __________________________________

**Mon engagement post-formation** *(à signer)*

Je m'engage à publier mon premier agent à un public restreint dans les **15 jours** qui suivent cette formation, et à partager mon retour d'expérience avec le groupe.

Signature : __________________  Date : __________

---

*Guide Participant v1.0 — © Formation interne, usage pédagogique.*
