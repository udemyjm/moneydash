# Dashboard de suivi boursier

Un tableau de bord d'actions, en **un seul fichier HTML** : pas d'installation, pas de serveur, gratuit. Il s'ouvre dans le navigateur (internet requis) et se configure entièrement depuis l'interface.

Fichier : `dashboard-bourse.html` · Données de marché : widgets gratuits [TradingView](https://www.tradingview.com/).

> **Important :** les cours des actions sont en général **différés (≈ 15 min)** selon la bourse. Ce n'est pas du temps réel strict, et ce dashboard ne constitue pas un conseil en investissement.

---

## 1. Démarrage

**En local :** double-clique sur `dashboard-bourse.html`.

**En ligne (GitHub Pages), pour y accéder de partout :**
1. Mets le fichier dans un dépôt GitHub (tu peux le renommer `index.html`).
2. Dépôt → *Settings* → *Pages* → *Deploy from a branch* → `main` / `(root)`.
3. Ton dashboard est disponible à `https://<ton-pseudo>.github.io/<depot>/`.

---

## 2. Les blocs

| Bloc | Rôle |
|---|---|
| **Bandeau d'indices** | S&P 500, Nasdaq, Dow, EUR/USD, Bitcoin, Ethereum, Or. |
| **Mon portefeuille** | Valeur actuelle, montant investi, plus/moins-value, répartition (donut). |
| **Investissements** | Une carte par action détenue : graphique, investi, valeur actuelle, plus-value. |
| **Favoris & surveillance** | Actions suivies, en vue **Tableau** ou **Gérer**. |
| **Marchés mondiaux** | Tuiles de cours par pays, ou heatmap de performance (actions US). |

**Déplacer / redimensionner :** attrape un bloc par son titre pour le déplacer, et tire le coin en bas à droite pour le redimensionner. Les widgets s'adaptent à la taille du bloc.
**Verrouiller :** Menu → *Modules, tuiles, thème…* → « Verrouiller la disposition ».
**Afficher / masquer un bloc :** Menu → *Modules, tuiles, thème…*.

---

### Sur téléphone
Sur un écran de moins de 900 px de large, le dashboard passe en **version mobile** : les blocs sont empilés les uns sous les autres (bandeau, portefeuille, investissements, favoris, marchés) et la page défile. La disposition en grille (déplacer / redimensionner / verrouiller) n'existe que sur ordinateur. Les tuiles passent sur 2 colonnes, la fiche détaillée s'ouvre en plein écran, et la synchronisation GitHub fonctionne de la même façon (colle ton jeton une fois sur le téléphone). Tu peux aussi ajouter la page à l'écran d'accueil depuis le menu de ton navigateur. Si tu pivotes le téléphone au-delà de 900 px, la page se recharge dans l'autre mode.

---

## 3. Portefeuille et plus-value

### Ajouter une action
Menu → **Ajouter au portefeuille** (ou le bouton **+ Ajouter** du bloc Investissements).
- Renseigne le symbole, puis **2 des 3 champs** *prix d'achat / quantité / montant investi* : le 3ᵉ se calcule tout seul.
- Choisis la **devise de cotation** (celle du prix d'achat).
- Les actions de Londres cotent en pence (GBX) : divise par 100 pour saisir en £.

### Renseigner le cours actuel (le crayon ✎)
Le dashboard ne peut **pas lire** le prix affiché par les widgets TradingView. Pour calculer la plus-value, saisis le **cours actuel** de l'action :
1. Clique sur le crayon ✎ de la carte.
2. Remplis **« Cours actuel »** (dans la devise de cotation).
3. La valeur actuelle, la plus-value (€ et %) et le résumé se mettent à jour.

Tant qu'aucun cours n'est saisi, le badge indique **« Cours à renseigner ✎ »** et la plus-value affiche « — ». Le résumé compte alors la position à son prix d'achat.

### Devises
Affichage en **€, $, £ ou ¥** (Menu → *Devise, notifications…*). Les taux de change viennent de l'API gratuite Frankfurter (BCE) ; s'ils sont injoignables, des taux approximatifs sont utilisés.

### Notifications
Menu → *Devise, notifications…* : une notification du navigateur peut t'avertir quand une position dépasse ± X %.

---

## 4. Favoris

- **Ajouter :** champ de recherche du bloc, Menu → *Ajouter aux favoris*, ou le bouton « Ajouter aux favoris » de la fiche d'une action.
- **Vue Tableau :** tableau TradingView avec une ligne par action (valeur, variation, %, et ouverture / haut / bas / précédent si la largeur le permet).
  Une **poignée** au bord droit du tableau règle sa largeur (double-clic : pleine largeur). Sous une certaine largeur, le widget masque lui-même des colonnes.
- **Vue Gérer :** une ligne par action avec les boutons *détails*, *ajouter au portefeuille*, *retirer*, et un **glisser-déposer** pour réordonner.

---

## 4 bis. Marchés mondiaux

- **Tuiles :** environ 190 actions par pays (États-Unis, France, Allemagne, Royaume-Uni, Japon, Pays-Bas) + quelques ETF. Filtre par pays, recherche rapide, nombre de tuiles réglable (Menu → *Modules, tuiles, thème…*). Clique sur une tuile pour ouvrir la **fiche détaillée** (graphique, profil, actualités).
- **Heatmap :** performance par secteur (jour, semaine, mois, an…) pour le S&P 500, le Nasdaq 100, le Dow Jones ou toutes les actions US.

### Londres et Japon
TradingView n'affiche pas ces bourses dans ses widgets gratuits. Quand l'action a une **version cotée aux États-Unis (ADR)**, la tuile affiche cette version (mention « version US ») et la fiche propose un lien vers la version d'origine sur TradingView. Le cours ADR est en dollars et peut légèrement différer de la cote d'origine. Sans ADR, une carte avec un lien vers TradingView s'affiche.

---

## 5. Trouver une action

La **barre de recherche** (en haut), le champ des favoris et le formulaire du portefeuille acceptent :
- un **nom** ou un ticker connu (la liste intégrée) ;
- sinon, une **recherche TradingView** (peut être bloquée par le navigateur en fichier local) ;
- ou directement le symbole au format **`BOURSE:TICKER`**, par exemple `EURONEXT:ASML`, `NASDAQ:AAPL`, `XETR:SAP`.

Pour trouver un symbole : cherche l'action sur tradingview.com. L'adresse `…/symbols/EURONEXT-ASML/` donne `EURONEXT:ASML`.

---

## 6. Sauvegarde et synchronisation

Par défaut, tout est enregistré dans le **navigateur** (`localStorage`) : portefeuille, favoris, disposition, thème. C'est propre à un navigateur et à une adresse : un autre appareil, un autre navigateur ou la navigation privée repartent de zéro.

### Synchronisation GitHub (recommandé)
Les modifications sont écrites automatiquement dans un fichier **`dashboard-config.json`** de ton dépôt, et rechargées à l'ouverture sur n'importe quel appareil.

**À faire une fois :**
1. Crée un **jeton fine-grained** : GitHub → *Settings* → *Developer settings* → *Personal access tokens* → *Fine-grained tokens* → *Generate new token*.
   - *Repository access* : **Only select repositories** → ton dépôt.
   - *Repository permissions* : **Contents → Read and write**.
   - Choisis une durée d'expiration (à son terme, il faut en recréer un).
2. Copie-le tout de suite (`github_pat_…`, affiché une seule fois) et garde-le dans un **gestionnaire de mots de passe**.
3. Dans le dashboard, clique sur **☁ GitHub** : renseigne propriétaire, dépôt, branche, fichier et jeton, puis **« Enregistrer les réglages & synchroniser »**.

**Ensuite :**
- Chaque modification est envoyée environ 4 secondes plus tard (chaque envoi crée un commit). Le bouton ☁ affiche l'état : *à envoyer*, *synchronisé*, *erreur*, *conflit*.
- Sur un autre appareil : colle le même jeton (ou, pour simplement **consulter** un dépôt public, aucun jeton n'est nécessaire : l'appareil est en lecture seule).
- Le jeton reste **uniquement dans le navigateur** de l'appareil : jamais dans le code, ni dans la config, ni sur GitHub. Ne le mets jamais dans le dépôt.
- **Dépôt privé :** le jeton est nécessaire sur tous les appareils, même pour lire.

**Boutons de la fenêtre ☁ :**
- **Envoyer vers GitHub** : la config de cet appareil écrase celle de GitHub.
- **Charger depuis GitHub** : la config de GitHub écrase celle de cet appareil.
- À utiliser surtout en cas de **conflit** (GitHub et l'appareil ont tous deux changé).

Pour ne pas retaper propriétaire / dépôt sur chaque appareil, remplis une fois la constante `GITHUB` en haut du script (le jeton, lui, ne va jamais dans le code).

### Sauvegarde dans un fichier
Menu → *Sauvegarder / restaurer (fichier)* : export / import de la config en JSON, ou téléchargement d'un HTML contenant ta config (ligne `EMBEDDED_CONFIG`).

---

## 7. Personnaliser le code

Quelques constantes dans le script :

| Constante | Utilité |
|---|---|
| `UNIVERSE` | Liste des actions des tuiles et de l'autocomplétion (format `TICKER\|Nom;…` par bourse). |
| `COUNTRIES` | Pays proposés dans le filtre des tuiles. |
| `NO_WIDGET` | Bourses dont TradingView n'affiche pas les cours dans les widgets gratuits. |
| `ADR` | Correspondance *symbole d'origine → version US*. |
| `GITHUB` | Propriétaire / dépôt / branche / fichier pour la synchronisation. |

---

## 8. Dépannage

| Problème | Piste |
|---|---|
| « Cours à renseigner ✎ » | Normal : saisis le cours actuel via le crayon. |
| Tuile ou ligne vide | Bourse non gérée par les widgets gratuits : ajoute-la à `NO_WIDGET` / `ADR`, ou vérifie le symbole (`BOURSE:TICKER`). |
| La recherche ne trouve rien | La recherche TradingView peut être bloquée en local : tape le symbole `BOURSE:TICKER`. |
| ☁ en « erreur » | Jeton expiré ou invalide, mauvais dépôt / branche, ou droits insuffisants (*Contents : Read and write* requis). |
| ☁ en « conflit » | GitHub et l'appareil ont changé : choisis *Charger* ou *Envoyer* dans la fenêtre ☁. |
| Données de démonstration au démarrage | Autre navigateur / adresse / données effacées : synchronise avec GitHub ou importe ta config. |
| Disposition cassée | Menu → *Modules, tuiles, thème…* → « Réinitialiser la disposition ». |
