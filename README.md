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
2. Nom : `suivi-pellets`. Visibilité : **Public**. Cliquez sur **Create repository**.
3. Sur la page du dépôt, cliquez sur **uploading an existing file**. Déposez `index.html` (et ce `README.md` si vous voulez), puis cliquez sur **Commit changes**.
4. Allez dans **Settings**, puis **Pages**. Dans **Branch**, choisissez `main` et `/ (root)`, puis cliquez sur **Save**.
5. Au bout d'une ou deux minutes, le site est en ligne à l'adresse
   `https://VOTRE-IDENTIFIANT.github.io/suivi-pellets/`

> Le dépôt du site doit être public pour que GitHub Pages soit gratuit. Il ne contient que le programme, jamais vos relevés.

### 3. Créer le dépôt des données (privé)

1. Cliquez sur **+**, puis **New repository**.
2. Nom : `suivi-pellets-donnees`. Visibilité : **Private**.
3. Cochez **Add a README file**, puis cliquez sur **Create repository**.

Vous n'avez rien d'autre à y mettre : l'application crée elle-même le fichier `donnees.json`.

### 4. Créer la clé d'accès (jeton)

C'est elle qui permet à l'application d'écrire dans le dépôt privé, et **seulement dans celui-là**.

1. Ouvrez <https://github.com/settings/personal-access-tokens/new>.
2. **Token name** : `Suivi pellets`.
3. **Expiration** : choisissez la durée la plus longue proposée et notez la date. À l'échéance, il faudra recréer une clé.
4. **Repository access** : cochez **Only select repositories**, puis choisissez `suivi-pellets-donnees`.
5. **Permissions**, puis **Repository permissions**, puis **Contents** : choisissez **Read and write**.
6. Cliquez sur **Generate token**, puis copiez la clé. Elle commence par `github_pat_` et ne s'affiche qu'une fois.

### 5. Connecter votre téléphone

1. Ouvrez l'adresse du site sur votre téléphone.
2. Indiquez votre identifiant GitHub, le dépôt (`suivi-pellets-donnees`) et collez la clé.
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
| « Dépôt introuvable » | Vérifiez l'identifiant, le nom du dépôt, et que la clé a bien accès à `suivi-pellets-donnees`. |
| « La météo n'est pas joignable » | Open-Meteo ne répond pas pour le moment. Notez la température dehors à la main, ou réessayez plus tard. |
| Téléphone perdu | Sur GitHub, allez dans **Settings**, **Developer settings**, **Personal access tokens**, supprimez la clé, puis recréez-en une. |

## Vos données

Le fichier `donnees.json` du dépôt privé contient tout : réglages du foyer, pièces, remplissages et météo enregistrée. C'est un fichier texte lisible. L'onglet **History** du dépôt montre chaque modification avec son auteur et sa date.

Météo : [Open-Meteo.com](https://open-meteo.com/) (licence CC BY 4.0).

## Historique des versions

Le numéro de version est affiché en bas de chaque écran de l'application. Après avoir déposé un nouveau `index.html`, rechargez la page (Cmd + Maj + R sur Mac) et vérifiez que le numéro a changé.

| Version | Date | Changements |
|---|---|---|
| 2.0 | 9 novembre 2026 | Nouvel accueil (dehors, maison, sacs) avec fond animé ; écrans séparés « Prendre les températures » et « Chargement pellets » ; écran Détails ; choix de la source de la température extérieure ; emplacements prévus pour thermomètres et poêles connectés (Jolly Mec / Agua IOT). Conversion automatique des données 1.x. |
| 1.3 | 9 novembre 2026 | Cases des pièces compatibles avec « Scanner du texte » de l'iPhone pour lire un thermomètre avec l'appareil photo. |
| 1.2 | 9 novembre 2026 | L'icône ajoutée à l'écran d'accueil (iPhone, iPad) garde la connexion. Numéro de version affiché. |
| 1.1 | 9 novembre 2026 | Invitation d'un appareil par lien ou QR code. |
| 1.0 | 9 novembre 2026 | Première version : remplissages, températures par pièce, météo automatique, données dans un dépôt GitHub privé. |
