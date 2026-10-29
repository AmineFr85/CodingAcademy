🎓 Algorithms from Zero to Hero — Coding Academy

> **Application pédagogique interactive d'algorithmique** pour les lycéens tunisiens
> (2ᵉ Info · 3ᵉ Sciences, 3ᵉ SI, Bac SI) — conçue et réalisée par
> **Mr. Amine FARJALLAH**.

Le site accompagne l'élève du **découverte** à la **maîtrise** selon la boucle
institutionnelle : **PRÉSENTER** (📖 Cours) → **DÉMONTRER** (▶️ Simulations)
→ **ÉVALUER** (✅ S'évaluer), avec exécution pas à pas des algorithmes,
variables animées et corrections détaillées immédiates.

---

# ✨ Fonctionnalités

### 📖 Cours détaillés
- Cours complets par rubrique : structures simples, structures de contrôle
  (TDO / TDNT), sous-programmes, tableaux & matrices, enregistrements, tri,
  recherche, arithmétique, approximation, structures répétitives…
- Blocs algorithme (convention tunisienne) et équivalent Python côte à côte,
  avec bouton « Copier ».
- Schémas de principes, tableaux de déclarations et visualisations animées.

### ▶️ Simulations pas à pas
- Exécution **manuelle** (étape par étape) ou **automatique** (lecture auto,
  vitesse réglable) de chaque algorithme.
- Machine à états visuelle : variables, mémoire, curseurs d'exécution,
  comparisons et permutations animées (tris, récursivité, fichiers
  séquentiels…).
- Voice-over pédagogique à chaque étape (libellés énoncés).

### ✅ Évaluations interactives — 8 familles de questions
| Type | Description |
|---|---|
| Vrai ou Faux | affirmation à valider |
| QCM | choix multiples (A–F) |
| Rôle du programme | algorithme à gauche, propositions à droite réparties uniformément |
| Résultat du programme | données saisies + algorithme, sortie à deviner |
| Correspondance | programmes ↔ rôles, rangées alignées, flèches SVG |
| Relier par flèches | éléments ↔ significations, plateau à rangées alignées |
| Mettre en ordre | réordonner les lignes d'un algorithme (↑ / ↓) |
| Compléter | insérer les blocs manquants d'un programme |

- Feedback immédiat vert/rouge + explication détaillée et correction complète,
  score final et bilan par famille de questions.

### 🛡️ Protection du contenu
- Anti-copie intégré : sélection, clic droit, copier/couper, Ctrl+C/X/A/S/U/P,
  impression et glisser-déposer désactivés (les boutons « Copier » du site
  restent fonctionnels).
- Aucune protection web n'est absolue : pour un contrôle d'accès réel,
  ajouter une authentification (`.htaccess` + `.htpasswd`, Cloudflare Access…).

### ♿ Qualité
- Responsive (mobile → écrans larges 1700 px), touch targets 44 px,
  `aria-live`, navigation clavier, `prefers-reduced-motion` respecté.

---

## 🧭 Navigation

Routage par ancre : `/#/{section}/{page}[/{view}]`

| Section | Contenu |
|---|---|
| `accueil` | page d'accueil |
| `2info` | 2ᵉ Info · 3ᵉ Sciences |
| `3si` | 3ᵉ Sciences Informatiques |
| `bacsi` | Bac Sciences Informatiques |

Chaque rubrique propose les vues **Cours** · **Simulations** · **S'évaluer**.

---

## 🛠️ Stack technique

- **Next.js 16** (App Router, Turbopack) · **React 19** · **TypeScript**
- **Tailwind CSS 4** + composants **shadcn/ui** · **lucide-react**
- **framer-motion** pour les animations
- Contenu pédagogique **typé** dans `src/lib/*.ts` (aucune base de données
  nécessaire au runtime — le site est déployable en 100 % statique)

---

## 📁 Structure du projet

```
src/
├── app/                    # App Router (page unique + layout + api démo)
│   ├── layout.tsx          # métadonnées SEO, polices, AntiCopy
│   └── page.tsx            # routeur par ancre + orchestration des vues
├── components/
│   ├── SiteHeader.tsx      # en-tête, navigation des rubriques
│   ├── HomeView.tsx        # accueil
│   ├── CourseView.tsx      # vues Cours (2 colonnes larges 1700 px)
│   ├── Simulation.tsx      # moteur de simulation pas à pas
│   ├── EvaluationView.tsx  # évaluations (8 types de questions)
│   ├── CopyButton.tsx      # bouton « Copier » (exempté anti-copie)
│   ├── AntiCopy.tsx        # protection anti-copie
│   ├── BackToTop.tsx       # retour en haut de page
│   └── cours-anim.tsx …    # visualisations animées des cours
└── lib/
    ├── types.ts            # types partagés (cours, évals, routes)
    ├── cours-2info.ts      # contenu cours 2ᵉ Info · 3ᵉ Sciences
    ├── cours-3si.ts        # contenu cours 3ᵉ SI
    ├── cours-bacsi.ts      # contenu cours Bac SI
    ├── evals-*.ts          # banques de questions par rubrique
    ├── rubrics-*.ts        # rubriques et sous-rubriques
    └── algo/               # algorithmes des simulations
```

---

## 🚀 Démarrage local

```bash
npm install          # installer les dépendances
npm run dev          # serveur de développement → http://localhost:3000
```

---

## 📦 Build de production

### Site 100 % statique (recommandé)
```bash
npm run build:static # génère out/ (≈ 2,6 Mo) — déploiable partout
```
Le dossier `out/` contient `index.html` + assets ; le routage `#/` ne
nécessite **aucune configuration serveur** (pas de réécriture d'URL).

### Serveur Node (standalone)
```bash
npm run build        # build standalone
npm run start        # démarre .next/standalone/server.js
```

---

## ☁️ Déploiement

| Option | Durée | Coût | Méthode |
|---|---|---|---|
| **Netlify Drop** | 2 min | Gratuit | glisser le dossier `out/` sur app.netlify.com/drop |
| **Vercel** | 10 min | Gratuit | pousser sur GitHub → Import Project (auto-détecté) |
| **Hébergement mutualisé** (OVH, IONOS…) | 15 min | déjà payé | décompresser le ZIP dans `www/` via FTP |

**Domaine personnalisé** : configurer le CNAME chez le registrar — HTTPS
automatique et gratuit sur Netlify/Vercel/Let's Encrypt.

---

## 👨‍🏫 Auteur & licence

**Mr. Amine FARJALLAH** — Coding Academy
Algorithmique pas à pas pour le lycée tunisien.

© Tous droits réservés — contenu pédagogique protégé, reproduction et
redistribution interdites sans autorisation de l'auteur.
