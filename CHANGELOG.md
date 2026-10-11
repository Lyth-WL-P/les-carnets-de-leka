# Journal complet des évolutions et correctifs

Cet historique décrit ce qui a réellement évolué dans le site version après version. Il ne référence pas les paquets de livraison : l’objectif est de suivre les bugs corrigés, les choix techniques et les changements visibles dans le code.

## V165 — 2026-10-11 11:28 — Signature discrète sur la carte de contact

- ajout de la mention « Carnet de Leka » dans la carte de message privé ;
- ajout d'un petit avatar circulaire ;
- positionnement discret sur desktop ;
- adaptation responsive pour éviter les chevauchements sur mobile ;
- incrément du cache-busting de la feuille de style contact.
- Détail technique et contexte : [`historique/V165.md`](historique/V165.md)

## V164 — 2026-10-11 10:22 — Nettoyage des cartes de la popup

- `Apprendre le français` devient `Learn French`.
- Suppression des gros indicateurs AL / FR sur les deux cartes initiales.
- Aucun changement de destination ni de logique.
- JS passé en v164.
- Service worker passé en `leka-cache-v164`.
- Détail technique et contexte : [`historique/V164.md`](historique/V164.md)

## V163 — 2026-10-11 08:50 — Correction réelle de la phrase visible + cache

- la phrase modifiée n'était pas celle visible sur la carte de la capture ;
- le JS restait appelé en `?v=161` et le service worker restait en `leka-cache-v161`.
- toutes les pages passent à `carnets-de-leka.js?v=163`
- service worker : `leka-cache-v163`
- Détail technique et contexte : [`historique/V163.md`](historique/V163.md)

## V162 — 2026-10-11 08:46 — Phrase popup en anglais

- Modification unique : `Choose English or Shqip to learn French.`
- Détail technique et contexte : [`historique/V162.md`](historique/V162.md)

## V161 — 2026-10-11 08:39 — Langue de l'assistant selon le navigateur

- `sq` / `al` -> Shqip ;
- `en` -> English ;
- `de` -> Deutsch ;
- `fr` -> Français ;
- toute autre langue -> English.
- Détail technique et contexte : [`historique/V161.md`](historique/V161.md)

## V160 — 2026-10-11 08:31 — Assistant d'entrée discret

- apprendre l'albanais ;
- apprendre le français.
- Français -> `/`
- English -> `/en/`
- Deutsch -> `/de/`
- Détail technique et contexte : [`historique/V160.md`](historique/V160.md)

## V159 — 2026-10-11 08:23 — Contact sans écran de boot

- l'animation `SYS://LEKA.PROFILE` ne doit apparaître que sur les pages À propos ;
- elle est supprimée des 6 pages Contact & communauté.
- bloc `#about-boot` ;
- `about-geek.js` ;
- `about-geek.css` ;
- Détail technique et contexte : [`historique/V159.md`](historique/V159.md)

## V158 — 2026-10-11 08:17 — Contact & communauté centralisés

- 6 pages Contact & communauté créées.
- Deux choix immédiatement visibles : mur public ou message privé.
- Formulaire privé unique : question, suggestion, bug, partenariat, autre.
- Accès « signaler un bug » prérempli avec le bon sujet.
- Les 6 pages du mur affichent clairement que les messages sont publics après modération.
- Détail technique et contexte : [`historique/V158.md`](historique/V158.md)

## V157 — 2026-10-11 08:07 — Correction du slider des villes

- CSS slider intégré également aux feuilles principales déjà chargées ;
- feuille slider dédiée réincluse dans ce patch ;
- anciennes règles `.city-photo` neutralisées pour le slider ;
- images en `object-fit: contain` afin de ne pas les couper ;
- ratio du slider calculé à partir de la photo principale après son chargement ;
- Détail technique et contexte : [`historique/V157.md`](historique/V157.md)

## V156 — 2026-10-11 07:59 — Slider villes à 2 secondes

- villes France : oui
- villes Albanie : oui
- navigation manuelle inchangée
- pause au survol / focus inchangée
- swipe et clavier inchangés
- Détail technique et contexte : [`historique/V156.md`](historique/V156.md)

## V155 — 2026-10-11 07:50 — Slider photos des villes

- la photo principale et les images supplémentaires sont réunies dans un seul slider ;
- la galerie séparée sous la grande photo n'est plus rendue ;
- défilement automatique toutes les 5,2 secondes ;
- flèches, points et compteur ;
- clavier gauche/droite ;
- Détail technique et contexte : [`historique/V155.md`](historique/V155.md)

## V154 — 2026-10-10 23:12 — Finition SEO avant pause

- Pages sans H1 détectées au départ : 67
- H1 statiques ajoutés : 63
- Pages techniques volontairement non modifiées : 404 / offline / vérification Google
- Pages SEO autonomes sans H1 restantes : 0
- Fragment HTML non autonome sans H1 : `lecture/integration/carnets-de-leka-snippet.html`
- Détail technique et contexte : [`historique/V154.md`](historique/V154.md)

## V153 — 2026-10-10 22:45 — Correction visuelle du menu Apprendre

- feuille dédiée `/assets/css/nav-levels-v153.css` chargée explicitement sur toutes les pages avec le menu Apprendre ;
- largeur et hauteur du dropdown adaptées ;
- 5 niveaux empilés verticalement ;
- ajout de `Toutes les leçons / All lessons / Alle Lektionen / Të gjitha mësimet`
- niveaux déplacés juste sous cette entrée ;
- Détail technique et contexte : [`historique/V153.md`](historique/V153.md)

## V152 — 2026-10-10 22:38 — 5 niveaux dans le menu Apprendre

- ouvrir le menu `Apprendre` ;
- juste sous `Toutes les leçons`, afficher 5 accès compacts ;
- un accès direct par niveau.
- A1
- A1-A2
- Détail technique et contexte : [`historique/V152.md`](historique/V152.md)

## V151 — 2026-10-10 22:34 — Menu niveaux visible / injection runtime

- V150 contenait bien le menu statique dans les pages HTML et le CSS correspondant.
- Pour rendre l'affichage robuste même si une page HTML ancienne est encore servie ou si un rendu réécrit le contenu,
- Le JS ne crée rien si le bloc statique existe déjà, donc aucun doublon.
- injection runtime sur toutes les pages `data-page="lesson"` ;
- 5 liens absolus vers `#niveau1` à `#niveau5` ;
- Détail technique et contexte : [`historique/V151.md`](historique/V151.md)

## V150 — 2026-10-10 22:29 — 5 accès de niveaux sous toutes les leçons

- Niveau 1 / A1
- Niveau 2 / A1-A2
- Niveau 3 / A2-B1
- Niveau 4 / B1-B2
- Niveau 5 / B2+
- Détail technique et contexte : [`historique/V150.md`](historique/V150.md)

## V149 — 2026-10-10 22:19 — Ressources UK/DE et CTA Explore

- 8 PDF English -> Albanian créés.
- `/en/ressources/` charge `resources-en.json`.
- `/de/ressources/` conserve sa bibliothèque `resources-de.json` et ses 8 PDF allemands.
- Recherche, catégories et boutons de téléchargement localisés.
- Les cartes `Explore / Discover` ont un CTA plus petit.
- Détail technique et contexte : [`historique/V149.md`](historique/V149.md)

## V148 — 2026-10-10 22:09 — Humanisation multilingue complète

- toutes les pages HTML du site ;
- introductions de leçons ;
- textes de présentation des hubs ;
- pages Découvrir ;
- textes de ressources ;
- Détail technique et contexte : [`historique/V148.md`](historique/V148.md)

## V147 — 2026-10-10 22:04 — Humanisation éditoriale du site

- 71/71 blocs SEO éditoriaux réécrits avec une voix plus personnelle et moins répétitive ;
- 6 pages « À propos » reprises dans une voix plus directe et personnelle ;
- 15 introductions culturelles FR / EN / DE retravaillées sans changer les faits ;
- 3 pages d'accueil ont reçu des ajustements sur les longs textes promotionnels ;
- 2 tirets cadratins supprimés ;
- Détail technique et contexte : [`historique/V147.md`](historique/V147.md)

## V146 — 2026-10-10 21:57 — Deutsch -> Albanisch

- 50 interaktive Lektionen vollständig auf Deutsch synchronisiert.
- Sichtbare Wortschatzlisten nur noch Albanisch -> Deutsch.
- Kulturhinweise auf Deutsch synchronisiert.
- Alphabetseite und Aussprachehinweise für Deutschsprachige angepasst.
- Alphabet-Quiz und dynamische Alphabetdaten um deutsche Inhalte ergänzt.
- Détail technique et contexte : [`historique/V146.md`](historique/V146.md)

## V145 — 2026-10-10 21:44 — Header du site Apprendre l'albanais

- sélecteur intégré dans le header principal ;
- suppression de la double barre ;
- XP et langue d'interface regroupés à droite ;
- badge BETA supprimé ;
- libellés localisés :
- Détail technique et contexte : [`historique/V145.md`](historique/V145.md)

## V144 — 2026-10-10 21:39 — Suppression du badge BETA

- Le badge `BETA` a été retiré du sélecteur Learn French sur l'ensemble du silo `/francais/`.
- Détail technique et contexte : [`historique/V144.md`](historique/V144.md)

## V143 — 2026-10-10 21:35 — Refonte du header du silo français

- le sélecteur "Learn Albanian / Learn French" est intégré dans le header principal ;
- navigation, parcours, XP et langue d'interface sont regroupés dans une seule barre cohérente ;
- le gros espace réservé aux actions fixes a été supprimé ;
- responsive mobile revu sur deux lignes ;
- destination "Learn Albanian" corrigée sur la version EN : `/en/` ;
- Détail technique et contexte : [`historique/V143.md`](historique/V143.md)

## V142 — 2026-10-10 21:28 — Page À propos recentrée

- passage à un bloc unique centré ;
- largeur max du panneau : 980px ;
- largeur de lecture du texte : 820px ;
- breadcrumb aligné sur le même axe ;
- comportement mobile conservé ;
- Détail technique et contexte : [`historique/V142.md`](historique/V142.md)

## V141 — 2026-10-10 21:23 — Ressources : mot de passe et chargement

- `ressources-fr.js` utilisait `root` sans le définir dans son propre scope ;
- après déverrouillage, la porte disparaissait mais le JSON pouvait ne jamais charger ;
- l'ancien `localStorage` gardait la bibliothèque déverrouillée entre les visites, donc le mot de passe pouvait ne plus apparaître.
- `root` est maintenant lu depuis `body[data-root]` ;
- déverrouillage stocké seulement pour la session courante (`sessionStorage`) ;
- Détail technique et contexte : [`historique/V141.md`](historique/V141.md)

## V140 — 2026-10-10 21:18 — Cache JS / sélecteur de langue

- les pages du silo `/francais/` chargeaient encore `carnets-de-leka.js?v=103` ;
- le service worker utilisait encore `leka-cache-v96` et préchargeait du JS/CSS `v94` ;
- Apache gardait les fichiers JS en cache pendant 30 jours ;
- le service worker servait les JS/CSS depuis le cache avant le réseau.
- cache-busting `carnets-de-leka.js?v=140` sur 273 pages ;
- Détail technique et contexte : [`historique/V140.md`](historique/V140.md)

## V139 — 2026-10-10 21:15 — Sélecteur de langue

- Shqip (albanais)
- English
- Détail technique et contexte : [`historique/V139.md`](historique/V139.md)

## V138 — 2026-10-10 21:12 — Alignement Shqip -> Frëngjisht

- interface albanaise nettoyée des libellés français génériques ;
- `Aller au contenu` -> `Shko te përmbajtja` ;
- `Continuer` -> `Vazhdo` ;
- 6 nouveaux PDF Shqip -> Frëngjisht ;
- bibliothèque protégée par le même mot de passe et même présentation ;
- Détail technique et contexte : [`historique/V138.md`](historique/V138.md)

## V137 — 2026-10-10 21:08 — Additional English -> French resources

- French Numbers & Time
- 20 Essential French Verbs
- French Present Tense Quick Guide
- French Travel Pocket Kit
- French False Friends for English Speakers
- Détail technique et contexte : [`historique/V137.md`](historique/V137.md)

## V136 — 2026-10-10 20:57 — UK resources, menus and PDF cleanup

- Common EN UI chrome cleaned on 91 pages.
- Resource page placeholders, labels and filters converted to English.
- Resource JS now uses language-aware English copy for download buttons, categories and errors.
- The second language-switch handler was corrected (it was overriding the earlier fix).
- 8 English PDF resources cleaned:
- Détail technique et contexte : [`historique/V136.md`](historique/V136.md)

## V135 — 2026-10-10 20:48 — Verification des lecons UK

- Pages HTML verifiees : 60
- Lecons interactives verifiees : 51
- Restes albanais visibles detectes apres correction : 0
- Restes albanais dans les champs dynamiques `en` : 0
- Problemes `lang` / canonical detectes : 0
- Détail technique et contexte : [`historique/V135.md`](historique/V135.md)

## V134 — 2026-10-10 20:40 — UK / English cleanup

- fixed language detection for `/francais/en/...`;
- fixed language-switch URL generation inside the `/francais/` silo;
- English pages now force English dynamic lesson/category/track labels;
- removed the French selector entry from all English pages, keeping Shqip + English;
- corrected static Albanian leftovers in About, Alphabet, Resources and History;
- Détail technique et contexte : [`historique/V134.md`](historique/V134.md)

## V133 — 2026-10-10 20:11 — Humanisation des textes

- 9575 tirets cadratins supprimés dans les ressources texte du site.
- 71 pages SEO V127 réécrites pour supprimer le ton répétitif et les formulations trop mécaniques.
- Meta descriptions des 71 pages harmonisées avec une formulation plus naturelle.
- Plusieurs textes du parcours English -> French et de la home ont été reformulés.
- Aucun caractère `—` ne reste dans les fichiers texte du site.
- Détail technique et contexte : [`historique/V133.md`](historique/V133.md)

## V132 — 2026-10-10 20:06 — Panneau EN cliquable + menu langue simplifié

- retrait de « Français » du sélecteur de langue de `/francais/en/`;
- ajout de 4 zones cliquables sur le panneau illustré :
- Learn French → `./apprendre/index.html`
- Explore France → `./decouvrir/index.html`
- Daily practice → `./apprendre/dialogues.html`
- Détail technique et contexte : [`historique/V132.md`](historique/V132.md)

## V131 — 2026-10-10 20:01 — Panneau hero /francais/en/

- Remplace la mascotte + panneau HTML superposé par une illustration unique intégrée, comme sur les autres homes.
- Asset transparent, sans fond noir.
- Variantes responsive AVIF/WebP 480/720/960 px.
- Aucun changement SEO de contenu ou d’URL.
- Détail technique et contexte : [`historique/V131.md`](historique/V131.md)

## V130 — 2026-10-10 18:48 — English → French experience

- English home now explicitly targets English speakers learning French.
- Added a beginner quick-start route.
- Learning hub now starts with a clear 5-step A1 sequence.
- Corrected English UI copy that still referred to Albanian language/history/news.
- Reworked 51 interactive lesson pages:
- Détail technique et contexte : [`historique/V130.md`](historique/V130.md)

## V129 — 2026-10-10 — Suivi des recommandations SEO

- consolidation des recommandations déjà identifiées ;
- suivi de leur état de traitement ;
- préparation des priorités pour les corrections techniques et éditoriales suivantes.
- Détail technique et contexte : [`historique/V129.md`](historique/V129.md)

## V128 — 2026-10-10 — Audit backlinks et toxicité

- revue du profil de liens externes ;
- repérage des domaines ou liens pouvant mériter une vérification ;
- préparation d'une liste de candidats à examiner avant toute action de désaveu ;
- séparation claire entre problèmes techniques internes et signaux SEO externes.
- Détail technique et contexte : [`historique/V128.md`](historique/V128.md)

## V127 — 2026-10-10 10:24 — Suivi des 71 recommandations « mots clés de contenu »

- Principe : aucune répétition artificielle. Chaque page reçoit un paragraphe éditorial visible, une meta description cohérente avec la requête cible et, lorsqu’il existe, le JSON-LD est synchronisé.
- Détail technique et contexte : [`historique/V127.md`](historique/V127.md)

## V126 — 2026-10-10 10:19 — Quick wins du nouvel audit SEO

- titres explicites des 4 pages légales EN/DE ;
- alternatives textuelles ajoutées sur les pages signalées par l'audit ;
- page `/decouvrir/culture-musique-chants.html` allégée avec images responsive AVIF/WebP.
- sources originales : 687 Kio environ ;
- variantes AVIF 720 px représentatives : 126 Kio environ.
- Détail technique et contexte : [`historique/V126.md`](historique/V126.md)

## V125 — 2026-10-10 09:52 — Correction des 404 remontées par l'audit SEO

- `/apprendre/parcours.html`
- le lien interne pointe maintenant vers `#parcours` sur `/apprendre/`;
- une 301 protège les anciens liens externes / historiques.
- `/francais/apprendre/parcours.html`
- le lien interne pointe maintenant vers `#learn-tracks`;
- Détail technique et contexte : [`historique/V125.md`](historique/V125.md)

## V124 — 2026-10-10 09:43 — Correction du carré noir sur le panneau de la home Français

- mêmes noms de fichiers ;
- même structure ;
- correction purement visuelle, compatible avec la home `/` et `/francais/`.
- Détail technique et contexte : [`historique/V124.md`](historique/V124.md)

## V123 — 2026-10-10 09:38 — Harmonisation performance des six pages d’accueil

- `/`
- `/en/`
- `/de/`
- `/francais/`
- `/francais/en/`
- Détail technique et contexte : [`historique/V123.md`](historique/V123.md)

## V122 — 2026-10-10 09:29 — LCP, cache AVIF et CSS du miroir français

- `image/avif` reçoit maintenant le même cache 1 an + immutable que WebP/JPEG/PNG.
- l'anti-hotlink reconnaît aussi l'extension AVIF.
- le Louvre LCP est désormais un `<img src="...960.avif">` direct dans le HTML ;
- plus de sélection `<picture>/<srcset>` pour cette ressource critique ;
- preload exact de la même URL ;
- Détail technique et contexte : [`historique/V122.md`](historique/V122.md)

## V121 — 2026-10-10 09:22 — Performance mobile du miroir français

- `/francais/`
- `/francais/en/`
- `/francais/fr/`
- CSS complet inline sur les homes, même méthode que la V116 gagnante de la home principale ;
- variantes responsive AVIF/WebP du Louvre (480/720/960 px) ;
- Détail technique et contexte : [`historique/V121.md`](historique/V121.md)

## V120 — 2026-10-10 09:11 — optimisation image mobile (homepage)

- nouvelles versions plus légères du panneau hero mobile :
- `hero-signboard-v120-400.{avif,webp}`
- `hero-signboard-v120-560.{avif,webp}`
- `hero-signboard-v120-640.{avif,webp}`
- `sizes` réaliste au lieu de `100vw` partout ;
- Détail technique et contexte : [`historique/V120.md`](historique/V120.md)

## V119 — 2026-10-10 09:08 — Footer mobile + accessibilité agentique

- le lien `.footer-signature` reçoit un `aria-label` explicite ;
- l'image de mascotte interne n'est plus chargée en priorité haute.
- badges de validation W3C masqués ;
- grande signature graphique du footer masquée.
- ces éléments sont décoratifs / techniques, pas nécessaires à la navigation ;
- Détail technique et contexte : [`historique/V119.md`](historique/V119.md)

## V118 — 2026-10-10 08:58 — Accessibilité / Navigation agentique

- le hero desktop avait `aria-hidden="true"` sur son conteneur ;
- ce conteneur contient pourtant plusieurs liens cliquables ;
- ces liens avaient eux-mêmes `aria-hidden="true"` et `tabindex="-1"`.
- suppression de `aria-hidden` sur le conteneur desktop ;
- suppression de `aria-hidden` et `tabindex=-1` sur les hotspots ;
- Détail technique et contexte : [`historique/V118.md`](historique/V118.md)

## V117 — 2026-10-10 08:53 — LCP mobile ciblé

- srcset plafonné à 720 px au lieu de 960 px ;
- nouvelle variante 640 px ;
- vrai fallback WebP au lieu du GIF transparent ;
- preload mobile unique et cohérent avec l'image réellement affichée ;
- decoding="sync" sur l'image LCP ;
- Détail technique et contexte : [`historique/V117.md`](historique/V117.md)

## V116 — 2026-10-10 08:48 — CSS complet inline sur la home

- V114 chargeait seulement un CSS critique incomplet, puis appliquait style.css après le premier rendu.
- V116 injecte directement le CSS COMPLET de la home dans le HTML.
- aucune requête render-blocking vers /css/style.css sur la page d'accueil ;
- aucun changement de mise en page quand le CSS "final" arrive, puisqu'il est déjà présent ;
- conservation des optimisations V112/V113 sur les images responsive/AVIF.
- Détail technique et contexte : [`historique/V116.md`](historique/V116.md)

## V115 — 2026-10-10 08:45 — Rollback V114

- Restaure la page d'accueil dans l'état V113 afin d'annuler le Critical CSS de V114, qui a dégradé le CLS et le LCP mobile.
- Détail technique et contexte : [`historique/V115.md`](historique/V115.md)

## V114 — 2026-10-10 08:38 — Critical CSS / Hero mobile

- CSS critique du switcher, header et hero directement inline dans le <head>.
- La grosse feuille style.css devient non bloquante (`media=print` + onload).
- Fallback <noscript> conservé.
- Les préconnexions Google Fonts sont supprimées du chemin critique.
- Les polices restent chargées de façon asynchrone comme en V113.
- Détail technique et contexte : [`historique/V114.md`](historique/V114.md)

## V113 — 2026-10-10 08:30 — LCP mobile / objectif 90+

- variantes AVIF du hero/panneau en complément du WebP ;
- preload LCP en AVIF, conditionné desktop/mobile ;
- fallback WebP conservé pour compatibilité ;
- Google Fonts n'est plus préchargé en priorité haute : la feuille de police devient non bloquante ;
- cache-busting des assets critiques en ?v=113.
- Détail technique et contexte : [`historique/V113.md`](historique/V113.md)

## V112 — 2026-10-10 08:12 — Performance mobile

- Le hero desktop ne se télécharge plus sur mobile.
- Le panneau mobile ne se télécharge plus sur desktop.
- Le panneau mobile utilise des variantes 480 / 720 / 960 px.
- Le hero desktop utilise 1280 / 1600 px.
- Le preload LCP est conditionné au viewport.
- Détail technique et contexte : [`historique/V112.md`](historique/V112.md)

## V111 — 2026-10-10 08:05 — SEO Homepage + Performance

- cohérence de la requête « apprendre l'albanais » dans title, description et headings ;
- contenu éditorial visible supplémentaire + FAQ utile ;
- liens cliquables sans texte dotés d'un libellé accessible ;
- URLs des hubs remplacées par leurs formes /dossier/ lorsqu'elles existent déjà ;
- scripts locaux chargés avec `defer` ;
- Détail technique et contexte : [`historique/V111.md`](historique/V111.md)

## V110 — 2026-10-09 22:29 — V110

- Patch V110 – suppression des derniers ajouts de mascottes Léka sur le miroir français. Ce patch retire l'injection JS restante et le CSS associé pour éviter toute apparition involontaire sur les pages.
- Détail technique et contexte : [`historique/V110.md`](historique/V110.md)

## V109 — 2026-10-09 22:25 — V109

- V109 — retrait des mascottes ajoutées sur le miroir français.
- Détail technique et contexte : [`historique/V109.md`](historique/V109.md)

## V108 — 2026-10-09 22:23 — V108

- accueil : carte Vivre & voyager ;
- Découvrir : carte Paris ;
- Culture : carte Fêtes de l'année ;
- Musique : première carte Chanson & cabaret (XXe siècle) ;
- Vidéothèque : première carte Alphabet & prononciation ;
- Détail technique et contexte : [`historique/V108.md`](historique/V108.md)

## V107 — 2026-10-09 22:19 — V107

- Patch V107 – Miroir français : placements de mascottes alignés sur la logique du site Albanie.
- Détail technique et contexte : [`historique/V107.md`](historique/V107.md)

## V106 — 2026-10-09 22:13 — Panneau miroir français

- Frëngjisht hap pas hapi
- Kulturë franceze
- Misione të drejtuara
- Histori & lexim
- Détail technique et contexte : [`historique/V106.md`](historique/V106.md)

## V105 — 2026-10-09 22:10 — Accueil Français miroir visuel

- hero plein écran inspiré de l’accueil principal ;
- arrière-plan Louvre/Paris conservé pour l’identité française ;
- grand titre éditorial en albanais ;
- Léka recentré au cœur du visuel ;
- panneau en bois recréé en HTML/CSS avec les rubriques Français, Culture, Missions et Histoire ;
- Détail technique et contexte : [`historique/V105.md`](historique/V105.md)

## V104 — 2026-10-09 21:30 — Festivals sur la page Musique albanaise

- ajout d'une section « L'Albanie en concert » ;
- ajout de trois rendez-vous : Colour Day Festival à Tirana, Himara International Music Festival et Korça Beer Fest ;
- ajout de visuels et de textes de contexte pour chaque festival ;
- adaptation de l'introduction et des statistiques du hero pour prendre en compte les festivals ;
- enrichissement du maillage vers les activités d'apprentissage liées à la musique.
- Détail technique et contexte : [`historique/V104.md`](historique/V104.md)

## V103 — 2026-10-09 21:20 — correction des vignettes musique

- Suppression des iframes YouTube intégrées qui affichaient l'erreur 153.
- Remplacement par deux **cartes vidéo cliquables** avec vignette, overlay, bouton play et CTA "Regarder sur YouTube".
- Vidéos corrigées : **Iso-polyphony** et **Alban Skënderaj · Unë dhe Ti**.
- Nettoyage des visuels **Lahuta**, **Çifteli**, **Klarinetë** et **Def** pour supprimer le texte parasite en haut des images.
- Ajustement du cadrage des vignettes d'instruments pour un rendu plus propre et homogène.
- Détail technique et contexte : [`historique/V103.md`](historique/V103.md)

## V102 — 2026-10-09 21:15 — vidéothèque : carte Alphabet

- Suppression du placement de la mascotte popcorn sur la première carte générique de la vidéothèque.
- Léka version **pointing** est désormais placée sur la carte **Alphabet & prononciation — Débutant / Albanian Alphabet — Alfabeti në shqip**.
- Placement sur le côté gauche de la carte, avec adaptation responsive.
- Cache busting mis à jour : `style.css?v=102` et `carnets-de-leka.js?v=102`.
- Détail technique et contexte : [`historique/V102.md`](historique/V102.md)

## V101 — 2026-10-09 21:02 — placements ciblés + corrections musique

- Accueil : Léka est placée sur la carte **Travel / Vivre & voyager** de la section Missions en Albanie.
- Découvrir l’Albanie : Léka est déplacée plus bas dans la page, sur la carte **Berat — la ville aux mille fenêtres**, avec une taille réduite.
- Culture & traditions : Léka est placée **de côté** sur la carte **Musique & chants**.
- Musique albanaise : la mascotte reste sur la carte **XXe siècle — La chanson devient scène**.
- Correction des vignettes **Alban Skënderaj** et **Aurela Gaçe** pour éviter les aperçus gris cassés de YouTube.
- Détail technique et contexte : [`historique/V101.md`](historique/V101.md)

## V100 — 2026-10-09 20:37 — ajustements mascotte + chronologie musique

- Accueil : Léka est déplacée à droite sur l’image de la section « Une langue, des paysages, des sons, des visages ».
- Hub Découvrir : Léka est placée sur la carte « Villes & régions » (image de Berat) au lieu de « Musique albanaise ».
- Pages Découvrir : lorsqu’une carte contenant « Berat » est présente, Léka se place au-dessus de cette image.
- Page « Musique albanaise » : Léka se place sur la carte « XXe siècle / La chanson devient scène ».
- La section « Voyage à travers les époques » passe en grille desktop de 4 colonnes.
- Détail technique et contexte : [`historique/V100.md`](historique/V100.md)

## V99 — 2026-10-09 20:27 — Accueil sur un seul écran

- Le hero V92 utilise désormais exactement la hauteur disponible sous le sélecteur de langue et le header.
- Calcul dynamique en JavaScript à partir des hauteurs réelles du header.
- L’illustration garde son ratio 1672×853 et n’est pas recadrée.
- Les hotspots restent alignés avec l’image.
- Recalcul au redimensionnement, changement d’orientation et changement de hauteur du header.
- Détail technique et contexte : [`historique/V099.md`](historique/V099.md)

## V98 — 2026-10-09 20:24 — Intro Coin lecture plus compacte

- Réduction de la hauteur du hero d’introduction.
- Desktop : environ 82svh avec bornes min/max.
- Ajustements tablette et mobile.
- Espacements verticaux resserrés.
- Zone du carrousel légèrement compactée.
- Détail technique et contexte : [`historique/V098.md`](historique/V098.md)

## V97 — 2026-10-08 21:54 — Ajustements d’intégration lecture

- `lecture/styles/home.css`
- le header du Coin lecture réserve désormais un espace visuel pour la mascotte ;
- la navigation du haut est rendue plus lisible avec un fond pill semi-transparent + blur ;
- sur mobile, le menu se replie proprement et ne passe plus sous la mascotte ;
- la mascotte `hero__leka` est repositionnée plus bas, sous la zone de navigation ;
- Détail technique et contexte : [`historique/V097.md`](historique/V097.md)

## V96 — 2026-10-08 21:44 — Mascottes calées sur les maquettes

- Léka est placée au-dessus des cartes, les mains posées visuellement sur le bord supérieur.
- Suppression de l’espace artificiel ajouté en V95 autour des grilles.
- Sur le hub Découvrir, la mascotte se pose sur « Musique albanaise », première carte de la seconde rangée, comme dans la composition de référence.
- Ciblage déterministe et non aléatoire.
- Taille responsive desktop / tablette / mobile.
- Détail technique et contexte : [`historique/V096.md`](historique/V096.md)

## V95 — 2026-10-08 21:35 — LEKA V95

- Léka est de nouveau positionnée **au-dessus** des cartes, pas à l'intérieur.
- L'espace vertical est réservé sur le conteneur de grille (`.leka-cameo-lane`) pour éviter chevauchements et débordements de viewport.
- Le positionnement des variantes de Léka est centré et responsive, avec réduction sur mobile.
- Les portraits des artistes albanais utilisent désormais des **vignettes de vidéos YouTube officielles / vérifiées** lorsqu'une vidéo fiable a été identifiée, avec fallback HQ puis image locale.
- Les cartes artistes utilisent un cadrage 16:10 `object-fit: cover` pour rendre les visages plus lisibles.
- Détail technique et contexte : [`historique/V095.md`](historique/V095.md)

## V94 — 2026-10-08 21:26 — UI polish

- Mascotte Léka : intégration contenue dans les cartes, sans débordement horizontal/vertical.
- Mascotte Léka : taille et position responsive, visible aussi sur mobile à une échelle réduite.
- Musique albanaise : zone portrait des artistes agrandie et images affichées sans recadrage agressif.
- Coin lecture : ajout d'un Léka lecteur discret sur les accueils FR, EN et SQ.
- Cache : passage des assets partagés `style.css` et `carnets-de-leka.js` en `v=94`.
- Détail technique et contexte : [`historique/V094.md`](historique/V094.md)

## V93 — 2026-10-08 21:06 — Première base conservée

- point de départ technique de l'historique reconstructible ;
- présence des principaux silos d'apprentissage et de découverte ;
- base utilisée pour comparer les évolutions suivantes ;
- aucune correction antérieure n'est attribuée à cette version sans preuve dans le code conservé.
- Détail technique et contexte : [`historique/V093.md`](historique/V093.md)
