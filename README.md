# my-budget

Application web autonome de **suivi de budget mensuel et annuel**, inspirée des tableurs de type *focus.daily* mais entièrement privée : aucune donnée ne quitte votre navigateur.

Un seul fichier HTML, aucune installation, aucun serveur. Il suffit de l'ouvrir dans un navigateur.

**➡️ Démo en ligne : https://pmeyssonnier.github.io/my-budget-app/**

> L'application reste 100% côté navigateur, même hébergée sur GitHub Pages : aucune donnée n'est envoyée au serveur.

## Fonctionnalités

- **Récapitulatif annuel** : revenus, dépenses, frais fixes, crédits, épargne, reste à vivre, répartition en donut, évolution mensuelle, top des dépenses par catégorie.
- **Vue mensuelle** : prévu vs réel par catégorie, avec progression.
- **Transactions** : ajout manuel, correction de catégorie, suppression.
- **Import de relevés** : lecture directe de fichiers **CSV**, **XLSX/XLS** et **PDF** (extraits bancaires, Visa/Mastercard). Détection automatique des colonnes, gestion des doublons.
- **Parseur dédié Belfius** : reconnaissance automatique du format d'extrait Belfius (mouvements numérotés, montants signés, exclusion des pages épargne-pension et décompte global).
- **Catégorisation automatique** par règles mots-clés, éditable, avec re-catégorisation en un clic.
- **Budget prévu** mensuel par catégorie.
- **Thème clair / sombre** avec bascule mémorisée.
- **Persistance** : `localStorage` (automatique) + export/import JSON.

## Utilisation

1. Ouvrir `mon-budget.html` dans un navigateur (double-clic).
2. Onglet **📥 Importer relevés** : glisser un extrait CSV, XLSX ou PDF.
3. Vérifier l'aperçu, ajuster les catégories si besoin.

## Confidentialité

Toutes les données restent **locales** au navigateur (aucun envoi réseau). Les bibliothèques SheetJS (lecture XLSX) et pdf.js (lecture PDF) sont chargées depuis un CDN au premier lancement, mais le contenu de vos fichiers n'est **jamais transmis**.

> ⚠️ Les exports JSON et les extraits bancaires contiennent des données personnelles sensibles. Le fichier `.gitignore` les exclut du dépôt — ne jamais les committer.

## Formats bancaires pris en charge

| Format | Statut |
|--------|--------|
| CSV (`;`, `,`, tabulation) | ✅ Détection auto des colonnes |
| XLSX / XLS | ✅ Via SheetJS |
| PDF Belfius | ✅ Parseur dédié |
| PDF autres banques | ⚙️ Parseur générique (à valider selon la mise en page) |
| PDF scanné (image) | ❌ Non lisible — exporter en CSV |

## Technique

- HTML + CSS + JavaScript vanilla, **fichier unique**, aucune dépendance de build.
- Graphiques dessinés en `canvas` natif (donut, aires), sans librairie.
- Dépendances runtime chargées via CDN : [SheetJS](https://sheetjs.com/), [pdf.js](https://mozilla.github.io/pdf.js/).

## Licence

Usage personnel.
