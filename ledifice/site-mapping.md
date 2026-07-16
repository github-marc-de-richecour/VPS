# L'ÉDIFICE — Cartographie du site (pages référencées et non référencées)

> Reconnaissance réalisée le 16/07/2026 via l'index des moteurs de recherche.
> Détail complet des URLs dans les fichiers CSV joints (`urls-ancienne-ui.csv`,
> `urls-nouvelle-ui.csv`, `documents.csv`, `domaines-connexes.csv`).

## 1. Synthèse chiffrée

| Catégorie | Nombre d'URLs uniques | Fichier |
|---|---:|---|
| **Ancienne UI** — pages HTML numérotées | **674** | `urls-ancienne-ui.csv` |
| **Nouvelle UI** — URLs propres | **551** | `urls-nouvelle-ui.csv` |
| **Documents** — PDF téléchargeables | **45** | `documents.csv` |
| **Domaines connexes** (4plus + edition) | **9** | `domaines-connexes.csv` |
| **Total référencé** | **1 279** | — |

> ⚠️ Il s'agit d'une **borne inférieure** : seules les pages indexées par les
> moteurs sont visibles ici. Le site annonce **plus de 5 000 planches** ; la
> majorité de l'ancien fonds n'est donc pas remontée par cette méthode (voir §7).

## 2. Le cœur du problème : deux interfaces qui coexistent

Le site fait cohabiter **deux générations de pages** avec deux systèmes d'URL
totalement différents. C'est la source directe du problème signalé par le client
(« il ne faut pas qu'on ait des pages à l'ancienne UI et d'autres avec la nouvelle »).

### Ancienne UI — pages statiques numérotées
`https://www.ledifice.net/{CODE}.html`

Le `CODE` suit une nomenclature interne `{préfixe}{numéro}-{suffixe}` :

| Élément | Valeurs | Signification |
|---|---|---|
| Préfixe numérique | `1xxx` | Accueil, plan, à propos, contact, obédiences, revues, abonnements |
| | `2xxx` | Mots clés, vitrines éditeurs, recueils, lettres mensuelles |
| | `3xxx` | **1er degré — Apprenti** |
| | `6xxx` | **2e degré — Compagnon** |
| | `7xxx` | **3e degré — Maître** |
| Préfixe alphabétique | `Axxx` / `hgindex` | Hauts grades (4e degré et +) |
| | `Rxxx` | Recueils (collections thématiques de planches) |
| | `Lxxx` | Ouvrages / mémentos édités |
| | `Bxxx` | Bulletins « Bulim » |
| | `Kxxx` | Revue *Khalam* (Memphis-Misraïm) — en PDF |
| | `Sxxx` | *Une Parole Circule / Sub Rosa* (Genève) — en PDF |
| | `Pxxx` | Guides et études |
| Suffixe | `-0`…`-9`, `-A`…`-Z` | Variante / version / langue de la même planche |

Le suffixe explique une **très forte redondance** : un même thème existe souvent
en 5 à 12 versions. Exemples relevés :
- **Le Tablier** : `3003-4`, `3003-5`, `3003-7`, `3003-A`, `3003-B`, `3003-C`, `3003-G`, `3003-K` (8 pages)
- **La Chambre du Milieu** : `7521-0`, `7521-1`, `7521-6`, `7521-7`, `7521-A`, `7521-B`, `7521-C` (7 pages)
- **Les 5 points parfaits de la maîtrise** : `7337-1/2/4/8/9/B/C/F` (8 pages)

### Nouvelle UI — URLs propres (CMS)
`https://ledifice.net/{section}/{sous-catégorie}/{slug}`

Arborescence hiérarchique par degré et par thème :

| Section (1er segment) | Rôle |
|---|---|
| `/apprenti/…` et `/1er-degre/…` | 1er degré |
| `/compagnon/…` | 2e degré |
| `/maitre/…` | 3e degré |
| `/maitre-secret/…` | 4e degré |
| `/grand-maitre-architecte/12/…`, `/grand-elu-parfait-et-sublime-macon/14/…` | 12e, 14e degrés |
| `/chapitre/17|18/…`, `/areopage/30|32/…`, `/hauts-grades/…` | Hauts grades |
| `/planches/{grade}/…` | Pages « index » d'un grade |
| `/abonnement`, `/glossaire-maconnique`, `/politesse-maconnique` | Pages système / transverses |

## 3. Détail : Ancienne UI (674 pages)

| Section | Pages |
|---|---:|
| 1er degré (Apprenti — `3xxx`) | 217 |
| 3e degré (Maître — `7xxx`) | 170 |
| 2e degré (Compagnon — `6xxx`) | 136 |
| Général / accueil / revues (`1xxx`) | 61 |
| Mots clés / éditions / recueils / lettres (`2xxx`) | 52 |
| Recueils (`R`) | 16 |
| Ouvrages / mémentos (`L`) | 12 |
| Guides / études (`P`) | 4 |
| Bulletins Bulim (`B`) | 3 |
| Hauts grades (`A`), Khalam (`K`), divers | 3 |

**Ce sont ces pages qui portent l'ancien design et qui, pour l'essentiel, ne
sont plus référencées dans la navigation actuelle.** Ce sont la cible prioritaire
de la refonte / du nettoyage.

> Note : il n'existe **pas** de pages numérotées `8xxx`/`9xxx`. Les hauts grades
> anciens sont rangés sous les préfixes `A`, `R`, `L` et via le nouveau schéma.

## 4. Détail : Nouvelle UI (551 pages)

| Section | Pages |
|---|---:|
| 1er degré (Apprenti) | 245 |
| 3e degré (Maître) | 156 |
| 2e degré (Compagnon) | 79 |
| 4e degré (Maître Secret) | 22 |
| Chapitre (15e–18e) | 18 |
| Index par grade (`/planches/*`) | 16 |
| Aréopage (19e–30e) | 5 |
| 12e / 14e degrés | 5 |
| Pages système / hauts grades divers / accueil | 5 |

## 5. Le recouvrement ancienne ↔ nouvelle UI

De nombreuses planches existent **en double** : une version ancienne (`.html`
numérotée) **et** une version nouvelle (URL propre). Preuve directe : plusieurs
URLs de la nouvelle UI **embarquent encore l'ancien identifiant** dans leur slug,
par exemple :

- `www.ledifice.net/7078-1.html` → `ledifice.net/maitre/la-reine-de-saba/7078-1`
- `www.ledifice.net/6009-5.html` → `ledifice.net/compagnon/compagnonnage/6009-5-le-compagnon-entre-apprenti-et-maitre`
- `www.ledifice.net/3286-F.html` → `ledifice.net/apprenti/lapprenti/3286-f-le-guide-utile-pour-les-apprentis`
- `www.ledifice.net/3169-B.html` → `ledifice.net/apprenti/le-bas/3169-b-les-trois-fenetres-du-tableau-de-loge`

C'est l'enjeu central de la refonte : **une même planche peut être accessible via
deux URLs et deux mises en page différentes**. Il faut décider, planche par planche,
quelle version fait foi, rediriger l'autre, et harmoniser le design.

## 6. Documents (45 PDF) et domaines connexes

**Documents** (`documents.csv`) — tous des PDF hébergés sur `www.ledifice.net` :
- **Index / listes** : `2501-*`, `2502-*`, `2503-A`, `2504-1` (listes de recueils et de mots clés), catalogues éditeurs `2651-D` (Dervy) et `2651-Y` (Fonds Bayard).
- **Revue *Khalam*** (Memphis-Misraïm) : 10 numéros `K000-0` → `K036-0`.
- **Bulletins *Une Parole Circule / Sub Rosa*** (Genève) : 19 numéros `S002-0` → `S040-Z`.
- **Guides** : `P136-8` (Guide L'Édifice), `L460-0` (ouvrages NUMERILIVRE), `R100-F` (présentation du Forum).

**Domaines connexes** (`domaines-connexes.csv`) — à intégrer à la réflexion de refonte :
- **`ledifice-4plus.net`** — site des **hauts grades**, accès protégé par mot de passe (`/protected/`, portail `/customeradmin/`). Réplique l'ancien schéma (`1000-0.html`, doc `A000-2.doc`). ⚠️ Design ancien également.
- **`ledifice-edition.net`** — **boutique** en ligne (PrestaShop : `category.php`, `manufacturer.php`).

## 7. Méthode, limites et prochaines étapes

**Méthode.** L'accès HTTP direct à `ledifice.net` étant bloqué par la politique
réseau de l'environnement (impossible de crawler le site, la Wayback Machine et
robots/sitemap sont aussi inaccessibles), la cartographie a été bâtie via l'**index
des moteurs de recherche**, avec une reconnaissance parallélisée : ratissage par
plages de numéros pour l'ancien schéma, par degré/catégorie pour le nouveau, et
par type de fichier pour les documents.

**Limites.**
1. **Couverture partielle.** ~1 280 URLs remontées vs. 5 000+ planches annoncées :
   l'essentiel de l'ancien fonds n'est pas indexé et reste invisible à cette méthode.
2. **Statut « vivant » non vérifié.** On ne sait pas, sans accès serveur, quelles
   anciennes pages sont encore réellement en ligne, lesquelles redirigent déjà vers
   la nouvelle UI, et lesquelles renvoient une 404.

**Prochaines étapes recommandées pour un inventaire exhaustif à 100 %.**
- Obtenir du client un **accès serveur / FTP** ou un **export du CMS** → liste réelle
  et complète des fichiers (`.html`, `.pdf`) et des entrées de la base.
- Récupérer le **`sitemap.xml`** et les **fichiers `2501-*.pdf` / `2504-1.pdf`**
  (« Tous les Recueils », « Tous les Mots Clé ») qui sont des index internes exhaustifs.
- Croiser cet inventaire réel avec les CSV de ce dossier pour établir, planche par
  planche, la table de correspondance **ancienne URL → nouvelle URL → statut → action**
  (à refondre / à rediriger / à supprimer).

**Objectif final de la refonte.** Un site où **100 % des pages** partagent la
nouvelle UI, sans page orpheline à l'ancien design, avec des redirections propres
depuis les anciennes URLs numérotées vers les nouvelles.
