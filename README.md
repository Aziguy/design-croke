# Handoff : CROKÉ — PWA (+ Cookies Fruités — PWA)

## Overview

Deux PWA e-commerce mobile-first, en français, pour deux marques artisanales :

1. **CROKÉ — croquettes snack** (livrable principal) : vente de croquettes de blé frites au volume, 4 saveurs × 4 formats, plus packs mix & match, abonnement, fidélité, pages légales et un back-office complet (commandes, produits, éditeur de contenu du front, thème, promos, clients, réglages).
2. **Cookies Fruités** (livrable antérieur, inclus pour référence) : vente de cookies aux fruits, même architecture de parcours, palette rose poudré / crème / noir.

Les deux sont conçues comme des **PWA installables** (pas d'app native) : viewport 390 × 844 px, cibles tactiles ≥ 44 px, barre d'onglets fixe en bas, contenu scrollable entre en-tête et barre d'onglets.

## About the Design Files

Les fichiers `.dc.html` de ce bundle sont des **références de design réalisées en HTML** — des prototypes montrant l'apparence et le comportement attendus, **pas du code de production à copier tel quel**.

La tâche consiste à **recréer ces designs dans l'environnement existant du codebase cible** (React, Vue, Svelte, Next.js…) avec ses patterns et ses bibliothèques établis. Si aucun environnement n'existe encore, choisissez le framework le plus adapté (recommandation : **Next.js + React + TypeScript**, styles au choix de l'équipe) et implémentez-y les écrans.

Les prototypes utilisent un petit runtime maison (`support.js`, balises `<sc-for>`, `<sc-if>`, `{{ hole }}`, styles inline) : **ce runtime n'a pas à être porté**. Il faut lire ces fichiers comme une spécification visuelle et comportementale. Ouvrez-les dans un navigateur (`CROKÉ - PWA.dc.html`) pour voir le rendu et cliquer dans le parcours — la barre de puces en haut permet de sauter à n'importe quel écran.

## Fidelity

**Haute fidélité (hifi).** Couleurs, typographies, espacements, rayons et micro-interactions sont définitifs. L'UI doit être recréée **au pixel près**, en utilisant les composants et utilitaires du codebase cible.

Deux réserves :
- Les **textes légaux** (CGV, mentions, confidentialité, livraison) contiennent des champs `[à compléter]` — à faire valider par le client avant mise en ligne.
- Les **données** (commandes, clients, avis, KPI, adresses, promos) sont fictives et doivent venir de l'API.

---

## Design Tokens — CROKÉ

### Couleurs

| Token | Hex | Usage |
| --- | --- | --- |
| `ink` | `#3B2415` | Texte principal, boutons primaires, blocs sombres |
| `cream` | `#F7EAD2` | Texte sur fond sombre, surface claire sur `ink` |
| `sand` | `#FBF4E7` | Fond de l'écran (canvas du téléphone) |
| `tan` | `#EFE6D0` | Surfaces secondaires, encarts, chips sélectionnés clairs |
| `accent` (défaut) | `#E0761A` | Accent produit — **modifiable dans le back-office** |
| `gold` | `#F7B321` | Bannière d'accueil, bouton secondaire sur fond sombre |
| `gold-deep` | `#EE9C12` | Bas du dégradé de bannière |
| `surface` | `#FFFFFF` | Cartes |
| `border` | `rgba(59,36,21,.07)` | Bord de carte standard |
| `border-strong` | `rgba(59,36,21,.12)` | Bord de contrôle / chip inactif |
| `text-muted` | `rgba(59,36,21,.5)` | Texte secondaire |
| `text-faint` | `rgba(59,36,21,.45)` / `.4` | Légendes, labels |
| Fond hors-cadre | `radial-gradient(1100px 560px at 50% -10%, #3A2416 0%, #241610 62%)` | Bureau autour du mockup (ne pas porter en prod) |

**Palette d'accents proposée dans le back-office** (thème) : `#E0761A` (orange, défaut), `#B8474C` (framboise), `#5C9450` (vert Croké), `#C2410C` (brique), `#8B4A22` (cacao), `#D9A21B` (or).

**Teintes de saveur** (fond des vignettes rondes) :

| Saveur | Teinte fond | Accent saveur |
| --- | --- | --- |
| Cacao | `#EFE0D2` | `#8B4A22` |
| Nature | `#EFEBD5` | `#6F7A2E` |
| Noix de coco | `#F1EADD` | `#9C8757` |
| Orange | `#FAE8D2` | `#D06A12` |

**Couleurs de statut** (pastille fond / texte) :

| Statut | Fond | Texte |
| --- | --- | --- |
| Nouvelle | `#FAE8D2` | `#D06A12` |
| À la friture | `#EFE6D0` | `#B26312` |
| À emballer | `#F3EBD6` | `#8A6A22` |
| Prête | `#E4EDE4` | `#41703F` |
| En livraison | `#E7EAF3` | `#3E4F87` |
| Livrée / Devis validé | `#E9EDE2` | `#5C7146` |
| Expiré (promo) | `#EDEAE4` | `rgba(59,36,21,.5)` |
| Destructif (rembourser) | texte `#B03A2E`, bord `rgba(176,58,46,.3)` |

### Typographie

Trois familles Google Fonts :

- **Baloo 2** (500/600/700/800) — titres, chiffres KPI, prix en gros. Rondeur qui répond au logo.
- **Nunito Sans** (300/400/600/700) — interface, copy, labels, boutons.
- **Caveat** (600) — uniquement la signature « Le plaisir de croquer. » (`#5C9450`).

Échelle utilisée (taille / graisse / interlignage / famille) :

| Rôle | Valeur |
| --- | --- |
| Titre de bannière | `700 25px/1.1 Baloo 2` |
| Titre d'écran (header) | `700 18px/1.05 Baloo 2` |
| Sur-titre de section | `700 21px/1 Baloo 2` (accueil), `700 16–19px/1 Baloo 2` (sous-sections) |
| Titre fiche produit | `700 26px/1.1 Baloo 2` |
| Chiffre KPI | `700 23–24px/1 Baloo 2` |
| Sous-titre header | `600 9px/1.2 Nunito Sans`, `letter-spacing:.22em`, uppercase |
| Kicker / eyebrow | `600 9px/1 Nunito Sans`, `letter-spacing:.26em`, uppercase |
| Corps de texte | `400 13.5px/1.65–1.7 Nunito Sans` |
| Corps secondaire | `300 11–12.5px/1.4–1.65 Nunito Sans` |
| Label de carte / ligne | `700 12.5–13px/1.2 Nunito Sans` |
| Bouton primaire | `700 13–14px/1 Nunito Sans` |
| Chip / filtre | `600 11–12px/1 Nunito Sans` |
| Badge statut | `600 10–10.5px/1 Nunito Sans` |
| Prix en ligne | `700 12–13px/1 Nunito Sans` |

`text-wrap: pretty` sur les paragraphes longs (descriptions produit, blocs légaux, marque).

### Espacement, rayons, ombres

- **Gouttière d'écran** : `16px` (listes, cartes), `20px` (blocs de texte long : fiche produit, marque, documents légaux).
- **Gaps** : `7–9px` (chips, boutons côte à côte), `10px` (lignes de liste), `12–14px` (cartes), `18–22px` (entre sections).
- **Rayons** : `999px` (pills, boutons, toggles, avatars), `26px` (héros / bannière / grande image produit), `20–24px` (cartes principales, encarts), `18px` (cartes de liste, blocs légaux), `16px` (champs, petits blocs), `14px` (chips de format), `12px` (badges de prix admin), `50%` (vignettes de saveur).
- **Ombres** : bannière d'accueil `0 14px 30px -12px rgba(59,36,21,.4)` ; visuel produit `0 14px 26px rgba(59,36,21,.22)` ; toast `0 12px 30px rgba(0,0,0,.28)`. Pas d'ombre sur les cartes courantes — elles s'appuient sur `1px solid rgba(59,36,21,.07)`.
- **Barre d'onglets** : fond `rgba(251,244,231,.94)`, `backdrop-filter: blur(8px)`, bord haut `1px solid rgba(59,36,21,.08)`, padding `10px 12px 22px` (les 22px du bas absorbent la safe-area iOS).

### Animations

- `rise` : `opacity 0→1`, `translateY(10px)→0`, `.35s ease both` (`.4s` sur l'accueil) — appliquée à chaque changement d'écran.
- `toastIn` : `opacity 0→1`, `translate(-50%,14px)→(-50%,0)`, `.25s ease both`.
- Toast : affiché 1700 ms puis disparaît. Position `bottom:96px`, centré, fond `ink`, texte `cream`, pill.
- Hover boutons : assombrissement de l'accent ou passage du bord à une valeur plus contrastée. Pas de transition longue ; le prototype s'appuie sur les états CSS natifs.

---

## Structure de l'application — CROKÉ

Shell commun à tous les écrans :

1. **Status bar factice** (46px) — à ne PAS porter : c'est le mockup. En PWA réelle, `viewport-fit=cover` + safe-area.
2. **En-tête** (`padding: 6px 18px 12px`) — bouton retour circulaire 34px (conditionnel), titre `Baloo 2 18px` + sous-titre uppercase, bouton panier 38px à droite avec pastille de compte (min 18px, fond `accent`).
3. **Zone scrollable** (`flex:1; overflow-y:auto`, scrollbar masquée) — remise à `scrollTop = 0` à chaque navigation.
4. **Toast** (conditionnel, absolu).
5. **Barre d'onglets** — 5 onglets : Accueil, Boutique, Panier, Compte, **••• Plus**.

### Mapping onglet → écrans actifs

| Onglet | Écrans qui allument l'onglet |
| --- | --- |
| Accueil | `home` |
| Boutique | `shop`, `product`, `pack` |
| Panier | `cart`, `checkout` |
| Compte | `account`, `track`, `sub` |
| ••• Plus | `more`, `doc`, `faq`, `contact`, `cookies`, `reviews`, `brand`, + tous les écrans admin |

Icônes d'onglet : carré 20px, bord 1.5px, rayons respectifs `30%`, `50%`, `0 0 8px 8px`, `50%`, `3px`. Actif = bord et remplissage à la couleur d'accent, label à l'accent ; inactif = `rgba(59,36,21,.42)`, remplissage transparent.

### Logique de retour (bouton ‹)

```
product                        → shop
doc | faq | contact | cookies  → more
adminOrder                     → adminOrders
adminProduct                   → adminProducts
admin                          → more
autre écran admin              → admin
défaut                         → home
```

---

## Écrans côté client

### 1. Accueil (`home`)

Objectif : convertir en une vue — promesse, saveurs, formats, preuve sociale.

- **Bannière** : carte `border-radius:26px`, image de fond 168px (`background-size:cover`, position `center 52%`) puis bloc `linear-gradient(180deg,#F7B321,#EE9C12)` en `padding:16px 20px 20px`. Titre (éditable back-office), sous-titre, deux boutons côte à côte `gap:9px` : « Commander » (fond `ink`, texte `cream`) et « Pack découverte » (bord 1.5px `ink`, fond `rgba(255,255,255,.35)`), tous deux `min-height:46px`, `border-radius:999px`.
- **Bandeau promesses** (section masquable) : 3 colonnes égales, `gap:8px`, carte blanche `border-radius:16px`, chiffre en `Baloo 2 14px` couleur accent + légende `300 9.5px`.
  Contenu : « Frit du jour / Jamais de stock de la veille » · « 0 conservateur / Croquant 3 semaines » · « Dès 1,50 € / 4 formats, du sachet au bidon ».
- **Nos 4 saveurs** : titre + lien « Tout voir → », carrousel horizontal `gap:12px`, cartes 142px ; vignette 142px `border-radius:22px` à la teinte de la saveur, image ronde `background-size:contain` centrée, `padding:10px` ; nom `700 14px`, mention « dès 1,50 € ».
- **Les formats** (section masquable) : bloc `ink` `border-radius:22px`, grille 2 × 2 `gap:9px`, chaque tuile `rgba(247,234,210,.08)` + bord `rgba(247,234,210,.14)` : label `Baloo 2 17px cream`, prix `700 12.5px #F7B321`, note `300 10px`. Clic → boutique.
- **Encart abonnement** (masquable) : fond `tan`, bord `rgba(224,118,26,.2)`, kicker accent, titre « Le bidon du mois, −15 % », flèche ronde 40px `ink`.
- **Avis** (masquable) : carte blanche, note « 4,8 ★ · 164 avis » cliquable, citation en italique, auteur.
- **Teaser marque** (masquable) : carte `1px dashed rgba(59,36,21,.22)`, logo rond 50px, deux lignes.

### 2. Boutique (`shop`)

- **Filtres** : rangée scrollable de pills — `Tous`, `Cacao`, `Nature`, `Noix de coco`, `Orange`, `Packs`. `Packs` navigue vers l'écran pack au lieu de filtrer. Actif = fond `ink` / texte `cream`.
- **Cartes saveur** empilées `gap:12px`, `border-radius:24px`, blanches :
  - Ligne haute : vignette ronde 86px (teinte saveur, image `contain`, `padding:5px`) + nom `700 15px` + badge de saveur (fond teinte, texte accent saveur, `700 8.5px` uppercase `letter-spacing:.1em`) + pitch + note « 4,9 ★ · 71 avis ».
  - Ligne basse : **4 boutons de format** en flex égal, `min-height:52px`, `border-radius:14px`, fond `sand`, bord `rgba(59,36,21,.12)`. Label format + prix accent. Clic = ajout direct au panier + toast « Cacao 250 ml ajouté ». Hover : bord accent, fond blanc.

### 3. Fiche produit (`product`)

- Visuel : bloc 270px teinte saveur, `border-radius:26px`, image ronde 226px avec ombre portée.
- Titre `Baloo 2 26px`, note uppercase accent, description `400 13.5px/1.65`.
- **Choix du format** : grille 2 × 2, boutons `min-height:74px`, bord 1.5px ; sélectionné = fond `ink`, texte `cream`, note `rgba(247,234,210,.6)`. La note affiche le prix au litre si l'option « prix au litre » du thème est active (ex. « Le format goûter · 10,00 €/L »).
- **Quantité + ajout** : stepper en pill blanche (− 30px bordé, valeur `700 14px`, + 30px `ink`) puis bouton plein accent `Ajouter · 5,00 €` (`flex:1`, `min-height:50px`).
- **Spécifications** : carte blanche, paires clé/valeur — Contenance, Poids net, Ingrédients, Conservation, Allergènes (le gluten toujours, fruits à coque pour la coco).
- **Les autres saveurs** : carrousel de vignettes 92px.

### 4. Composer un pack (`pack`)

Trois étapes visibles sur un seul écran.

1. **Le pack** — bloc `ink` : `Pack Découverte` (4 × 250 ml, 9 €) ou `Caisse Partage` (4 × 1 L, 32 €). Sélectionné = fond `cream`, texte `ink`. Changer de pack **réinitialise** la sélection de saveurs.
2. **Vos saveurs** — compteur `packCount/packSlots` en accent. 4 lignes avec stepper. Dépassement bloqué + toast « Pack complet (4) ».
3. **Le petit plus** — encart `tan`, 3 pills : Sachet refermable / Étiquette message / Emballage cadeau.

Bouton final : désactivé visuellement (`rgba(59,36,21,.35)`) tant que le compte n'est pas atteint, libellé « Choisissez encore 2 pot(s) » ; sinon fond accent, « Ajouter le pack · 9,00 € », puis toast + navigation vers le panier.

### 5. Panier (`cart`)

- Lignes : vignette ronde 52px, nom (`Cacao · 250 ml` ou `Pack Découverte · 250 ml ×4`), prix unitaire, stepper. Passer à 0 supprime la ligne.
- **Jauge de livraison offerte** : encart `tan`, message dynamique « Encore 11,00 € pour la livraison offerte » / « Livraison offerte, c'est acquis », barre 6px, remplissage accent, `width = min(100, sous-total/25 × 100)%`.
- **Totaux** : Sous-total · Livraison (ou « Retrait boutique ») · Créneau · Option, séparateur, Total en `Baloo 2 18px`.
- CTA `ink` pleine largeur « Commander · 14,00 € », hover accent.
- **État vide** : image ronde 84px à `opacity:.45`, « Panier vide, ça ne croque pas », « La friture du jour sort à 11h », bouton accent « Voir la boutique ».

### 6. Checkout (`checkout`) — 3 étapes

Indicateur : 3 barres 4px, remplies en accent jusqu'à l'étape courante.

- **Étape 1 — Livraison** : 3 modes en cartes sélectionnables (bord accent + fond `tan` si actif) — Livraison à domicile (2,90 €, offerte ≥ 25 €) · Retrait en boutique (gratuit) · Revendeur / événement (sur devis). Puis 4 créneaux en boutons `min-height:44px`. CTA « Continuer ».
- **Étape 2 — Coordonnées & paiement** : 4 champs en lecture (Nom, Téléphone, Adresse, Note au livreur) présentés en cartes label-uppercase + valeur ; puis 3 moyens de paiement (PayPal, Paiement à la livraison, Virement bancaire) en cartes sélectionnables. CTA accent « Payer 14,00 € » + mention « Paiement sécurisé · Annulation gratuite jusqu'à 9h le jour J ».
  ⚠️ En production ce sont de vrais inputs avec validation (téléphone FR, adresse dans la zone desservie, e-mail).
- **Étape 3 — Confirmation** : disque 84px `tan` avec ✓ accent, « C'est parti pour la friture ! », référence + créneau + mode·paiement, CTA « Suivre ma commande », encart points de fidélité (`total × 10`, arrondi).

### 7. Suivi (`track`)

Bandeau `ink` avec référence, statut courant en `Baloo 2 23px`, mode + créneau. Timeline verticale à 5 étapes : Commande reçue → Pâte en préparation → À la friture → En route → Livré. Pastille 14px (accent si franchie, blanche bordée sinon), trait 2px. Bouton de démo « Simuler l'étape suivante » (à remplacer par le websocket/polling réel). Encart WhatsApp en bas.

### 8. Compte & fidélité (`account`)

- **Carte de fidélité** : `linear-gradient(150deg,#F7B321,#E0761A)`, texte `ink`, nom + points (`700 26px`), barre de progression 6px (remplissage `ink` sur `rgba(59,36,21,.2)`), « 180 points avant le bidon 1 L offert ».
- Grille 2 × 2 de tuiles : Mon abonnement · Mes adresses · Parrainage · Vue production (raccourci admin).
- Liste des commandes avec pastille de statut, clic → suivi.

### 9. Abonnement (`sub`)

Trois formules en cartes sélectionnables (`ink` quand active) : Solo 7,60 €/mois (1 L) · Duo 15,30 €/mois (2 × 1 L) · Bureau 42 €/mois (6 × 1 L, facture pro). Chips d'avantages, CTA « S'abonner · 15,30 €/mois ».

### 10. Avis (`reviews`)

En-tête : note `Baloo 2 38px` + étoiles + histogramme 5 barres (5★ 88 %, 4★ 9 %, 3★ 2 %, 2★ 1 %, 1★ 0 %). Puis liste d'avis : auteur, étoiles, texte, « produit · date relative ».

### 11. La marque (`brand`)

Image flyer 190px, signature Caveat verte, titre, deux paragraphes, 4 engagements en cartes à puce accent, bandeau des 4 saveurs en ronds, encart `ink` « Revendeur, boutique, événement ? » avec CTA or.

### 12. ••• Plus (`more`)

Point d'entrée de tout ce qui ne tient pas dans 4 onglets.

- **Bandeau installation PWA** : bloc `ink`, « Installer Croké », bouton or. Doit brancher `beforeinstallprompt`.
- **4 groupes** de liens en cartes blanches (label + note + chevron, `min-height:48px`) :
  - *Commander & suivre* : Suivre ma commande · Mon compte · Club Croké · Avis clients
  - *Aide* : FAQ · Contact · Livraison & retours · La marque
  - *Informations légales* : CGV · Mentions légales · Politique de confidentialité · Préférences cookies
  - *Espace professionnel* : Devenir revendeur · Back-office
- Pied : « Croké — Croquettes snack · v1.0.0 » + SIRET/TVA à compléter.

### 13. Documents légaux (`doc`)

Un seul écran, quatre contenus (`cgv`, `mentions`, `confidentialite`, `livraison`). En-tête `tan` avec titre + date de mise à jour, chapô, blocs numérotés en cartes blanches (titre `700 12.5px` + paragraphe `300 12px/1.65`), puis rangée de pills pour passer d'un document à l'autre.

Contenus rédigés dans le prototype (droit français) :

- **CGV** — 10 articles : identité du vendeur, produits, prix (les 4 tarifs), commande, paiement, livraison et retrait, **absence de droit de rétractation sur les denrées périssables (art. L221-28 Code de la consommation)**, réclamations sous 48 h, abonnements sans engagement, données/litiges/médiation.
- **Mentions légales** — éditeur, contact, hébergement, propriété intellectuelle (marque, logo, signature, étiquettes), hygiène/étiquetage (déclaration DDPP), signalement.
- **Politique de confidentialité** — responsable de traitement, données collectées, finalités et bases légales, durées (compte 3 ans, factures 10 ans, cookies 13 mois), destinataires, droits RGPD + CNIL, sécurité.
- **Livraison & retours** — zones et délais, frais, retrait, commandes pro, produit non conforme, conservation.

Tous les champs entre crochets sont à renseigner par le client.

### 14. FAQ (`faq`)

Accordéon à ouverture unique (`faqOpen` = index, `-1` = tout fermé). En-tête cliquable `min-height:48px`, signe `+`/`−` (accent quand ouvert). 7 questions : fabrication, conservation, choix du format, allergènes, paiement à la livraison, zones de livraison, commandes événement. Encart de bascule vers Contact.

### 15. Contact (`contact`)

3 tuiles (WhatsApp / Courriel / Atelier), formulaire 4 champs (le champ Message fait `min-height:96px`), CTA `ink`, carte d'informations atelier (adresse à compléter, horaires, délai de réponse 24 h ouvrées).

### 16. Préférences cookies (`cookies`)

Chapô expliquant que tout est désactivé par défaut sauf le nécessaire. 4 lignes avec **toggle** :
- *Strictement nécessaires* — verrouillé (`cursor:not-allowed`, piste grise, toast d'explication au clic).
- *Mesure d'audience*, *Publicité*, *Personnalisation* — libres.

Toggle : piste 44 × 26px `border-radius:999px`, `padding:3px`, pastille 20px blanche, `justify-content: flex-end` quand actif ; piste = accent si actif, `rgba(59,36,21,.18)` sinon. **Ce composant est réutilisé partout dans l'admin — en faire un composant unique.**

Deux CTA : « Tout accepter » (plein `ink`) et « Enregistrer » (contour 1.5px).

---

## Écrans back-office

Tous les écrans admin partagent une **barre de sous-onglets** scrollable, insérée juste sous l'en-tête : Tableau de bord · Commandes · Produits · Contenu · Thème · Promos · Clients · Réglages. Actif = fond `ink`, texte `cream`. L'onglet Commandes reste actif sur le détail d'une commande ; idem Produits/édition produit.

### A1. Tableau de bord (`admin`)

Grille 2 × 2 de cartes KPI `ink` (label uppercase, valeur `Baloo 2 23px`, delta en or) : CA du jour 318 € (+12 %) · Commandes 41 (6 à préparer) · Panier moyen 7,80 € (+0,60 €) · Note 4,8 (164 avis).
Puis **Stock par saveur (en litres)** : 4 barres colorées à la couleur de la saveur (`18 L / 30`, etc.).
Puis **Commandes à traiter** : mêmes cartes que la liste, cliquables vers le détail.

### A2. Commandes (`adminOrders`)

Filtres de statut en pills (Toutes / Nouvelle / À la friture / À emballer / Livrée) appliqués sur le statut **courant** (donc réactifs aux changements faits dans le détail). Cartes de commande : référence · client, total, détail, pastille de statut, créneau, et « Ouvrir › » en accent aligné à droite.

### A3. Détail commande (`adminOrder`)

- Bandeau `ink` : référence en `Baloo 2 20px`, total, puis client · téléphone / adresse / créneau · moyen de paiement.
- **Contenu de la commande** : lignes libellé → montant (incluant livraison et total TTC ; pour le paiement à la livraison, « Total à encaisser »).
- **Statut** : 6 pills — Nouvelle, À la friture, À emballer, Prête, En livraison, Livrée. Le clic met à jour l'état et déclenche un toast `#CK-1042 → Prête`.
- **Note interne** en encart `tan`.
- 3 actions : Imprimer l'étiquette · Appeler le client · Rembourser (style destructif).

### A4. Produits (`adminProducts`)

Bouton « + Ajouter un produit » en carte pointillée. Puis une carte par saveur : vignette ronde 46px, nom, « 1,50 € – 9,00 € · en stock / masqué du site », **toggle de publication** (masquer retire le produit du front), rangée de chips (4 formats, badge, Publié/Brouillon, niveau de stock) et bouton « Éditer ».

### A5. Éditer un produit (`adminProduct`)

- Bloc visuel : rond 72px + explication du format attendu (PNG carré, 1200 px min) + bouton « Remplacer » (drop d'image à implémenter).
- 7 champs : Nom, Accroche courte, Description, Catégorie, Ingrédients / allergènes, Slug (`/produits/croke-cacao`), Titre SEO.
- **Prix et stock par format** : une ligne par format avec prix et stock éditables (`48 u.`, `12 u.`).
- 3 interrupteurs : Mis en avant sur l'accueil · Badge « Nouveau » · Réservé aux pros.
- CTA « Enregistrer » (accent, `flex:2`) + « Archiver » (contour, `flex:1`).

### A6. Contenu du site (`adminContent`) — l'éditeur du front

- **Bandeau d'état** `tan` : « Page d'accueil — Publiée · dernière mise à jour aujourd'hui » ou « Brouillon non publié — 1 modification en attente », bouton « Publier ». Toute modification de copy ou de section repasse l'état en brouillon.
- **Textes de la bannière** : 3 champs (Titre, Sous-titre, Bouton principal) affichant la valeur courante, un compteur de caractères, et **2 variantes proposées en pills** — le clic applique la variante et se répercute immédiatement sur l'accueil. En production, remplacer par un champ libre + compteur, en gardant les variantes comme suggestions.
- **Sections affichées** : 5 lignes avec poignée de réordonnancement (3 traits) et toggle — Bandeau promesses · Bloc « Les formats » · Encart abonnement · Avis mis en avant · Teaser marque. Le toggle masque réellement la section de l'accueil. Le drag-and-drop est à implémenter (la poignée est dessinée, pas fonctionnelle).
- **Pages légales** : 4 lignes vers l'éditeur du document, avec état « Publié » / « À compléter » (les Mentions légales sont marquées à compléter).

### A7. Thème (`adminTheme`)

- **Aperçu live** : encart dont le fond suit la bannière choisie, avec le titre et les CTA réels — il reflète les valeurs en cours.
- **Couleur d'accent** : 6 pastilles rondes 46px, bord 3px `ink` sur la sélection. Le choix se propage instantanément à toute l'app (pastille panier, CTA, jauges, timeline, onglets actifs, toggles).
- **Bannière d'accueil** : 3 vignettes (crème / jaune / cacao) avec aperçu 52px et bord 2px sur la sélection.
- **Réglages d'affichage** : Afficher le prix au litre (ajoute « 10,00 €/L » sous les formats de la fiche produit) · Badges de saveur · Alerte stock faible.
- CTA « Appliquer au site ».

### A8. Codes promo (`adminPromos`)

Bouton de création + 4 cartes : code en `700 13px letter-spacing:.08em`, pastille d'état (Actif / Programmé / Expiré), règle, « Utilisé 84 fois », « CA 612 € ».

### A9. Clients (`adminCustomers`)

3 KPI (Clients actifs 318 · Réachat 46 % · Panier moyen 7,80 €) puis liste : avatar initiales 38px sur `tan`, nom, « 12 commandes · 320 points · Montreuil », LTV alignée à droite avec segment (Club Duo / Fidèle / Pro / Nouveau).

### A10. Réglages (`adminSettings`)

- **Boutique** : horaires, zones livrées, frais (2,90 €), livraison offerte dès 25 €, capacité 60 L/jour, devise EUR et TVA 5,5 % (alimentaire).
- **Moyens de paiement et notifications** : 4 interrupteurs (PayPal, Paiement à la livraison, Virement, Notifications push).
- **Équipe** : 3 membres avec rôle (Admin / Livraison / Lecture).
- Deux actions : Exporter CSV · Journal d'activité.

---

## Catalogue & règles métier

### Formats (identiques pour les 4 saveurs)

| Format | Prix TTC | Prix au litre |
| --- | --- | --- |
| 150 ml | 1,50 € | 10,00 €/L |
| 250 ml | 2,50 € | 10,00 €/L |
| 350 ml | 3,50 € | 10,00 €/L |
| 1 L | 9,00 € | 9,00 €/L |

### Saveurs

| id | Nom | Badge | Pitch | Note |
| --- | --- | --- | --- | --- |
| `cacao` | Croké Cacao | Best-seller | Enrobage cacao amer, croquant franc | 4,9 (71) |
| `nature` | Croké Nature | Le classique | Juste le blé, le sucre et le sel | 4,8 (44) |
| `coco` | Croké Noix de coco | Doux | Coco râpée torréfiée, note lactée | 4,7 (33) |
| `orange` | Croké Orange | Vif | Zeste d'orange confit, acidulé | 4,7 (26) |

### Packs

| id | Nom | Composition | Prix | Prix séparé |
| --- | --- | --- | --- | --- |
| `p250` | Pack Découverte | 4 × 250 ml au choix | 9,00 € | 10,00 € |
| `p1000` | Caisse Partage | 4 × 1 L au choix | 32,00 € | 36,00 € |

### Règles

- **Livraison** : 2,90 €, offerte à partir de **25 €** de sous-total ; toujours gratuite en retrait.
- **Fidélité** : `points = round(total TTC × 10)`. Palier : bidon 1 L offert à 500 points.
- **Abonnement** : −15 % (−22 % formule Bureau), sans engagement, résiliation ≥ 5 jours avant renvoi.
- **Rétractation** : inapplicable (denrée alimentaire périssable) — le mentionner au checkout et dans les CGV.
- **Réclamation** : 48 h avec photo.
- **Devise** : EUR, format français (`14,00 €`, espace insécable avant `€`), TVA 5,5 %.
- **Typographie française** : espace fine insécable (`\u202F`, `&#8239;`) avant `?`, `!`, `:`, `;` et avant `€`. Déjà appliqué dans le prototype — à conserver.

---

## State Management

État du prototype, à répartir entre store client, URL et API :

| Clé | Type | Rôle | Destination en prod |
| --- | --- | --- | --- |
| `screen` | string | Écran courant | **Routeur** (une URL par écran) |
| `filter` | string | Filtre boutique | URL (query param) |
| `fid` | string | Saveur affichée | URL (`/produits/[slug]`) |
| `fmt` | string | Format sélectionné | État local de la fiche |
| `qty` | number | Quantité fiche produit | État local |
| `packId`, `pack` | string, map | Pack en cours de composition | Store panier (persisté) |
| `extra` | string | Option cadeau | Store panier |
| `cart` | map `"saveur\|format" → qty` (`"pack\|p250"` pour un pack) | Panier | Store persisté + serveur si connecté |
| `step` | 1‑3 | Étape checkout | URL ou machine à états |
| `mode`, `slot`, `pay` | string | Choix de livraison | Store checkout |
| `plan` | string | Formule d'abonnement | Store |
| `track` | 0‑4 | Étape de suivi | **API** (polling / websocket) |
| `toast` | string | Notification éphémère | Composant toast global |
| `doc`, `faqOpen` | string, number | Navigation contenu | URL / local |
| `orderFilter`, `orderRefSel`, `statuses` | — | Back-office commandes | **API** |
| `editId`, `avail`, `prodFlags` | — | Back-office produits | **API** |
| `theme` `{accent, banner, perLitre, badges, stockAlert}` | objet | Thème du site | **API réglages** — lu par le front public |
| `sections`, `copy`, `published` | — | Contenu éditorial de l'accueil | **API CMS** |
| `cookiePrefs` | objet | Consentement | `localStorage` + bandeau au 1er lancement |
| `settingFlags` | objet | Moyens de paiement actifs | **API réglages** |

**Point d'architecture important** : `theme`, `sections` et `copy` sont modifiés en back-office et **consommés par le front public**. Prévoyez un endpoint de configuration de site (`GET /api/site-config`) mis en cache côté client, plus un état brouillon/publié.

---

## Comportements à implémenter au-delà du prototype

1. **PWA** : manifeste (nom, icônes 192/512, `display: standalone`, `theme_color: #3B2415`, `background_color: #FBF4E7`), service worker (cache du shell + catalogue, file d'attente des commandes hors ligne), gestion de `beforeinstallprompt` derrière le bouton « Installer » de l'écran Plus.
2. **Formulaires réels** : les champs coordonnées et contact sont affichés en lecture dans le prototype. Prévoir inputs, masques (téléphone FR), validation, messages d'erreur, autocomplétion d'adresse et contrôle de zone desservie.
3. **Paiement** : intégration PayPal (redirection), génération d'IBAN/référence pour le virement, encaissement à la livraison géré côté livreur.
4. **Suivi temps réel** : remplacer le bouton « Simuler l'étape suivante » par du polling ou un websocket.
5. **Notifications** : push web pour les changements de statut (côté client) et les nouvelles commandes (côté admin).
6. **Auth & rôles** : Admin / Livraison / Lecture ; le back-office doit être derrière authentification, pas seulement derrière un onglet.
7. **Réordonnancement** des sections d'accueil (drag-and-drop) et **upload d'image** produit.
8. **Accessibilité** : les vignettes rondes sont des `div` avec `role="img"` + `aria-label` dans le prototype (contrainte du runtime) — en production, utiliser de vraies balises `<img>` avec `alt`. Vérifier les contrastes de l'accent choisi en back-office (imposer un ratio minimum sur les swatches). Focus visible sur tous les contrôles.
9. **Responsive** : le design est calé sur 390 px. Prévoir une montée en largeur propre jusqu'à 640 px (contenu centré, `max-width`), et éventuellement un back-office desktop (les écrans admin gagneraient une vue tableau au-delà de 768 px).
10. **i18n** : tout est en français. Externaliser les chaînes si un anglais est prévu.

---

## Assets

Dans `uploads/` :

| Fichier | Contenu | Usage |
| --- | --- | --- |
| `cacao.jpeg` | Étiquette ronde saveur cacao | Vignettes, fiche, panier |
| `nature.jpeg` | Étiquette ronde saveur nature | idem + logo du teaser marque |
| `noix-de-coco.jpeg` | Étiquette ronde saveur coco | idem |
| `orange.jpeg` | Étiquette ronde saveur orange | idem |
| `flyer_1.jpeg` | Flyer / logo sur fond crème | Écran marque, option de bannière « crème » |
| `flyer_2.jpeg` | Flyer sur fond jaune | Bannière d'accueil par défaut |
| `flyer_3.jpeg` | Flyer variante | Vignette des packs au panier |
| `pasted-1786862088526-0.png` | Photo de la fondatrice | **Cookies Fruités uniquement** |

Fournis par le client. Les étiquettes sont utilisées telles quelles, recadrées en cercle. **À demander au client** : des photos produit réelles (croquettes en pot, macro texture) et un logo vectoriel (SVG) pour les icônes PWA.

---

## Files

| Fichier | Contenu |
| --- | --- |
| `CROKÉ - PWA.dc.html` | **Prototype principal** — 26 écrans (client + back-office). Ouvrir dans un navigateur ; la barre de puces en haut permet de sauter à un écran. |
| `Cookies Fruités - PWA.dc.html` | Second prototype (cookies aux fruits) — 12 écrans, même architecture, palette rose/crème. Utile si les deux marques partagent une base de code. |
| `support.js` | Runtime des prototypes. **Ne pas porter** — présent uniquement pour que les fichiers HTML s'ouvrent hors ligne. |
| `uploads/` | Visuels sources. |
| `screenshots/` | **28 captures** — une par écran, dans l'ordre du parcours (voir table ci-dessous). Référence visuelle pour l'implémentation au pixel près. |

### Captures d'écran

| Fichier | Écran |
| --- | --- |
| `01-accueil.png` | Accueil |
| `02-boutique.png` | Boutique (4 saveurs × 4 formats) |
| `03-fiche-produit.png` | Fiche produit — Cacao |
| `04-composer-pack.png` | Composer un pack (3 étapes) |
| `05-panier.png` | Panier |
| `06-checkout-1-livraison.png` | Checkout étape 1 — mode et créneau |
| `07-checkout-2-paiement.png` | Checkout étape 2 — coordonnées et paiement |
| `08-checkout-3-confirmation.png` | Checkout étape 3 — confirmation |
| `09-suivi-commande.png` | Suivi de commande |
| `10-compte-fidelite.png` | Compte & fidélité |
| `11-abonnement.png` | Club Croké (abonnement) |
| `12-avis-clients.png` | Avis clients |
| `13-la-marque.png` | La marque |
| `14-plus-menu.png` | ••• Plus (menu secondaire) |
| `15-cgv.png` | Document légal — CGV |
| `16-faq.png` | FAQ |
| `17-contact.png` | Contact |
| `18-preferences-cookies.png` | Préférences cookies |
| `19-admin-tableau-de-bord.png` | Back-office — tableau de bord |
| `20-admin-commandes.png` | Back-office — commandes |
| `21-admin-detail-commande.png` | Back-office — détail commande |
| `22-admin-produits.png` | Back-office — produits |
| `23-admin-editer-produit.png` | Back-office — éditer un produit |
| `24-admin-contenu.png` | Back-office — contenu du site |
| `25-admin-theme.png` | Back-office — thème |
| `26-admin-promos.png` | Back-office — codes promo |
| `27-admin-clients.png` | Back-office — clients |
| `28-admin-reglages.png` | Back-office — réglages |

Les captures montrent la partie visible de l'écran ; le contenu sous la ligne de flottaison est décrit dans la section « Écrans » ci-dessus et visible en scrollant le prototype.

### Où lire quoi dans le prototype

Chaque écran est un bloc `<sc-if value="{{ isX }}">` contenant un `<div data-screen-label="…">` — cherchez `data-screen-label` pour naviguer dans le fichier. Toutes les données (catalogue, textes légaux, FAQ, commandes, palette) sont en tête de la classe `Component`, dans les constantes `FORMATS`, `FLAVORS`, `PACKS`, `DOCS`, `FAQS`, `ORDERS`, `STATUS_STYLE`.

---

## Note sur Cookies Fruités

Même squelette, tokens différents : `#221A16` (encre), `#FBF6F0` (crème), `#F6E2E2` (blush), `#B8474C` (framboise) ; typographies **Cormorant Garamond** (titres) et **Jost** (interface). Les visuels cookies y sont générés en CSS faute de photos — à remplacer par de vraies images. Les écrans « Plus », légaux et back-office étendu **n'ont pas encore été portés sur ce projet** : si les deux marques doivent converger, prendre CROKÉ comme référence d'architecture.
