# Page composée pour Grist

Widget personnalisé [Grist](https://www.getgrist.com/) qui rassemble sur **une seule page, condensée et lisible**, plusieurs vues natives d'un document : tableaux, fiches, listes de fiches, graphiques natifs et avancés, cartes et listes déroulantes.

Le widget ne duplique rien. Il **relit la configuration des vues Grist** (tables de métadonnées `_grist_*`) et en reproduit le rendu. Cela comprend les colonnes affichées, le tri, les filtres, les liaisons entre vues, la mise en forme conditionnelle et la disposition des fiches. Quand une vue change dans Grist, la page composée suit.

---

## Sommaire

- [Fonctionnalités](#fonctionnalités)
- [Installation](#installation)
- [Préparer le document Grist](#préparer-le-document-grist)
- [Utilisation](#utilisation)
- [Cartes et zonages](#cartes-et-zonages)
- [Sécurité et confidentialité](#sécurité-et-confidentialité)
- [Dépendances](#dépendances)
- [Structure du code](#structure-du-code)
- [Limites connues](#limites-connues)
- [Licence et sources des données](#licence-et-sources-des-données)

---

## Fonctionnalités

**Vues prises en charge**

| Vue Grist | Rendu dans la page |
|---|---|
| Tableau | Tableau à largeurs ajustées, en-têtes fixes, tri et filtres par colonne, recherche, colonnes figées |
| Fiche | Fiche avec la disposition de la vue Grist, navigation précédent / suivant, ou toutes les fiches en liste |
| Fiches | Liste de fiches, largeur réglable |
| Graphique | Graphiques natifs (barres, lignes, secteurs, aires…) avec Chart.js |
| Graphique avancé | Widget Plotly de Grist, sources de données comprises |
| Carte | Widget carte de Grist avec Leaflet, voir [Cartes et zonages](#cartes-et-zonages) |
| Liste déroulante | Affichée dans l'en-tête comme liste de sélection qui pilote les autres blocs |

**Comportements repris de Grist**
- Liaisons entre vues : filtre, curseur, tables de synthèse.
- Mise en forme : couleurs, gras, règles conditionnelles de cellule et de ligne, pastilles des choix.
- Descriptions de colonnes en infobulle.
- Fiche d'un enregistrement référencé, ouverte en fenêtre superposée.
- **Édition** des champs dans les tableaux et les fiches, si le bloc l'autorise :
  - texte, nombres, dates, choix, références, références multiples ;
  - conditions des listes déroulantes ;
  - les règles d'accès de Grist s'appliquent, les lecteurs restent en lecture seule.

**Mise en page**
- Grille de 6 colonnes : largeur, colonne de départ, hauteur en rangées, retour à la ligne.
- Mode ultracompact : blocs ajustés à leurs données.
- Mode empilé sans trous.
- **Mode Disposition** : déplacer et redimensionner les blocs à la souris.
- Blocs repliables, état à l'ouverture réglable, blocs figés à l'écran, plein écran.
- Affichage adapté aux smartphones.

**Navigation et export**
- Menu commun à toutes les pages composées. Les pages que l'utilisateur ne peut pas lire sont masquées.
- Changement de page instantané, dans le widget.
- Listes de sélection synchronisées d'une page à l'autre.
- Impression / PDF.
- Export CSV par bloc : séparateur `;`, ouverture directe dans Excel.

---

## Installation

Le widget est un **fichier HTML unique**, sans étape de construction.

1. **Héberger les fichiers** : déposer `page-composee.html` et `qpv-bretagne.geojson` (couche QPV, facultative) dans un dépôt GitHub, puis activer **GitHub Pages** (*Settings → Pages → Deploy from a branch → main / root*).
   Adresse obtenue :
   ```
   https://<compte>.github.io/<dépôt>/page-composee.html
   ```
2. **Ajouter le widget dans Grist** :
   - *Ajouter un widget → Personnalisé*, sur n'importe quelle table ;
   - *URL personnalisée* : coller l'adresse ci-dessus ;
   - *Niveau d'accès* : **Accès complet au document**. Le widget doit lire les métadonnées des vues.
3. **Mettre à jour** : remplacer le fichier dans le dépôt, attendre la republication (1 à 2 minutes), puis recharger Grist avec **Ctrl+F5**.

> Tout autre hébergement statique en HTTPS convient aussi, par exemple un serveur interne. Le fichier GeoJSON des QPV doit être placé à côté du widget, ou son adresse indiquée dans la configuration de la carte.

---

## Préparer le document Grist

Le widget enregistre sa configuration **dans le document**. Elle survit donc aux mises à jour du code.

| Table | Rôle | Création |
|---|---|---|
| `W_Composition` | Une ligne par page composée (`Nom`, `Config` en JSON). Contient aussi deux lignes réservées : `_Navigation` (menu commun) et `_Securite` (témoin de protection) | Automatique au premier enregistrement |
| `W_Admin` | Détermine qui peut configurer : seules les personnes qui voient au moins une ligne de cette table ont accès au bouton **Configurer** et au mode **Disposition** | À créer (une ligne suffit) |

**Règles d'accès recommandées**
- `W_Admin` : lecture réservée aux propriétaires, par exemple refuser la lecture si `user.Access != OWNER`.
- `W_Composition` : lecture pour tous, **modification réservée aux propriétaires**.

Masquer le bouton ⚙ n'est qu'un confort. La vraie protection, ce sont ces règles d'accès.

Sans table `W_Admin`, tout utilisateur peut configurer. C'est pratique pour une première mise en place, à corriger ensuite.

---

## Utilisation

**Composer une page** (bouton **Configurer**)
1. **Vues disponibles** : choisir une page Grist, cocher ses vues. Les vues de plusieurs pages peuvent se combiner.
2. **Vues retenues** : ordre d'affichage et réglages de chaque bloc (largeur, hauteur, édition, liste de sélection, options de carte…).
3. **Disposition** : grille, mode ultracompact, empilement sans trous. L'aperçu en haut du panneau se met à jour en direct.
4. **Affichage** : masquer les champs ou les blocs vides, hauteur des graphiques et des tableaux.
5. **Navigation** : menu commun. Chaque lien peut être réservé aux personnes qui ont accès à une table donnée.

Chaque option est expliquée au survol de son libellé.

**Plusieurs pages composées**
- Une configuration porte un **nom**. Deux widgets qui utilisent le même nom partagent la même configuration.
- Le widget retrouve sa configuration par ce nom. À défaut, il prend la seule configuration liée à sa table, ou propose de choisir.

**Listes de sélection**
- Une vue peut s'afficher en liste déroulante dans l'en-tête : options *Colonne affichée*, *Ordre* et *Regrouper par*.
- Des listes qui portent le même **identifiant de synchronisation** partagent leur sélection d'une page à l'autre.

---

## Cartes et zonages

Un bloc carte reprend le widget carte de Grist : colonnes Nom / Latitude / Longitude, fond de carte. Les coordonnées en Lambert 93 et les virgules décimales sont acceptées.

**Points**
- **Étiquette** : par défaut la colonne « Name » de la carte Grist. Si elle contient du HTML, l'étiquette s'ouvre au clic, après nettoyage (voir Sécurité).
- **Couleur selon** une colonne : une couleur par valeur, ou des classes pour un nombre. Les valeurs invalides sont en rouge.
- **Contour selon** une colonne, avec 3 couleurs choisies au plus (conditions `=`, `≠`, `<`, `≤`, `>`, `≥`, `contient`), ou selon la **situation QPV**.

**Zonages** (sous les points)

| Zonage | Source | Remarque |
|---|---|---|
| Communes | [geo.api.gouv.fr](https://geo.api.gouv.fr) | Communes qui contiennent des points |
| EPCI | geo.api.gouv.fr, communes fusionnées | EPCI entiers |
| IRIS | Service WFS de la Géoplateforme IGN, couche `STATISTICALUNITS.IRISGE:iris_ge` | Communes découpées en IRIS uniquement |
| QPV | Fichier GeoJSON fourni (QPV 2024, ANCT) | Points dans un QPV ou à moins de X m |

**Code INSEE des points**
- La commune d'un point est lue dans une colonne de code INSEE (directement ou via une référence).
- À défaut, elle est **déduite de la position du point**.

**Couleur des zones**
- Une couleur par zone, ou un dégradé selon le nombre de points ou la somme d'une colonne.
- Ou une valeur lue dans **une table Grist reliée par code**, pour afficher des données INSEE par IRIS par exemple. Le code est :
  - le code INSEE pour les communes ;
  - le SIREN pour les EPCI ;
  - le code IRIS à 9 caractères pour les IRIS.

**Couche QPV pour un autre territoire**
1. Télécharger les périmètres sur [data.gouv.fr (ANCT)](https://www.data.gouv.fr/datasets/quartiers-prioritaires-de-la-politique-de-la-ville-qpv).
2. Filtrer les départements voulus.
3. Convertir en WGS84 (EPSG:4326).
4. Déposer le fichier à côté du widget, puis indiquer son nom dans l'option *Fichier des QPV*.

Le fichier fourni couvre les départements 22, 29, 35 et 56.

---

## Sécurité et confidentialité

- **Droits** : le widget passe par l'API de Grist et ne contourne aucune règle d'accès. Les lecteurs (`readonly`) ne peuvent rien modifier.
- **Affichage des données** : toutes les valeurs insérées dans la page sont échappées.
- **HTML des étiquettes de carte** : nettoyé par DOMPurify. La mise en forme est conservée ; scripts et gestionnaires d'événements sont retirés.
- **Bibliothèques externes** : versions figées, vérifiées par empreinte d'intégrité (SRI). Un fichier altéré sur le CDN est refusé par le navigateur.
- **Liens du menu** : seules les adresses `https://` sont acceptées.
- **Export CSV** : les textes commençant par `=`, `+`, `-` ou `@` sont neutralisés, pour éviter qu'Excel ne les interprète comme des formules.
- **Données envoyées à des services tiers** :
  - avec un zonage, les **codes INSEE** des communes et, si le code manque, les **coordonnées d'un point** sont transmis à geo.api.gouv.fr ;
  - avec les IRIS, des codes INSEE sont transmis au service de l'IGN ;
  - le fond de carte est chargé depuis OpenStreetMap, ou le fournisseur réglé dans la carte Grist ;
  - aucune autre donnée du document ne quitte le navigateur.
- **Compte d'hébergement** : quiconque peut modifier le dépôt modifie le widget de tous les utilisateurs. Activez la double authentification et limitez les droits d'écriture.

---

## Dépendances

Toutes sont chargées depuis un CDN, en version figée, avec empreinte d'intégrité.

| Bibliothèque | Version | Usage | Chargement |
|---|---|---|---|
| grist-plugin-api | — | API des widgets Grist | Au démarrage |
| Chart.js | 4.4.1 | Graphiques natifs | Au démarrage |
| Leaflet | 1.9.4 | Cartes | À la première carte |
| Plotly | 2.35.2 | Graphiques avancés | Au premier graphique avancé |
| DOMPurify | 3.2.6 | Nettoyage du HTML des étiquettes | Si une étiquette contient du HTML |
| polygon-clipping | 0.15.7 | Fusion des communes en EPCI | Avec le zonage EPCI |

Police : Marianne.

---

## Structure du code

Le fichier est commenté. Un **sommaire** en tête du script décrit les parties, le cycle de vie, le stockage et le schéma de configuration. Chaque fonction est précédée d'une ligne d'explication.

```
<style>    grille, blocs, tableaux, fiches, cartes, panneau de configuration, impression
<body>     en-tête (menu, barre d'outils, listes de sélection), grille, panneau
<script>
  État (objet S) et utilitaires
  Métadonnées      loadMeta, getInfo           lecture des vues Grist
  Données          rowsFor, selectedRowId      filtres, tri, liaisons
  Rendu des blocs  renderTable, renderSingle, renderCards, renderChart,
                   renderAdvChart, renderMap (+ zonages, QPV)
  Rendu principal  render() via scheduleRender()
  Interactions, mode Disposition, export, configuration, démarrage (init)
```

**Cycle de vie**
1. `grist.onOptions` → `init()` : métadonnées, configurations, menu, droits.
2. `render()` : premier affichage.
3. Ensuite, toute modification (sélection, données, options) passe par `scheduleRender()`. Un rendu doublé par un plus récent est abandonné. Les dessins lourds (cartes, graphiques, grands tableaux) sont différés après l'affichage.

**Règles de contribution**
- Toute valeur issue des données ou de la configuration passe par `esc()` avant d'être insérée en HTML.
- Une nouvelle bibliothèque est ajoutée à `LIBS`, avec sa version figée et son empreinte SRI.
- Une nouvelle option de bloc est déclarée dans `renderConfig()`, avec une explication au survol.

**Diagnostic** : la console du navigateur affiche une ligne `page « … » calculée en … ms`. Elle donne le nombre de blocs affichés, masqués ou non pris en charge, et la raison pour chaque bloc vide.

---

## Limites connues

- Formulaires et widgets personnalisés autres que carte et graphique avancé : non affichés.
- Conditions de liste déroulante qui utilisent `user` : la liste complète est proposée, et Grist valide à l'enregistrement.
- Contours geo.api.gouv.fr simplifiés : de fins traits peuvent subsister à l'intérieur d'un EPCI fusionné.
- Très grandes tables (plusieurs centaines de milliers de lignes) : le premier chargement peut prendre quelques secondes. Les tables sont ensuite en cache, et les autres pages du menu sont préchargées en arrière-plan.

---

## Licence et sources des données

- **Code** : licence à préciser (par exemple MIT ou Licence Ouverte / Etalab 2.0).
- **QPV 2024** : © ANCT, [Licence Ouverte 2.0](https://www.etalab.gouv.fr/licence-ouverte-open-licence/).
- **Contours des communes et EPCI** : [API Découpage administratif](https://geo.api.gouv.fr), IGN / INSEE.
- **Contours IRIS** : © IGN – INSEE, via la Géoplateforme.
- **Fond de carte** : © contributeurs [OpenStreetMap](https://www.openstreetmap.org/copyright).
