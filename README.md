# Atelier Newsletters — Union pour l'Enfance

Outil de fabrication des lettres d'information de l'Union pour l'Enfance.
On empile des blocs, on les met dans l'ordre voulu, on copie le HTML obtenu dans Mailchimp.

**Ouvrir l'atelier :** https://upe-bot.github.io/atelier-newsletters/

L'accès est protégé par un mot de passe, communiqué par la Direction de la
Mobilisation et des Partenariats. Le contenu de la page est chiffré : sans le
mot de passe, il n'est pas lisible, même en affichant le code source.

## Ce que ça fait

- Quatre familles de lettres — **Veille**, **Interne**, **Externe**, **Établissement** —
  chacune avec son bandeau, ses couleurs et son motif, toutes dans la charte graphique
  et la charte design « La porte et l'abri ». On les distingue au premier coup d'œil.
- Dix-neuf blocs : en-tête, édito, sommaire, intitulé de rubrique, article, vidéo,
  album photo, indicateurs, chiffre clé, citation, bonus culturel, ressource,
  rendez-vous, formation, informations pratiques, offre d'emploi, sondage,
  participation, pied de page.
- Ajout, déplacement par glissé, duplication, suppression. Aucune limite de nombre de blocs.
- Aperçu ordinateur et téléphone en temps réel.
- Sortie : un fichier HTML autonome, compatible Gmail, Outlook, Apple Mail et iOS,
  avec le lien de désabonnement et les balises de personnalisation Mailchimp.

## Comment s'en servir

Le mode d'emploi complet est un document interne, diffusé par la Direction de la
Mobilisation et des Partenariats. Il n'est pas publié ici.

En résumé : choisir la famille, ajouter les blocs, remplir, relire l'aperçu téléphone,
copier le HTML, puis dans Mailchimp créer une campagne en **Codage personnalisé** et coller.

### La famille Établissement

Pensée pour qu'un établissement prépare lui-même un envoi, prêt à partir :
le nom de l'établissement et la commune s'affichent dans un bandeau jaune sous
le titre, et le numéro démarre avec son propre jeu de blocs — édito signé,
article, album photo, rendez-vous, informations pratiques.

Le bloc **En-tête** propose la liste des logos d'établissement, repris de
ceux publiés sur unionpourlenfance.com. Un champ permet aussi de coller
l'adresse d'un autre logo.

Les logos d'origine sont en vert UPE et ne se lisent pas sur l'en-tête vert.
Une version blanche sur fond transparent a donc été produite pour chacun et
déposée dans la médiathèque du site (`…/uploads/2026/10/<établissement>-blanc.png`) :
le logo s'affiche dans l'en-tête vert, à la place de celui de l'Union, qu'il porte déjà.

Un établissement dont la version blanche n'est pas renseignée (champs `ub`, `lb`,
`hb` d'une entrée de `LOGOS`) retombe sur un bandeau blanc au-dessus de l'en-tête,
avec son logo en couleur. C'est le cas d'Agapè Anjou, dont le seul fichier publié
est la version co-signée École de production, sur fond blanc opaque.

### Les images

L'atelier ne stocke pas les images : il demande leur adresse. Pour en obtenir une,
téléverser le fichier dans Mailchimp (**Contenu → Téléchargements → Télécharger**),
puis sur l'image **Afficher les détails → Copier l'URL**.

Attention : tout fichier déposé dans le studio Mailchimp est consultable par quiconque
a le lien. Ne pas y déposer de photo d'enfant sans les autorisations requises.

## La personnalisation

Les 26 balises de l'audience Mailchimp de l'UPE sont dans l'atelier, groupées
par thème (personne, contact, adresse, lien à l'Union, entreprise). On clique
dans un champ, puis sur la balise : elle se pose au curseur. Elles fonctionnent
dans n'importe quel champ, pas seulement la formule d'appel.

L'aperçu les remplace par des valeurs d'exemple et résout les conditions
`*|IF:FNAME|*Bonjour *|FNAME|*,*|ELSE:|*Bonjour,*|END:IF|*`, pour qu'on voie la
phrase finie. Le catalogue est l'objet `BALISES` du code source.

## Le contenu rédigé

Les textes se saisissent en clair. Trois conventions dans les champs longs :

| Ce qu'on tape | Ce que ça donne |
| --- | --- |
| une ligne vide | un nouveau paragraphe |
| `- texte` en début de ligne | une puce |
| `**texte**` | du gras |

## Sauvegarde et passage de relais

**Enregistrer** garde le numéro en cours dans le navigateur — propre à l'ordinateur
et au navigateur utilisés. GitHub Pages ne sert que des fichiers : il n'y a pas de
serveur pour partager quoi que ce soit, donc pas de sauvegarde commune de ce côté.

Pour passer un numéro à quelqu'un d'autre, le bloc **Transmettre ce numéro** produit
un code qui contient tout le numéro, compressé. On l'envoie par message, l'autre
personne le colle et reprend le travail là où il en était. Aucun compte, aucun serveur.

La version hébergée dans Claude a en plus une sauvegarde réellement commune : deux
personnes ouvrant la même page voient le même numéro.

## Charte appliquée

| Rôle | Couleur |
| --- | --- |
| Vert UPE — couleur principale | `#0A6F71` |
| Vert profond — fonds sombres | `#073A3B` |
| Jaune sable — signal | `#F7BE47` |
| Orange vif — accent ponctuel | `#F5A600` |
| Vert clair — texte secondaire sur sombre | `#A2D2D2` |
| Vert d'eau — fond de la famille Établissement | `#E4F0F0` |
| Encre — texte courant | `#12302F` |
| Gris-vert — légendes | `#5E7473` |

Typographie : **Poppins** pour tout le contenu, **Neucha** pour les citations.
Les messageries qui ne chargent pas les polices web basculent sur Century Gothic,
puis Helvetica ou Arial.

Corps 16 px interligne 28, titres d'article 24 px, intitulés 12 px.
Rien ne descend sous 12 px.

## Modifier l'atelier

`index.html` est la page de garde : elle contient l'atelier **chiffré** (AES-256-GCM,
clé dérivée du mot de passe par PBKDF2-SHA256, 310 000 itérations) et rien d'autre.
Le code source en clair n'est pas dans ce dépôt — il est conservé par la Direction de
la Mobilisation et des Partenariats, avec le script `chiffrer.mjs` qui reconstruit
`index.html` et permet de changer le mot de passe.

Dans ce code source :

- Les couleurs sont dans l'objet `P`, les quatre familles dans `FAMILLES`.
- Chaque bloc est une entrée de l'objet `B` : `nom`, `champs` (ce que l'utilisateur
  remplit), `resume` (ce qui s'affiche sur la carte repliée) et `rendu` (le HTML
  de l'e-mail). Pour ajouter un bloc, ajouter une entrée dans `B` et sa valeur de
  départ dans `DEFAUTS` — la palette se met à jour toute seule.
- `document_email()` assemble l'en-tête HTML, les blocs et le pied.

Les boutons des e-mails sont construits par bordures plutôt que par rembourrage :
c'est la seule technique qu'Outlook respecte sur un lien.

## Autres fichiers

- [`modeles/veille-modele-mailchimp.html`](modeles/) — l'ancien modèle Veille, à importer
  directement dans Mailchimp (Modèles → Codage personnalisé). Conservé comme repli.

---

Direction de la Mobilisation et des Partenariats
Union pour l'Enfance · 174 quai de Jemmapes, 75010 Paris
communication@unionpourlenfance.com
