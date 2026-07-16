# L'ÉDIFICE — Accompagnement refonte visuelle

**Client :** L'ÉDIFICE — https://ledifice.net
**Nature du site :** « La plus grande bibliothèque de planches maçonniques » (5 000+ planches, plus de 100 obédiences, du 1er au 33e degré).
**Mission :** accompagnement sur la refonte visuelle complète du site.

## Le problème à résoudre

Le site a connu une migration vers un nouveau CMS à **URLs propres**, mais un grand
nombre d'**anciennes pages** (HTML statiques et PDF numérotés) sont toujours en ligne
et **orphelines** : elles ne sont plus référencées dans la navigation actuelle. Le
client n'a **plus le mapping complet** de son site.

Conséquence directe pour la refonte : deux interfaces coexistent aujourd'hui.

| | Ancienne UI | Nouvelle UI |
|---|---|---|
| **Schéma d'URL** | `www.ledifice.net/{préfixe}{numéro}-{suffixe}.html` (ou `.pdf`) | `ledifice.net/{degré}/{catégorie}/{slug}` |
| **Exemples** | `/3148-I.html`, `/2501-1.pdf`, `/R203-0.html`, `/L403-F.html`, `/B009-5.html` | `/apprenti/la-planche/plancher`, `/planches/maitre/planche-tracee` |
| **Statut** | Pages historiques, souvent non référencées | Pages de la refonte en cours |

**Objectif de ce dossier :** retrouver un maximum de pages non référencées (ancienne
et nouvelle UI) + les documents (PDF, etc.) hébergés à ces adresses, afin que **toutes**
les pages soient revues et harmonisées — pour qu'il ne reste aucune page « à l'ancienne
UI » à côté des nouvelles.

## Contrainte technique de la reconnaissance

L'accès HTTP direct à `ledifice.net` est **bloqué par la politique réseau** de
l'environnement d'exécution (403 au niveau du proxy d'egress). Impossible donc de
crawler le site directement (robots.txt, sitemap.xml, suivi des liens) ni d'utiliser
la Wayback Machine (également bloquée).

**Méthode retenue :** cartographie via l'**index des moteurs de recherche** (WebSearch),
en ratissant systématiquement par plages de numéros (ancien schéma), par degré/catégorie
(nouveau schéma) et par type de document (`filetype:pdf`, etc.), avec une reconnaissance
parallélisée sur plusieurs agents.

> Limite à connaître : l'index d'un moteur de recherche ne contient que les pages qu'il
> a explorées et retenues. La liste obtenue est donc une **borne inférieure** du nombre
> réel de pages. Pour un inventaire exhaustif à 100 %, il faudra compléter côté client
> (accès FTP/serveur, export CMS, ou déblocage réseau permettant un vrai crawl).

## Contenu du dossier

| Fichier | Description |
|---|---|
| `README.md` | Ce document (contexte, problème, méthode). |
| `site-mapping.md` | Cartographie complète et commentée du site (à plat + par section). |
| `urls-ancienne-ui.csv` | Toutes les pages HTML de l'ancien schéma numéroté trouvées. |
| `urls-nouvelle-ui.csv` | Toutes les pages du nouveau schéma à URLs propres trouvées. |
| `documents.csv` | Tous les documents (PDF, DOC…) hébergés sur le site. |
