# Fantasy Botola — projet mobile (Android + iOS, un seul code)

Ce dossier contient ton appli déjà prête à devenir une vraie appli Android **et** iOS,
à partir du même code web (`www/index.html`) que tu utilises déjà.

- `www/` → ton appli (HTML/CSS/JS + Supabase). C'est la SEULE chose à modifier pour changer une fonctionnalité.
- `android/` → projet natif Android, généré automatiquement par Capacitor à partir de `www/`.
- `ios/` → projet natif iOS, généré automatiquement par Capacitor à partir de `www/`.
- `capacitor.config.json` → réglages communs (nom de l'appli, couleurs, écran de démarrage).

Tu ne touches jamais directement à `android/` ou `ios/` à la main : à chaque changement dans `www/`,
on relance `npx cap sync` et les deux projets natifs se remettent à jour tout seuls.

## Étape 1 — Mettre ce projet sur GitHub (gratuit)

1. Va sur https://github.com/new
2. Nom du dépôt : `fantasy-botola-app` (privé, coche "Private")
3. Ne coche PAS "Add a README" (on a déjà tout)
4. Clique "Create repository"
5. Sur la page suivante, GitHub te donne des commandes du type :
   ```
   git init
   git add -A
   git commit -m "Premier envoi"
   git remote add origin https://github.com/TON-COMPTE/fantasy-botola-app.git
   git branch -M main
   git push -u origin main
   ```
   Utilise-les depuis ce dossier (dans un terminal, ouvert dans ce dossier `capacitor-project`).
   Le dossier `node_modules/` n'est pas inclus dans ce zip (normal, il est régénéré automatiquement
   par Codemagic avec `npm install` — c'est plus rapide à télécharger).

## Étape 2 — Construire les deux applis sans Mac ni PC puissant : Codemagic

1. Va sur https://codemagic.io et crée un compte gratuit (connecte-toi avec GitHub)
2. Clique "Add application", choisis ton dépôt `fantasy-botola-app`
3. Codemagic détecte automatiquement que c'est un projet Capacitor
4. Choisis le workflow "Capacitor" → il propose de construire Android ET iOS
5. Pour Android : Codemagic génère directement un `.apk` (à tester) ou `.aab` (à publier sur Google Play)
6. Pour iOS : il te demandera de connecter ton compte Apple Developer (99$/an) — Codemagic gère
   automatiquement les certificats de signature à ta place, tu n'as pas besoin d'un Mac
7. Chaque build te donne un fichier téléchargeable + Codemagic peut aussi publier automatiquement
   sur Google Play Console / App Store Connect si tu branches tes comptes développeur

Free tier Codemagic : 500 minutes de build Mac gratuites par mois — largement suffisant pour
plusieurs builds de test avant la publication.

## Étape 3 — Comptes développeur nécessaires

- Google Play Console : 25$, paiement unique — https://play.google.com/console
- Apple Developer Program : 99$/an — https://developer.apple.com/programs/enroll

## Pour continuer à développer

Toute nouvelle fonctionnalité se code dans `www/index.html` (ou les fichiers qu'il charge),
exactement comme avant. Ensuite :

```
npx cap sync
git add -A
git commit -m "description du changement"
git push
```

Codemagic reconstruit automatiquement les deux applis à chaque `push` si tu actives les builds automatiques.
