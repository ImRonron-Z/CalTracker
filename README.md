# CalTracker – Carnet de sèche

Appli installable (PWA) pour suivre son alimentation et son poids pendant une sèche :

- scan de code-barres par la caméra, valeurs nutritionnelles via Open Food Facts ;
- quantités en grammes, totaux du jour (calories, protéines, lipides, glucides) ;
- calories dépensées et poids du jour, avec le **bilan calorique** (déficit ou surplus) ;
- **poids théorique** déduit du bilan, comparé à ton poids réel sur un graphique ;
- historique sur 7 jours, 1 mois ou 1 an.

Tout fonctionne hors ligne une fois installée (sauf la recherche d'un produit jamais scanné).
Aucun compte, aucun serveur : les données restent sur le téléphone.

## 1. L'adresse de l'appli

L'appli est publiée avec GitHub Pages : **https://imronron-z.github.io/CalTracker/**

Les navigateurs n'autorisent la caméra que sur une page en HTTPS, d'où cette mise en ligne.

Pour la publier soi-même (fork ou nouveau dépôt public) :
1. Pousse le contenu de ce dossier sur un dépôt GitHub **public** (index.html, sw.js, manifest.webmanifest,
   et les dossiers icons, fonts, vendor).
2. Settings > Pages > « Deploy from a branch » > `main` / `/ (root)` > Save.
3. Après une minute, l'appli est sur `https://TON-PSEUDO.github.io/NOM-DU-DEPOT/`.

Le dépôt ne contient aucune donnée personnelle. Autres options équivalentes : Netlify Drop ou Cloudflare Pages.

## 2. L'installer sur le téléphone

- **iPhone** : ouvre l'adresse dans Safari > bouton Partager > « Sur l'écran d'accueil ».
- **Android** : ouvre l'adresse dans Chrome > menu > « Installer l'application ».

Ouvre-la ensuite depuis l'icône, accepte l'accès à la caméra au premier scan.

## 3. Utilisation

### Ajouter ce que tu manges
1. « Scanner un code-barres » : le produit s'affiche avec ses valeurs pour 100 g.
2. Saisis les grammes (ou touche une portion rapide), puis « Ajouter ».
3. Un produit introuvable ou incomplet : « Créer un produit à la main » ou « Corriger ».
4. Si la caméra pose problème : « Lire depuis une photo » ou saisie du code à la main.

### Dépense et poids
Dans le bloc « Dépense et poids », renseigne pour le jour affiché :
- les **calories dépensées** (dépense totale de la journée, repos + activité, telle qu'affichée par ta montre
  ou Garmin Connect) ;
- ton **poids du jour** (en kg).

Les flèches en haut permettent de compléter ou corriger un autre jour. Vider un champ supprime la valeur.

### Bilan du jour
Dans « Valeurs du jour », le bilan est calculé comme **mangé − dépensé** : un déficit s'affiche en vert,
un surplus en rouge, avec le poids théorique correspondant (≈ kg). Il apparaît quand tu as saisi la dépense
**et** au moins un aliment ce jour-là, pour qu'un jour vide ne ressemble pas à un énorme déficit.

### Historique et graphique
La section « Historique » (repliable) propose trois périodes : **7 jours**, **1 mois**, **1 an**.
- Le tableau montre une ligne par jour (7 jours), par semaine (1 mois) ou par mois (1 an), en moyennes par jour.
- Le graphique superpose le **poids réel** (une pesée = un point) et le **poids théorique** (pointillés).
  Touche ou survole la courbe pour voir le détail d'un jour.

Le poids théorique part de ton premier poids de la période, puis applique chaque jour ton bilan, sur la base de
**7 700 kcal = 1 kg**. Les jours sans bilan sont ignorés. C'est une approximation : l'eau et le sel font varier
la balance, et sur une longue période les petites erreurs de saisie s'accumulent. Lis la courbe théorique comme
une tendance.

### Sections repliables
Le Journal, « Mes produits » et l'Historique se déplient et se replient d'un geste. L'appli retient ton choix.

### Objectifs
Les objectifs (calories max, protéines et lipides min) se règlent dans « Objectifs, installation et sauvegarde ».

## 4. Données

Tout reste sur le téléphone (stockage du navigateur) : produits, journal, dépenses, poids et objectifs.
Les données sont liées à l'adresse de l'appli : si l'adresse change, l'appli s'ouvre vide.

Utilise « Exporter mes données » de temps en temps : le fichier JSON se réimporte avec
« Importer une sauvegarde », sur le même appareil ou sur un autre.

Seul le code-barres est envoyé à Open Food Facts quand tu cherches un produit. Tes quantités, ton poids et ton
historique ne quittent jamais le téléphone.

## 5. Mettre à jour l'appli

Après une modification de fichier, incrémente `CACHE` dans `sw.js` (par exemple `carnet-seche-v3` en
`carnet-seche-v4`) avant de republier, sinon les téléphones gardent l'ancienne version en cache.

Une fois la nouvelle version en ligne (compte une minute pour GitHub Pages), ferme et rouvre l'appli deux fois
pour qu'elle remplace l'ancienne.
