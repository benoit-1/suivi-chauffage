# Suivi pellets

Application pour noter chaque remplissage du poêle à granulés avec la température des pièces, et voir combien on consomme selon le froid dehors.

- **Le site** (ce fichier `index.html`) est publié avec GitHub Pages. Il ne contient aucune donnée.
- **Les données** sont dans un fichier `donnees.json`, rangé dans un **dépôt privé** que vous seuls pouvez voir. Chaque enregistrement y laisse une trace dans l'historique.
- **La météo** vient d'Open-Meteo, un service gratuit et sans inscription. L'application calcule la moyenne de chaque journée pour votre commune.

---

## Mise en route (environ 15 minutes, une seule fois)

### 1. Créer un compte GitHub

Si vous n'en avez pas encore : <https://github.com/signup> (gratuit).

### 2. Créer le dépôt du site (public)

1. En haut à droite, cliquez sur **+**, puis **New repository**.
2. Nom : `suivi-chauffage`. Visibilité : **Public**. Cliquez sur **Create repository**.
3. Sur la page du dépôt, cliquez sur **uploading an existing file**. Déposez `index.html` (et ce `README.md` si vous voulez), puis cliquez sur **Commit changes**.
4. Allez dans **Settings**, puis **Pages**. Dans **Branch**, choisissez `main` et `/ (root)`, puis cliquez sur **Save**.
5. Au bout d'une ou deux minutes, le site est en ligne à l'adresse
   `https://VOTRE-IDENTIFIANT.github.io/suivi-chauffage/`

> Le dépôt du site doit être public pour que GitHub Pages soit gratuit. Il ne contient que le programme, jamais vos relevés.

### 3. Créer le dépôt des données (privé)

1. Cliquez sur **+**, puis **New repository**.
2. Nom : `suivi-chauffage-donnees`. Visibilité : **Private**.
3. Cochez **Add a README file**, puis cliquez sur **Create repository**.

Vous n'avez rien d'autre à y mettre : l'application crée elle-même le fichier `donnees.json`.

### 4. Créer la clé d'accès (jeton)

C'est elle qui permet à l'application d'écrire dans le dépôt privé, et **seulement dans celui-là**.

1. Ouvrez <https://github.com/settings/personal-access-tokens/new>.
2. **Token name** : `Suivi chauffage`.
3. **Expiration** : choisissez la durée la plus longue proposée et notez la date. À l'échéance, il faudra recréer une clé.
4. **Repository access** : cochez **Only select repositories**, puis choisissez `suivi-chauffage-donnees`.
5. **Permissions**, puis **Repository permissions**, puis **Contents** : choisissez **Read and write**.
6. Cliquez sur **Generate token**, puis copiez la clé. Elle commence par `github_pat_` et ne s'affiche qu'une fois.

### 5. Connecter votre téléphone

1. Ouvrez l'adresse du site sur votre téléphone.
2. Indiquez votre identifiant GitHub, le dépôt (`suivi-chauffage-donnees`) et collez la clé.
3. Indiquez la commune, le code postal et les pièces, en mettant **en premier la pièce du poêle**.
4. Dans **Réglages**, renseignez « Qui utilise ce téléphone ? » : votre prénom apparaîtra dans le journal.
5. Ajoutez la page à l'écran d'accueil :
   - sur iPhone, Safari, bouton **Partager**, puis **Sur l'écran d'accueil** ;
   - sur Android, Chrome, menu **⋮**, puis **Ajouter à l'écran d'accueil**.

### 6. Connecter le téléphone de votre conjoint

1. Sur votre téléphone, allez dans **Réglages**, puis **Connecter un autre téléphone**, puis **Copier le code**.
2. Envoyez ce code par un message privé (SMS, WhatsApp). Il contient la clé : ne le publiez nulle part.
3. Sur son téléphone : elle ouvre l'adresse du site, touche **Vous avez reçu un code de connexion ?**, colle le code, puis **Utiliser ce code**.
4. Elle renseigne son prénom dans **Réglages**.

Vous travaillez ensuite tous les deux sur les mêmes données. Si vous enregistrez en même temps, l'application fusionne les saisies sans rien perdre.

---

## Utiliser l'application sans compte (stockage sur l'appareil)

C'est le plus simple pour un particulier : envoyez-lui seulement l'adresse du site.
1. Il ouvre l'adresse et touche **Commencer sur cet appareil**.
2. Il indique sa commune et ses pièces : c'est prêt. Pas de compte, pas de clé.

Ses relevés restent **sur son appareil uniquement**. Dans **Réglages**, puis **Mes données** :
- **Sauvegarder mes relevés** crée un fichier, à garder dans iCloud Drive, Google Drive ou par e-mail. L'accueil rappelle de le faire au bout d'un mois.
- **Restaurer ou ajouter un fichier** récupère une sauvegarde, sur un nouveau téléphone par exemple, ou ajoute les relevés d'un autre appareil de la famille, sans doublon.

Dans ce mode, les appareils d'une même famille ne se synchronisent pas tout seuls. Pour un suivi partagé automatiquement, utilisez plutôt un dépôt GitHub (ci-dessous).

## Installer l'application (pour tout le monde)

Envoyez simplement l'adresse **https://benoit-1.github.io/suivi-chauffage/** à la personne. Elle n'a besoin d'aucun compte.

- **iPhone / iPad** : ouvrir le lien dans Safari, bouton Partager, puis « Sur l'écran d'accueil ».
- **Android** : ouvrir le lien dans Chrome, puis « Installer l'application » (bouton dans l'application ou menu ⋮).
- **Ordinateur** : Chrome ou Edge proposent « Installer » dans la barre d'adresse.

Ensuite elle touche **🔥 Commencer**. Ses relevés restent sur son appareil. Une fois installée, l'application s'ouvre même sans réseau (seule la météo attend le retour du réseau).

## Compteur d'utilisateurs

L'application peut envoyer un signal anonyme à GoatCounter (gratuit, sans cookie, sans bandeau de consentement). Aucun relevé, aucun nom, aucune commune n'est envoyé. Seuls ces événements sont comptés :

| Événement | Signification |
|---|---|
| nouvel-appareil | une nouvelle installation |
| mode-sans-compte / mode-github | le mode choisi à l'installation |
| appareil-actif-du-jour | un appareil utilisé ce jour-là (une fois par jour) |
| chargement | un chargement de pellets noté |

Pour l'activer : créer un compte sur goatcounter.com, puis mettre le code du site dans `COMPTEUR` (fichier app.js) et reconstruire index.html. Les chiffres se lisent sur le tableau de bord GoatCounter. Chaque utilisateur peut couper l'envoi dans **Réglages**, **Statistiques anonymes : Non**.

## Partager l'application avec d'autres foyers

Tout le monde utilise la même adresse (votre site). Les autres foyers n'ont **rien à créer** : ni compte, ni GitHub.

**Une seule fois** (5 minutes) :
1. Sur GitHub, créez un dépôt **privé** `suivi-chauffage-foyers`, en mettant **Add README** sur **On**.
2. Créez une clé limitée à ce seul dépôt : **No expiration**, **Only select repositories**, puis `suivi-chauffage-foyers`, et **Contents : Read and write**.
3. Dans l'application : **Réglages**, puis **Ajouter un foyer**. Collez la clé, puis **Vérifier et enregistrer**.

**Pour chaque nouveau foyer** : **Réglages**, puis **Ajouter un foyer**, tapez son nom (par exemple « Dupont »), puis **Créer**. Envoyez le lien ou faites scanner le QR code. En l'ouvrant, le foyer indique sa commune et ses pièces. Il pourra ensuite inviter ses propres appareils.

Chaque foyer a son fichier à part dans le dépôt, et ne voit que ses relevés dans l'application. Les foyers partagent toutefois la même clé : une personne qui s'y connaît pourrait lire les autres fichiers. C'est réservé aux proches. Pour couper un accès, il faut changer la clé et renvoyer les liens.

## Utilisation

- **Accueil** : la température dehors, la moyenne de la maison et les sacs consommés depuis le début de la saison.
- **Prendre les températures** : une case par pièce. Sur iPhone, touchez une case deux fois, puis **Scanner du texte** pour lire un thermomètre avec l'appareil photo. On peut relever les températures à tout moment, même sans recharger.
- **Chargement pellets** : choisissez le nombre de sacs avec − et +, puis **Enregistrer**.
- **Voir tous les détails** : graphiques, tableaux par pièce et par tranche de froid, météo, journal et export pour Excel.
- **Réglages (⚙︎)** : votre prénom, la source de la température extérieure (automatique, manuelle ou les deux), les pièces, le prix des sacs, la commune, l'invitation d'un appareil.
- Rechargez toujours au **même niveau de réservoir** (par exemple presque vide) : la consommation se calcule entre deux chargements.
- **Sans réseau**, les saisies sont gardées dans le téléphone et envoyées au retour de la connexion.

### Ajouter un appareil (famille, tablette)

Sur un appareil déjà connecté : **Réglages**, puis **Inviter un appareil**.
- **À côté** : visez le QR code avec l'appareil photo, puis touchez le lien.
- **À distance** : **Envoyer le lien…** par SMS ou WhatsApp.

Sur iPhone et iPad, ouvrez le lien dans **Safari**, puis tout de suite **Partager**, **Sur l'écran d'accueil**, **Ajouter**. L'icône garde la connexion.

## En cas de problème

| Message | Que faire |
|---|---|
| « Clé refusée par GitHub » | La clé a expiré ou a été supprimée. Recréez-la (étape 4), puis **Réglages**, **Changer la connexion**, sur chaque téléphone. |
| « Dépôt introuvable » | Vérifiez l'identifiant, le nom du dépôt, et que la clé a bien accès à `suivi-chauffage-donnees`. |
| « La météo n'est pas joignable » | Open-Meteo ne répond pas pour le moment. Notez la température dehors à la main, ou réessayez plus tard. |
| Téléphone perdu | Sur GitHub, allez dans **Settings**, **Developer settings**, **Personal access tokens**, supprimez la clé, puis recréez-en une. |

## Vos données

Le fichier `donnees.json` du dépôt privé contient tout : réglages du foyer, pièces, remplissages et météo enregistrée. C'est un fichier texte lisible. L'onglet **History** du dépôt montre chaque modification avec son auteur et sa date.

Météo : [Open-Meteo.com](https://open-meteo.com/) (licence CC BY 4.0).

## Historique des versions

Le numéro de version est affiché en bas de chaque écran de l'application. Après avoir déposé un nouveau `index.html`, rechargez la page (Cmd + Maj + R sur Mac) et vérifiez que le numéro a changé.

| Version | Date | Changements |
|---|---|---|
| 3.4 | 9 novembre 2026 | Les animations des fêtes s'affichent 15 jours avant et 15 jours après chaque fête. Entre Noël et le Nouvel An, la fête la plus proche l'emporte. |
| 3.3 | 9 novembre 2026 | L'animation démarre toujours au départ, même sur un appareil réglé sur « Réduire les animations ». Chacun peut la couper dans les Réglages. |
| 3.2 | 9 novembre 2026 | Application installable sur le téléphone (icône, fonctionne hors ligne). Accueil simplifié : un gros bouton « Commencer » sans compte. Compteur anonyme d'utilisateurs (GoatCounter), désactivable. |
| 3.1 | 9 novembre 2026 | Mode sans compte : « Commencer sur cet appareil ». Relevés gardés sur l'appareil, avec sauvegarde et restauration par fichier, et rappel de sauvegarde. |
| 3.0 | 9 novembre 2026 | Ajout d'un foyer en un clic : un seul dépôt et une seule clé pour tous les autres foyers, un fichier par foyer. |
| 2.9 | 9 novembre 2026 | Réglage des animations simplifié : Oui / Non. L'intensité est fixée par nous pour tout le monde. |
| 2.8 | 9 novembre 2026 | Écran de veille fixé à 15 secondes pour tout le monde (plus de réglage). Il s'arrête si l'animation est sur « Arrêt ». |
| 2.7 | 9 novembre 2026 | Écran de veille : sur l'accueil, l'animation passe devant l'écran après un moment sans toucher (15 s à 3 min, ou jamais) et repasse derrière au premier toucher. |
| 2.6 | 9 novembre 2026 | Halloween : toiles d'araignée dans les coins et araignées qui descendent au bout de leur fil. |
| 2.5 | 9 novembre 2026 | Réglages : « Préparer l’accès d’un autre foyer » crée le lien et le QR code d’un proche, sans déconnecter votre appareil. |
| 2.4 | 9 novembre 2026 | Correctif : le prénom s'enregistre pendant la saisie (bouton OK) et n'est plus effacé par une mise à jour en arrière-plan ; les autres cases ne sont plus effacées non plus. |
| 2.3 | 9 novembre 2026 | Animations des fêtes automatiques : Noël, Nouvel An (feux d'artifice), Chandeleur, Saint-Valentin, Pâques, Halloween. Désactivables dans les Réglages. |
| 2.2 | 9 novembre 2026 | Animations : chiffres qui défilent à l'ouverture, étincelles à chaque chargement, flamme qui grossit quand on consomme plus que d'habitude, ciel du moment (soleil, pluie, neige, orage, vent). |
| 2.1 | 9 novembre 2026 | Animation de l'accueil plus visible ; réglage par appareil : Arrêt, Douce, Normale ou Vive. |
| 2.0 | 9 novembre 2026 | Nouvel accueil (dehors, maison, sacs) avec fond animé ; écrans séparés « Prendre les températures » et « Chargement pellets » ; écran Détails ; choix de la source de la température extérieure ; emplacements prévus pour thermomètres et poêles connectés (Jolly Mec / Agua IOT). Conversion automatique des données 1.x. |
| 1.3 | 9 novembre 2026 | Cases des pièces compatibles avec « Scanner du texte » de l'iPhone pour lire un thermomètre avec l'appareil photo. |
| 1.2 | 9 novembre 2026 | L'icône ajoutée à l'écran d'accueil (iPhone, iPad) garde la connexion. Numéro de version affiché. |
| 1.1 | 9 novembre 2026 | Invitation d'un appareil par lien ou QR code. |
| 1.0 | 9 novembre 2026 | Première version : remplissages, températures par pièce, météo automatique, données dans un dépôt GitHub privé. |
