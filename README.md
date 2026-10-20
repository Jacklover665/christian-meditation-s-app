# Sérénité

Application de méditation en français, installable comme PWA et emballée en application Android avec Capacitor.

## Prérequis

- Node.js 22 ou plus récent
- npm
- Pour générer Android localement : Android Studio et le SDK Android

## Développement et build web

```sh
npm ci
npm run build
```

Les fichiers distribuables sont placés dans `dist/`. Pour tester l'installation PWA et le mode hors ligne, hébergez ce dossier en HTTPS. Le service worker n'est pas disponible quand `index.html` est ouvert directement depuis le disque.

## Android local

```sh
npm ci
npm run build
npx cap add android
npm run android:sync
```

Ouvrez ensuite `android/` avec Android Studio et générez l'APK ou le bundle signé depuis son menu de build. L'identifiant d'application est `com.serenite.app`.

## GitHub

Poussez le dossier dans un dépôt GitHub avec la branche `main`. **Actions > Build Android APK > Run workflow** génère un APK de débogage ; téléchargez-le dans les artefacts de l'exécution. Le workflow Android s'exécute aussi à chaque push sur `main`.

Pour publier la version web, activez **Settings > Pages > Build and deployment > GitHub Actions**. Le workflow `Deploy web app` publie ensuite `dist/` sur GitHub Pages à chaque push sur `main`.

Ces workflows produisent un APK de débogage pour les essais. Une publication sur Google Play nécessite une clé de signature et une configuration de release qui ne doivent pas être stockées dans le dépôt.