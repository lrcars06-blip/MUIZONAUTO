# Muizon Automobiles — site vitrine

Site vitrine d'une page pour Muizon Automobiles (31 Route Nationale, 51140 Muizon) : animation d'accueil, catalogue filtrable, fiches véhicule, services, horaires, carte et formulaire.

Tout tient dans `index.html` (HTML, CSS et JavaScript). Aucune installation, aucune dépendance à compiler.

## Voir le site en local

Ouvrir `index.html` dans un navigateur. Ajouter `?intro` à l'adresse pour rejouer l'animation d'accueil.

## Mettre en ligne

**Vercel** : importer ce dépôt sur vercel.com, laisser tous les réglages par défaut (aucune commande de build), déployer.

**GitHub Pages** : dans le dépôt, Settings > Pages > Source « Deploy from a branch », branche `main`, dossier `/ (root)`.

## Réglages

Tout se règle dans l'objet `CONFIG`, au début du script en bas de `index.html`.

| Clé | Rôle | Si vide |
| --- | --- | --- |
| `phone` | Téléphone affiché, ex. `"03 26 12 34 56"` | Boutons « Appeler » masqués |
| `email` | Adresse de réception du formulaire (ouvre la messagerie du visiteur) | Voir `formEndpoint` |
| `formEndpoint` | URL d'envoi du formulaire (Formspree, Basin, route API), POST JSON | Message d'indisponibilité si `email` est vide aussi |
| `instagram` | Identifiant Instagram sans @ | Liens Instagram masqués |
| `instagramFeedUrl` | URL JSON d'un flux Behold pour afficher les dernières publications | Photos du catalogue à la place |
| `featured` | Identifiants des véhicules affichés dans le hero | Encart masqué |
| `pageSize` | Nombre de véhicules avant « Afficher plus » | — |
| `hours` | Horaires servant au statut ouvert / fermé | — |

Si les horaires changent, modifier aussi le tableau `#hours` dans le HTML et le bloc JSON-LD dans le `<head>`.

## Catalogue

Les véhicules sont dans le tableau `VEHICLES`, juste sous `CONFIG`. Un véhicule :

```js
{ id:"touareg", cat:"suv", brand:"Volkswagen", model:"Touareg", version:"3.0 V6 TDI R-Line",
  year:2016, km:121500, fuel:"Diesel", box:"Automatique", price:26980,
  tags:["Première main"], equip:["Suivi d'entretien","Attelage"],
  photos:["photo-1.jpg","photo-2.jpg"], url:"https://lien-vers-l-annonce", demo:false }
```

- `cat` : `citadine`, `suv`, `famille` ou `plaisir`.
- `photos` : chemin d'un fichier déposé à côté de `index.html` (`"./touareg-1.jpg"`), URL complète, ou identifiant Unsplash. La première photo sert de vignette, quatre au maximum dans la fiche.
- `url` : lien facultatif vers l'annonce complète.
- Lien direct vers une fiche : `index.html#voiture-<id>`.

## À remplacer avant la mise en ligne définitive

- **Photos** : images d'illustration Unsplash, chargées par lien. Ce ne sont pas les voitures du garage.
- **Fiches `demo: true`** : dix fiches inventées pour la maquette (année, kilométrage, prix, équipements). Les huit fiches `demo: false` reprennent les annonces réelles du 12 octobre 2026.
- **Mentions légales** : hébergeur à compléter.
- **Horaires** : samedi 9 h – 18 h et lundi jusqu'à 19 h d'après leboncoin, à confirmer avec le garage.
