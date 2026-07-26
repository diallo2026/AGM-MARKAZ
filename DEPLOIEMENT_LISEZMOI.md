# Déploiement AGM — Firebase Hosting + GitHub

## Contenu de ce zip
- `index.html` — l'application, avec la config Firebase déjà remplie (projet `agm-markaz-prod`)
- `manifest.json` — fichier PWA (installation sur mobile)
- `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`, `favicon.ico` — icônes générées (à remplacer plus tard par ton propre logo si tu en as un)
- `firebase.json` — configuration de l'hébergement Firebase
- `.firebaserc` — associe ce dossier au projet Firebase `agm-markaz-prod`
- `database.rules.json` — règles de sécurité (accès réservé aux appareils authentifiés)

## Avant de déployer
Vérifie dans la console Firebase (console.firebase.google.com → agm-markaz-prod) :
- [ ] Realtime Database créée (fait ✅)
- [ ] Authentication → Sign-in method → **Anonyme** activé

## Étapes

1. **Remplace tout le contenu de ton dépôt GitHub cloné par ces fichiers**
   (garde aussi tes autres fichiers existants du dépôt s'il y en a d'autres).

2. Dans le terminal, à la racine du dépôt :
   ```bash
   npm install -g firebase-tools
   firebase login
   firebase init hosting
   ```
   - Projet existant → `agm-markaz-prod`
   - Dossier public → `.`
   - Configurer comme single-page app ? → **Non**
   - Fichier `index.html` existant détecté → **Non** (ne pas écraser)
   - "Set up automatic builds and deploys with GitHub ?" → **Oui** → autorise l'accès → choisis ton dépôt → branche `main`

3. Déploie une première fois manuellement (optionnel mais recommandé pour vérifier tout de suite) :
   ```bash
   firebase deploy
   ```

4. Pousse sur GitHub pour activer le déploiement automatique futur :
   ```bash
   git add .
   git commit -m "Déploiement Firebase Hosting + config production"
   git push origin main
   ```

Ton appli sera en ligne sur : **https://agm-markaz-prod.web.app**
