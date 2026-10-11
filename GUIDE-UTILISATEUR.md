# Guide d'utilisation — UX widget grist

<img src="aia.png" alt="AIA" width="40" align="left" /> **AIA — Assisté par l'intelligence artificielle.** Ce widget et sa documentation ont été réalisés avec l'assistance d'une IA, sous la direction et avec la validation de leur auteur. Icône : [Martine Peters](https://mpeters.uqo.ca/utilisation-transparente-de-lintelligence-artificielle/), CC BY-NC-SA 4.0.
<br clear="left" />

Ce guide s'adresse :
- aux **utilisateurs**, qui consultent les pages : partie 1 ;
- aux **administrateurs**, qui les composent : partie 2.

Pour l'installation et le fonctionnement technique, voir le `README.md`.

---

## Sommaire

1. [Consulter une page](#1-consulter-une-page)
   - [L'en-tête](#len-tête)
   - [Les blocs](#les-blocs)
   - [Tableaux et fiches](#tableaux-et-fiches)
   - [Cartes](#cartes)
   - [Imprimer et exporter](#imprimer-et-exporter)
   - [Sur smartphone](#sur-smartphone)
2. [Composer une page (administrateurs)](#2-composer-une-page-administrateurs)
   - [Ouvrir la configuration](#ouvrir-la-configuration)
   - [Choisir et régler les vues](#choisir-et-régler-les-vues)
   - [Disposition](#disposition)
   - [Filtre rapide](#filtre-rapide)
   - [Listes de sélection](#listes-de-sélection)
   - [Cartes : réglages](#cartes--réglages)
   - [Menu de navigation](#menu-de-navigation)
   - [Enregistrer](#enregistrer)
3. [Questions fréquentes](#3-questions-fréquentes)

---

## 1. Consulter une page

### L'en-tête

En haut de la page, de gauche à droite et de haut en bas :

- **Menu des pages** : un clic affiche une autre page. Seules les pages auxquelles vous avez accès apparaissent.
- **Menu ☰** (en haut à droite) : il ouvre la liste des actions.

  | Action | Rôle |
  |---|---|
  | Tout replier / Tout déplier | Replie ou déplie tous les blocs d'un coup |
  | Actualiser | Recharge les données et la configuration des vues |
  | Imprimer | Imprime la page ou l'enregistre en PDF |
  | Aide | Ouvre ce guide ; l'onglet Nouveautés présente les évolutions du widget |
  | Disposition, Configurer | Réservés aux administrateurs (partie 2) |

  Une pastille rouge sur ☰ signale une nouvelle version du widget : elle disparaît après lecture de l'onglet Nouveautés.
- **Listes de sélection** (par exemple Département, Circonscription, École) : choisir une valeur filtre les blocs de la page.
  - Une liste qui ne propose qu'un seul choix, selon vos droits, n'est pas affichée : sa valeur s'applique automatiquement.
  - Certaines listes gardent leur sélection quand vous changez de page.

### Les blocs

Chaque vue s'affiche dans un **bloc**, avec un titre et quelques commandes :

| Élément | Rôle |
|---|---|
| ▾ / ▸ devant le titre | Replier ou déplier le bloc (un clic sur le titre fonctionne aussi) |
| **Filtre rapide** (`Tous \| Public \| Privé`) | Ne montrer que les lignes d'une valeur (voir ci-dessous) |
| Champ « Filtrer… » | Recherche dans les lignes du bloc (grands tableaux et listes de fiches) |
| ⤓ | Exporter le bloc en CSV |
| ⛶ | Afficher le bloc en plein écran ; ✕ ou Échap pour revenir |

**Filtre rapide**
- **Ce qu'il fait** : il ne s'applique qu'à son bloc et ne change rien aux autres blocs ni aux sélections.
- **Synchroniser** : un **clic milieu** (molette) ou **Maj+clic** sur une valeur l'applique à tous les blocs de la page filtrés sur le même champ (par exemple *Réseau*). Sur « Tous », tous ces blocs sont remis à « Tous ». Au-delà de 4 valeurs (liste déroulante), choisir la valeur puis faire un clic milieu sur la liste. L'infobulle de chaque valeur le rappelle. La comparaison porte sur le texte affiché, sans tenir compte des majuscules ni des accents. Si la valeur n'existe pas telle quelle dans un bloc, le rapprochement se fait par le début du texte : « Privé » garde « Privé sous contrat » et « Privé hors contrat » ; à l'inverse, « Privé sous contrat » garde « Privé ».
- **Selon la largeur du bloc** :
  - boutons côte à côte ;
  - un seul bouton portant la valeur active (`Public ▾`), qui ouvre la liste des choix ;
  - une icône d'entonnoir, pleine et bleue quand un filtre est actif.
- **Rechargement** : la page revient à la valeur prévue par l'administrateur.
- **Une seule valeur** : si toutes les lignes du bloc ont la même valeur (par exemple uniquement « Public »), le filtre n'est pas affiché, puisqu'il ne changerait rien.

**Page vide** : le message « Aucune donnée, pas d'élément sélectionné » signifie qu'il faut d'abord faire un choix dans les listes de sélection.

### Tableaux et fiches

- **Trier** : cliquer sur le nom d'une colonne. Un deuxième clic inverse l'ordre, un troisième revient à l'ordre d'origine.
- **Filtrer une colonne** : bouton de filtre de l'en-tête, puis cocher les valeurs à garder.
- **Description d'une colonne** : survoler le ⓘ.
- **Fiche liée** : le petit lien à côté d'une valeur ouvre la fiche de l'élément référencé.
- **Fiche seule** : les flèches ◀ ▶ (ou celles du clavier) passent d'un enregistrement à l'autre.
- **Modifier une valeur**, si le bloc l'autorise et si vos droits le permettent : double-clic sur la cellule, saisie, puis Entrée pour valider ou Échap pour annuler.
  - Les valeurs calculées (formules) ne sont pas modifiables.
  - Une modification refusée par les droits est signalée.

### Cartes

- **Point** : le survol affiche son étiquette. Si l'étiquette est mise en forme, elle s'ouvre au clic.
- **Couleur d'un point** : elle dépend d'une valeur (par exemple la circonscription).
- **Cercle autour d'un point** : il peut signaler une autre information (réseau, situation en quartier prioritaire…).
- **Légendes** : elles expliquent les couleurs, en bas à gauche pour les points et en haut à droite pour les zones.
- **Zones** (communes, intercommunalités, quartiers IRIS) : le survol affiche leur nom et leurs chiffres.
- **Quartiers prioritaires (QPV)** : en pointillés rouges. L'infobulle d'un établissement indique s'il est dans un QPV ou à proximité.
- **Sélection** : cliquer sur un point le sélectionne et met à jour les blocs liés.

### Imprimer et exporter

- **Imprimer** : tous les blocs sont dépliés le temps de l'impression. Le titre de la page et les sélections en cours figurent en tête. Pour un PDF, choisir « Enregistrer au format PDF » dans la fenêtre d'impression.
- **⤓ (CSV)** : exporte les lignes visibles du bloc (filtres, recherche et filtre rapide compris). Le fichier s'ouvre directement dans Excel ou LibreOffice.

### Sur smartphone

- Les blocs s'affichent les uns sous les autres.
- Les listes de sélection tiennent sur une seule ligne. Leur nom n'est plus affiché : la valeur choisie suffit à les reconnaître, et le texte complet apparaît à l'ouverture de la liste.

---

## 2. Composer une page (administrateurs)

Les actions **Disposition** et **Configurer** du menu ☰ n'apparaissent qu'aux administrateurs : les personnes qui ont accès à la table `W_Admin`.

### Ouvrir la configuration

**☰ → Configurer** ouvre un panneau sur la moitié droite de l'écran :
- l'**aperçu de la disposition** reste affiché en haut ;
- chaque option est expliquée au **survol** de son libellé (soulignement en pointillés) ;
- rien n'est appliqué avant **Enregistrer**, et **Annuler** ferme le panneau sans rien changer.

**Général**
- **Page réglée** : la page dont on règle la composition. Par défaut, c'est la page affichée (marquée « — affichée »). On peut en choisir une autre : l'affichage du widget ne change pas.
- **＋ Nouvelle page** : crée une page vide, sans toucher à la page affichée. **Dupliquer** crée une nouvelle page à partir de celle en cours de réglage (mêmes blocs, mêmes réglages).
- Quand la page réglée n'est pas la page affichée, un encadré jaune le signale. L'enregistrement range alors la page dans `W_Composition` sans changer l'affichage. Deux options :
  - **L'afficher dans ce widget après l'enregistrement** : le widget affichera désormais cette page ;
  - **L'ajouter au menu de navigation** (mode « Changer de page dans le widget ») : un lien vers la page est ajouté au menu commun.
- **Nom de la page** : identifie la page dans `W_Composition`. Si le nom existe déjà, le widget demande confirmation avant de remplacer l'autre page. Un nom ne peut pas commencer par « _ » (réservé).
- **Liens vers des formulaires Grist** (facultatif) : « + Ajouter un lien vers un formulaire », puis un libellé (ex. « Signaler un problème »), un commentaire au survol facultatif (affiché dans une infobulle sur le bouton) et l'adresse du formulaire. Pour obtenir l'adresse : dans Grist, ouvrir la vue Formulaire, cliquer sur « Publier », puis « Partager » et copier le lien. Chaque lien devient un bouton dans l'en-tête de la page, à gauche du menu ☰. Le formulaire s'ouvre dans une fenêtre au-dessus de la page, ou dans un nouvel onglet si la case « nouvel onglet » est cochée. La fenêtre se ferme avec ✕, Échap ou un clic à côté, et toute seule après l'envoi du formulaire ; la page est alors rechargée pour montrer la nouvelle réponse. La fermeture automatique fonctionne si l'utilisateur peut lire la table du formulaire ; sinon, réglez dans Grist une redirection après l'envoi (n'importe quelle adresse). Le bouton ↗ de la fenêtre ouvre le formulaire dans un nouvel onglet. Seules les adresses en https sont acceptées.
- **Titre affiché** : laissé vide, il libère de la place en haut de page.

### Choisir et régler les vues

1. **Vues disponibles** : choisir une page Grist, puis cocher ses vues. On peut combiner des vues de plusieurs pages.
2. **Vues retenues** : chaque vue cochée devient un bloc.
   - Les flèches ↑ ↓ règlent l'ordre ; ✕ retire le bloc (la vue Grist n'est pas supprimée).
   - Chaque bloc a ses réglages :

| Réglage | Effet |
|---|---|
| Largeur, Colonne, Hauteur (lignes) | Place du bloc dans la grille de 6 colonnes |
| Taille | Hauteur maximale ; au-delà, le contenu défile dans le bloc |
| À l'ouverture | Bloc replié ou déplié à l'arrivée sur la page |
| À la ligne | Le bloc commence une nouvelle rangée |
| Figer à l'écran | Le bloc reste visible pendant le défilement d'un bloc voisin. Plusieurs blocs figés d'une même colonne s'empilent. Un bloc déplié trop haut défile à l'intérieur de son cadre ; un bloc dont même l'en-tête ne tient plus défile normalement, sous les autres |
| Édition des champs | Autorise la modification des valeurs (droits Grist respectés) |
| Afficher les champs vides | Pour les fiches de ce bloc |
| Largeur des colonnes | Ajustées (sans ascenseur horizontal), celles de Grist, ou automatiques |
| Afficher toutes les fiches | Une vue fiche affichée en liste |
| Liste de sélection | Le bloc devient une liste déroulante dans l'en-tête |
| **Filtre rapide**, **Filtre à l'ouverture** | Voir ci-dessous |

### Disposition

- **Section « Disposition » du panneau** :
  - **Mode ultracompact** : les blocs prennent la largeur de leurs données.
  - **Combler automatiquement les espaces libres** : un petit bloc peut remonter dans un trou.
  - **Empiler les blocs sans trous** : chaque colonne s'empile indépendamment.
- **☰ → Disposition** (hors du panneau) : on déplace les blocs à la souris et on les redimensionne par leur coin inférieur droit. Terminer par *Enregistrer* ou *Annuler*.

### Filtre rapide

Pour ajouter les boutons `Tous | Public | Privé` à un bloc :
1. Dans les réglages du bloc, **Filtre rapide** : choisir le champ (par exemple *Réseau*).
   - Les champs de la vue sont proposés d'abord, puis les autres colonnes de la table.
   - Un champ non affiché peut donc servir de filtre.
2. **Filtre à l'ouverture** : *Tous*, ou la valeur à présélectionner.

Le filtre est disponible pour les tableaux, les listes de fiches, les graphiques et les cartes.

### Listes de sélection

Pour une vue affichée en **Liste de sélection** :
- **Colonne affichée** : le texte proposé dans la liste.
- **Ordre** : alphabétique, ou celui de la vue Grist.
- **Regrouper par** : intertitres dans la liste (par exemple les écoles par commune).
- **ID de synchronisation** : les listes qui portent le même identifiant gardent la même sélection d'une page à l'autre.

### Cartes : réglages

| Réglage | Effet |
|---|---|
| Étiquette | Colonne affichée au survol (par défaut celle de la carte Grist) |
| Couleur selon | Couleur des points selon une colonne |
| Contour selon | Cercle autour des points : selon une colonne, avec jusqu'à 3 couleurs et conditions (`=`, `≠`, `<`, `≤`, `>`, `≥`, `contient`), ou **situation QPV (calculée)** |
| Quartiers prioritaires (QPV) | Affiche les périmètres des QPV |
| Proximité d'un QPV | Distance retenue pour « à proximité » (0 à 500 m) |
| Zonage | Communes, EPCI ou IRIS, dessinés sous les points |
| Couleur des zones | Une couleur par zone, nombre de points, somme d'une colonne, ou valeur d'une table Grist reliée par code |
| Code INSEE | Colonne du code commune ; ou « position des points » pour le déduire des coordonnées |
| Étiquettes toujours visibles | Affiche toutes les étiquettes en permanence |

**Colorer les zones avec vos propres données** (par exemple la population des 3-10 ans par IRIS) :
1. Importer une table dans Grist, avec une colonne de code :
   - code IRIS à 9 caractères pour les IRIS ;
   - code INSEE pour les communes ;
   - SIREN pour les EPCI.
2. Couleur des zones → *selon une table Grist* : choisir la table, la colonne du code et la colonne de la valeur.

### Menu de navigation

Section **5. Navigation entre pages**. Ce réglage est commun à toutes les configurations.

- **Adresse du document** : adresse de base du document Grist (https).
- **Changer de page dans le widget** : le menu bascule de configuration sans recharger Grist. Recommandé quand toutes les configurations sont réunies dans une seule page Grist.
- **Ouvrir les pages en mode page unique** : les liens ouvrent Grist sans ses menus.
- **Pour chaque lien** :
  - libellé ;
  - page Grist, ou **— ce widget —** ;
  - configuration à afficher ;
  - visibilité : *tous*, ou *si accès à* une table (le lien n'apparaît qu'aux personnes qui voient au moins une ligne de cette table).

### Enregistrer

**Enregistrer** applique la configuration et l'écrit dans la table `W_Composition` du document. Les filtres rapides reviennent alors à leur valeur à l'ouverture.

---

## 3. Questions fréquentes

**Une valeur ne correspond pas à ce que montre Grist.**
Le widget affiche les colonnes de la vue Grist. Vérifiez la vue native, puis choisissez **☰ → Actualiser**.

**Un bloc a disparu.**
Il est sans données et l'option « Masquer les blocs sans données » est active. Faites une sélection dans les listes.

**L'action Configurer n'apparaît pas dans le menu.**
Vous n'avez pas accès à la table `W_Admin` : seuls les administrateurs configurent les pages.

**J'ai renommé une colonne ou une vue dans Grist.**
Le panneau **Configurer** relit la structure à chaque ouverture : les nouveaux noms y apparaissent. Les colonnes déjà choisies dans les réglages suivent automatiquement leur renommage, pour les configurations enregistrées depuis la version 0.8.5. Pour l'affichage des pages, choisissez **☰ → Actualiser**.

**Les modifications du widget n'apparaissent pas après une mise à jour.**
Rechargez la page avec **Ctrl + F5** pour vider le cache du navigateur.

**Une carte reste vide.**
- Vérifiez que les colonnes de latitude et de longitude sont renseignées.
- Pour les contours des communes, la colonne **Code INSEE** doit contenir un code à 5 chiffres, et non le nom de la commune. Sinon, choisissez « position des points ».

**Où voir la version du widget et ses nouveautés ?**
Dans le titre de la fenêtre **☰ → Aide**, onglet **Nouveautés**. Les administrateurs la voient aussi en bas du panneau **Configurer**.
