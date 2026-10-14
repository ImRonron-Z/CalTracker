# Carnet de sèche

Appli installable (PWA) : scan de code-barres par la caméra, valeurs nutritionnelles via Open Food Facts,
quantités en grammes, totaux du jour et moyenne sur 7 jours. Tout fonctionne hors ligne une fois installée
(sauf la recherche d'un produit jamais scanné).

## 1. La mettre en ligne (obligatoire pour la caméra)

Les navigateurs n'autorisent la caméra que sur une page en HTTPS. Le plus simple, gratuit :

**GitHub Pages**
1. Crée un dépôt public sur github.com (par exemple `carnet-seche`). Il ne contient aucune donnée personnelle.
2. « Add file » > « Upload files » : glisse le CONTENU de ce dossier (index.html, sw.js, manifest.webmanifest,
   et les dossiers icons, fonts, vendor), puis valide.
3. Settings > Pages > « Deploy from a branch » > `main` / `/ (root)` > Save.
4. Après une minute, l'appli est sur `https://TON-PSEUDO.github.io/carnet-seche/`.

Autres options équivalentes : Netlify Drop (glisser le dossier sur app.netlify.com/drop) ou Cloudflare Pages.

## 2. L'installer sur le téléphone

- **iPhone** : ouvre l'adresse dans Safari > bouton Partager > « Sur l'écran d'accueil ».
- **Android** : ouvre l'adresse dans Chrome > menu > « Installer l'application ».

Ouvre-la ensuite depuis l'icône, accepte l'accès à la caméra au premier scan.

## 3. Utilisation

1. « Scanner un code-barres » : le produit s'affiche avec ses valeurs pour 100 g.
2. Saisis les grammes (ou touche une portion rapide), puis « Ajouter ».
3. Un produit introuvable ou incomplet : « Créer un produit à la main » ou « Corriger ».
4. Les objectifs (calories max, protéines et lipides min) se règlent dans « Objectifs, installation et sauvegarde ».

Si la caméra pose problème : « Lire depuis une photo » ou saisie du code à la main.

## 4. Données

Tout reste sur le téléphone (stockage du navigateur). Utilise « Exporter mes données » de temps en temps :
le fichier JSON se réimporte sur un autre appareil.

## 5. Mettre à jour l'appli

Après une modification de fichier, change `CACHE = 'carnet-seche-v1'` en `v2` dans `sw.js` avant de republier,
sinon les téléphones gardent l'ancienne version en cache.
