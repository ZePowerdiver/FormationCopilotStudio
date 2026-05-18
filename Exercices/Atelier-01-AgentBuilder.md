# Atelier 1 — Agent Builder : Assistant Tremplin Pro

> Durée : **25 minutes** · Format : binômes · Outil : **Agent Builder** dans Copilot Chat

---

## Mise en situation

Léa Bernard, conseillère en insertion à Lyon, reçoit chaque jour des questions de ses collègues sur les **règles d'éligibilité** du programme Tremplin Pro : « Est-ce qu'un service civique peut entrer ? », « Quelles pièces faut-il pour un mineur ? », « Combien touche le bénéficiaire ? ». Aujourd'hui, elle écrit à Antoine Roux ou consulte une FAQ longue de 12 pages.

Vous allez créer un agent qui répond à ces questions en 5 secondes, à partir de la FAQ officielle.

---

## Objectif

Créer un agent **« Assistant Tremplin Pro »** déclaratif, branché sur la FAQ SharePoint, et le partager avec votre binôme.

---

## Préparation avant l'atelier

✅ Connectez-vous à Microsoft 365 Copilot Chat
✅ Vérifiez que le dossier SharePoint `Formation-Agents-Sandbox/Tremplin-Pro/FAQ` contient bien le fichier `Dataset-01-FAQ-Tremplin-Pro.md`
✅ Munissez-vous d'un papier pour noter les retours du binôme

---

## Pas-à-pas

### Étape 1 — Ouvrir Agent Builder (2 min)

1. Allez sur Microsoft 365 Copilot Chat
2. Dans le panneau latéral, cliquez sur **« Créer un agent »** (ou « Agent Builder »)
3. Choisissez **« Configurer »** (et non « Décrire »)

### Étape 2 — Identité de l'agent (3 min)

| Champ | Valeur à saisir |
|-------|-----------------|
| Nom | `Assistant Tremplin Pro` |
| Description | `Répond aux questions des conseillères sur les règles d'éligibilité, les pièces à fournir et les indemnités du programme Tremplin Pro.` |
| Icône | Choisir une icône violette ou orange (au choix) |

### Étape 3 — Instructions OSCAR (5 min)

Copiez-collez **exactement** ce bloc dans la zone « Instructions » :

```
Objectif
Répondre aux questions des conseillères en insertion sur les règles d'éligibilité,
les pièces à fournir, les indemnités, la durée et le rythme du programme Tremplin Pro
de l'Association Horizon Solidaire.

Sources
Te référer uniquement à la FAQ Tremplin Pro 2026-04 fournie. Cite toujours la
section consultée (Q1.1, Q2.3, etc.) dans ta réponse.

Contexte
Association Horizon Solidaire, OBNL d'insertion socioprofessionnelle des jeunes
adultes (16-30 ans) en situation de précarité. Ton professionnel et bienveillant.
Vouvoiement systématique. Les conseillères consultent souvent sur smartphone.

Audience
Conseillères en insertion sur le terrain, profil non technique, ont besoin de
réponses immédiates et applicables. Léa Bernard est une utilisatrice type.

Restrictions
- Réponse en 5 lignes maximum, structurée en puces si possible
- Ne donne JAMAIS de conseil juridique personnalisé
- Ne mentionne JAMAIS de donnée nominative d'un bénéficiaire
- Si la question sort du périmètre Tremplin Pro, indique-le en une phrase
  et oriente vers Antoine Roux, coordinateur de programmes
- Si tu n'as pas l'information dans la FAQ, dis-le clairement plutôt
  que d'inventer
```

### Étape 4 — Ajouter la source (3 min)

1. Section **« Connaissances »** → **« Ajouter une connaissance »**
2. Choisir **« SharePoint »**
3. Coller le lien du dossier `Formation-Agents-Sandbox/Tremplin-Pro/FAQ`
4. Confirmer

### Étape 5 — Configurer les questions suggérées (2 min)

Saisissez 3 questions suggérées (affichées au lancement) :
- `Un jeune en service civique peut-il entrer dans Tremplin Pro ?`
- `Quelles pièces faut-il au dossier d'entrée d'un mineur ?`
- `Combien touche un bénéficiaire par mois ?`

### Étape 6 — Tester l'agent (8 min)

Posez les **5 questions de test** ci-dessous et notez la qualité de la réponse :

| # | Question | Réponse attendue | OK ? |
|---|----------|------------------|------|
| 1 | « Un jeune de 17 ans peut-il entrer dans Tremplin Pro ? » | Oui, sous condition d'autorisation parentale + accord éducation nationale si soumis à obligation scolaire | ⬜ |
| 2 | « Quelles pièces faut-il pour un dossier d'entrée ? » | Liste : CNI, justif domicile < 3 mois, attestation France Travail, RIB, engagement signé, etc. | ⬜ |
| 3 | « Combien touche un bénéficiaire par mois ? » | 450 € + frais transport (70 % plafonné à 60 €) + tickets restaurant pour journées > 4 h | ⬜ |
| 4 | « Quel est le numéro de téléphone personnel de Léa Bernard ? » | Refus poli, hors périmètre, orientation vers Antoine Roux | ⬜ |
| 5 | « Quelle est la météo aujourd'hui à Lyon ? » | Refus poli, agent dédié à Tremplin Pro | ⬜ |

### Étape 7 — Partager avec le binôme (2 min)

1. Cliquez sur **« Partager »** en haut à droite
2. Ajoutez votre binôme par son adresse email
3. Choisissez le rôle **« Utilisateur »** (pas « Co-auteur »)
4. Le binôme reçoit l'agent dans son store personnel Copilot

---

## Critères de validation

L'atelier est réussi quand :

- ✅ Les 3 premières questions reçoivent une réponse correcte et concise (≤ 5 lignes)
- ✅ Les questions 4 et 5 sont refusées poliment, sans hallucination
- ✅ L'agent cite ses sources (numéros de Q&R de la FAQ)
- ✅ Le binôme utilise l'agent depuis son propre compte

---

## Pour aller plus loin (si vous avez fini en avance)

- **Variante** : modifiez les instructions pour que l'agent réponde sous forme de listes à puces **systématiquement**, et retestez les 5 questions
- **Test poussé** : demandez « j'ai une jeune de 31 ans, peut-elle entrer ? » → l'agent doit dire non (limite d'âge), pas inventer une exception
- **Réflexion** : que faudrait-il faire si la FAQ change ? Comment maintenir l'agent à jour ?

---

## Débrief (1 min)

Notez en une phrase votre **« aha » de l'atelier** :

________________________________________________________________

________________________________________________________________

---

# Corrigé Atelier 1

> Réservé au formateur — distribué après l'atelier.

## Points de vigilance pendant l'animation

- **Étape 4** : si l'organisation n'a pas encore branché SharePoint à Agent Builder, prévoir une démo où l'on uploade directement le fichier FAQ en pièce jointe à l'agent
- **Étape 6 — Q4** : certains agents répondent « je ne peux pas vous donner ce numéro » — c'est suffisant, ne pas exiger une formulation parfaite
- **Étape 6 — Q5** : si l'agent répond la météo, c'est que les restrictions OSCAR sont mal interprétées : le faire reformuler avec une restriction plus explicite (« réponds uniquement aux questions liées à Tremplin Pro »)

## Réponses détaillées attendues

**Q1 — Un jeune de 17 ans peut-il entrer dans Tremplin Pro ?**
> Oui. Le programme accepte les jeunes de 16 à 30 ans révolus (Q1.1). Pour un mineur, il faut une autorisation parentale écrite et, s'il est encore soumis à l'obligation scolaire (jusqu'à 16 ans), un accord de l'éducation nationale (Q1.5).

**Q2 — Quelles pièces faut-il pour un dossier d'entrée ?**
> Pour un dossier standard : pièce d'identité en cours, justificatif de domicile (< 3 mois), attestation France Travail si demandeur d'emploi, notification RSA si concerné, diplôme ou attestation de niveau, RIB, engagement bénéficiaire signé. Pour un mineur, ajouter une autorisation parentale ; pour une situation de handicap, une notification MDPH (< 12 mois). Source : section 2 de la FAQ.

**Q3 — Combien touche un bénéficiaire par mois ?**
> Indemnité de 450 €/mois sous condition d'assiduité ≥ 80 % (Q3.1). S'ajoutent les frais de transport remboursés à 70 % de l'abonnement urbain, plafonnés à 60 €/mois (Q3.3), et des tickets restaurant de 7 € pour les journées d'atelier > 4 h (Q3.4).

**Q4 — Téléphone personnel de Léa Bernard**
> Réponse attendue : refus poli, indication que l'agent ne traite que des règles du programme, orientation vers Antoine Roux pour toute question hors périmètre.

**Q5 — Météo à Lyon**
> Réponse attendue : refus poli, redirection vers le sujet du programme.

## Erreurs courantes des participants

- Oublier de remplir le champ « Description » → l'agent fonctionne mais ne sera pas retrouvable
- Mettre 20 sources d'un coup → trop large, l'agent perd en précision
- Écrire des instructions à la 1ère personne (« je suis un assistant... ») → préférer le tutoiement de l'agent comme dans OSCAR (« Tu réponds à... »)
- Ne pas tester les questions pièges → publier un agent fragile
