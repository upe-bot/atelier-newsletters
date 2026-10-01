# Atelier Newsletters — Union pour l'Enfance

Outil de fabrication des lettres d'information de l'Union pour l'Enfance.
On empile des blocs, on les met dans l'ordre voulu, on copie le HTML obtenu dans Mailchimp.

**Ouvrir l'atelier :** https://upe-bot.github.io/atelier-newsletters/

Cette adresse ne répondra qu'une fois le dépôt rendu public et GitHub Pages activé
(Settings → Pages → *Deploy from a branch* → `main` / `/ (root)`).

## Ce que ça fait

- Trois familles de lettres — **Veille**, **Interne**, **Externe** — chacune avec son bandeau, ses couleurs et son motif, toutes dans la charte graphique 2025 et la charte design « La porte et l'abri ».
- Seize blocs : en-tête, édito, sommaire, intitulé de rubrique, article, vidéo, indicateurs, chiffre clé, citation, bonus culturel, ressource, rendez-vous, formation, sondage, participation, pied de page.
- Ajout, déplacement par glissé, duplication, suppression. Aucune limite de nombre de blocs.
- Aperçu ordinateur et téléphone en temps réel.
- Sortie : un fichier HTML autonome, compatible Gmail, Outlook, Apple Mail et iOS, avec le lien de désabonnement et les balises de personnalisation Mailchimp.

## Comment s'en servir

Le mode d'emploi complet est dans [`tuto/`](tuto/) — cinq pages, à imprimer ou à transmettre.

En résumé : choisir la famille, ajouter les blocs, remplir, relire l'aperçu téléphone,
copier le HTML, puis dans Mailchimp créer une campagne en **Codage personnalisé** et coller.

### Les images

L'atelier ne stocke pas les images : il demande leur adresse. Pour en obtenir une,
téléverser le fichier dans Mailchimp (**Contenu → Téléchargements → Télécharger**),
puis sur l'image **Afficher les détails → Copier l'URL**.

Attention : tout fichier déposé dans le studio Mailchimp est consultable par quiconque
a le lien. Ne pas y déposer de photo d'enfant sans les autorisations requises.

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
| Encre — texte courant | `#12302F` |
| Gris-vert — légendes | `#5E7473` |

Typographie : **Poppins** pour tout le contenu, **Neucha** pour les citations.
Les messageries qui ne chargent pas les polices web basculent sur Century Gothic,
puis Helvetica ou Arial.

Corps 16 px interligne 28, titres d'article 24 px, intitulés 12 px.
Rien ne descend sous 12 px.

## Modifier l'atelier

Tout tient dans [`index.html`](index.html), sans dépendance ni étape de construction.

- Les couleurs sont dans l'objet `P`, les trois familles dans `FAMILLES`.
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
