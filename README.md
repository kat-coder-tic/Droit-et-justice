# ⚖️ DROIT & JUSTICE — STMG Terminale

Jeu pédagogique en HTML/CSS/JavaScript vanilla, conçu pour les élèves de terminale STMG en économie-droit. Le joueur incarne un avocat junior qui traite des affaires juridiques progressives.

---

## 🎯 Objectifs pédagogiques

Le jeu entraîne les élèves aux compétences exigées au BAC STMG :

- Qualifier juridiquement des faits à partir d'un dossier documentaire
- Identifier les règles de droit pertinentes (articles du Code civil et du Code du travail)
- Construire un syllogisme juridique avec les connecteurs du BAC (*"Selon l'article…"*, *"En l'espèce,"*, *"En conséquence,"*)
- Sélectionner des preuves pertinentes parmi des distracteurs crédibles
- Répondre à des contre-arguments en s'appuyant sur des textes de loi
- Organiser une synthèse juridique

**Règle d'or : l'élève ne rédige jamais.** Il clique, sélectionne, classe et assemble.

---

## 📚 Programme couvert

| Dossier | Thème | Notions clés |
|---------|-------|--------------|
| 01 | Thème 5 — Le Contrat | Formation du contrat, inexécution, mise en demeure, résolution |
| 02 | Thème 6 — La Responsabilité | Responsabilité extracontractuelle, fait personnel, fait d'autrui (commettant/préposé) |
| 03 | Thème 7 — Le Travail Salarié | CDI, licenciement pour motif personnel, procédure, entretien préalable |
| 04 | Thème 5 — Le Contrat | Dol, vice du consentement, nullité relative, dommages et intérêts |
| 05 | Thème 6 — La Responsabilité | Responsabilité du fait des choses, gardien, présomption, exonération |
| 06 | Thème 7 — Le Travail Salarié | Clause de non-concurrence, 4 conditions de validité, sanction de la violation |
| 07 | Thème 8 — Entreprendre | Concurrence déloyale par imitation, parasitisme, action en concurrence déloyale, art. 1240 |
| 08 | Thème 8 — Entreprendre | Contrat de franchise, obligations du franchisé, clause d'approvisionnement exclusif, résiliation |

---

## 🕹️ Structure de chaque affaire

Chaque dossier suit 4 étapes jouables + une synthèse finale :

### Étape 1 — Sélection des preuves
L'élève lit des documents (PV, contrats, emails, certificats médicaux, relevés bancaires…) et doit identifier ceux qui sont juridiquement pertinents. Des **distracteurs crédibles** sont inclus : des documents qui semblent utiles mais ne prouvent aucune condition juridique. Les explications s'affichent en vert/rouge après validation.

### Étape 2 — Qualification juridique
Deux questions successives à choix unique. La première qualifie la situation (type de contrat, type de responsabilité, type de rupture). La seconde approfondit (validité, régime applicable, conditions). Un feedback pédagogique immédiat explique chaque réponse.

### Étape 3 — Syllogisme juridique (méthode BAC)
L'élève construit son argumentaire en trois blocs, comme dans les réponses 2 et 3 du sujet de BAC :

- **Majeure** : sélection du connecteur (*"Selon l'article"*) + sélection du fragment de règle de droit
- **Mineure** : sélection du connecteur (*"En l'espèce,"*) + sélection du fragment de faits
- **Conclusion** : sélection du connecteur (*"En conséquence,"*) + sélection de la solution juridique

Un aperçu de la phrase complète s'affiche en temps réel. Les bons/mauvais choix sont colorés à la validation.

### Étape 4 — Contre-argumentation
L'avocat adverse présente deux objections successives. L'élève choisit la meilleure réponse juridique parmi trois options. La jauge de conviction du juge évolue en fonction des choix. La bonne réponse cite toujours un article de loi ou une preuve du dossier.

### Synthèse finale
L'élève place des notions-clés dans les bonnes zones (qualification → règle → faits → solution) par clic successif. Des distracteurs issus d'autres affaires sont mêlés.

---

## 🎮 Système de jeu

- **Progression verrouillée** : les dossiers 02 et 03 se débloquent après le précédent ; les dossiers 04, 05 et 06 (niveau 2) se débloquent après 01, 02 et 03
- **Score en direct** : affiché dans l'en-tête de jeu
- **Indices** : 3 indices par affaire (le mentor donne un conseil ciblé sur l'étape en cours)
- **Feedback immédiat** : chaque réponse déclenche une explication pédagogique
- **Verdict** : barres de score par compétence + conseils personnalisés du mentor
- **Badges** : obtenus à 80% de score (Maître du Contrat, Expert Responsabilité, etc.)
- **XP et réputation** : progression de Stagiaire à Avocat Senior
- **Sauvegarde automatique** : via `localStorage` — la progression est conservée entre les sessions

---

## 🚀 Déploiement

Le jeu tient en **un seul fichier HTML** autonome, sans dépendance externe (hors police Google Fonts).

### Sur GitHub Pages

```bash
# 1. Créer un dépôt GitHub (ex : droit-et-justice)
# 2. Uploader le fichier index.html
# 3. Dans les paramètres du dépôt : Settings → Pages → Source : main branch / root
# 4. Le jeu est accessible à : https://[username].github.io/[nom-du-depot]/
```

### En local (sans installation)

Double-cliquer sur `index.html` dans l'explorateur de fichiers — le jeu s'ouvre directement dans le navigateur.

### Sur un ENT ou Google Sites

Héberger le fichier sur un service de fichiers statiques (GitHub Pages, Netlify, GitHub Gist…) et intégrer l'URL via un iframe ou un lien direct.

---

## 🔧 Personnalisation

Le code est structuré pour être modifiable sans compétence avancée en JavaScript.

### Ajouter une nouvelle affaire

Dans le fichier JS, le tableau `CASES` contient toutes les affaires. Pour en ajouter une, copier la structure d'un cas existant et modifier :

```javascript
CASES[7] = {
  title: "Titre de l'affaire",
  theme: "Thème X — Intitulé",
  client: "Nom du client",
  steps: [
    // Étape 1 : type "docs"
    // Étape 2 : type "quali"
    // Étape 3 : type "syllog"
    // Étape 4 : type "contre"
  ],
  synth: { ... }
}
```

Puis ajouter la carte correspondante dans le HTML (section `#screen-map`) et la logique de déverrouillage dans la fonction `updMap()`.

### Modifier le contenu d'un dossier existant

Rechercher `title:"L'achat qui tourne mal"` (ou tout autre titre) dans le code source pour localiser le bon objet et modifier directement les textes, documents, fragments de syllogisme ou objections.

### Modifier les couleurs

Les variables CSS au sommet du fichier (`--navy`, `--gold`, `--green`, etc.) centralisent toute la palette.

---

## ♿ Accessibilité et compatibilité

- Compatible desktop et mobile (layout responsive)
- Sur mobile : le syllogisme fonctionne par double-clic (connecteur puis fragment) sans drag & drop
- Testé sur Chrome, Firefox, Safari, Edge
- Fermeture des overlays par touche `Échap`
- Pas de dépendance à un backend — fonctionne hors connexion une fois la page chargée (sauf la police Google Fonts)

---

## 📁 Structure du projet

```
index.html   ← fichier unique, tout-en-un
README.md                ← ce fichier
```

Tout le CSS et le JavaScript sont embarqués dans le HTML. Pour un projet multi-fichiers (utile si vous souhaitez versionner séparément) :

```
index.html
style.css
script.js
```

---

## 📝 Notes pédagogiques

Ce jeu est un **outil d'entraînement méthodologique**, pas un cours magistral. Il est conçu pour être utilisé **après l'enseignement des notions**, en révision ou en évaluation formative. Il ne remplace pas l'étude du cours ni la rédaction complète.

Les articles cités sont issus du programme officiel de terminale STMG (Bulletin Officiel — Annexe 1) et correspondent aux thèmes 5, 6 et 7 de l'enseignement de droit :
- Code civil : art. 1101, 1109, 1132, 1137, 1178, 1217, 1240, 1242, 1344
- Code du travail : art. L1232-1, L1232-2, L1235-2
- Jurisprudence : Cass. soc. 10 juillet 2002 (clause de non-concurrence)

---

---

## 📋 Couverture programme — Vue d'ensemble

| Thème | Dossiers | Sous-thèmes couverts |
|-------|----------|----------------------|
| T5 — Le Contrat | 01, 04 | Formation, inexécution, mise en demeure, dol, nullité relative |
| T6 — La Responsabilité | 02, 05 | Fait personnel, fait d'autrui, fait des choses, conditions, exonération |
| T7 — Le Travail Salarié | 03, 06 | Licenciement procédure, entretien préalable, clause de non-concurrence |
| T8 — Entreprendre | 07, 08 | Concurrence déloyale, contrat de franchise, obligations contractuelles |

---

*Réalisé avec Claude — Cabinet Leclerc & Associés — STMG Terminale*
