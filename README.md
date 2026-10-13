# Caast Hub

Page publique qui donne accès à tous les services Caast en un clic : **https://hub.caast.tv**

Site statique, sans build : `index.html` + `assets/`. Français par défaut, bouton FR / EN dans le header (choix mémorisé dans le navigateur, ou forcé avec `?lang=en`).

## Ajouter ou modifier un service

Tout se passe en haut du `<script>` de `index.html` :

- **Un service** = une entrée dans `SERVICES` :

  ```js
  { g: 'run', domain: 'exemple.caast.tv', url: 'https://exemple.caast.tv',
    fr: { name: 'Nom', short: 'Court', desc: 'Description, 55 caractères max.' },
    en: { name: 'Name', short: 'Short', desc: 'Description, 55 characters max.' } },
  ```

  `g` est l'id de la rubrique, `short` le libellé dans l'orbite du header. La tuile, la numérotation, l'orbite, les compteurs, les filtres et la recherche suivent automatiquement.

- **Une rubrique** = une entrée dans `GROUPS` (id, couleur, largeur mini des tuiles, libellés FR / EN).

- **Les textes d'interface** (titre, recherche, boutons) sont dans `UI`.

Les descriptions tiennent sur deux lignes : visez 55 caractères maximum.

## Déploiement (GitHub Pages)

1. Dans le dépôt : **Settings → Pages → Build and deployment → Source : Deploy from a branch**, branche `main`, dossier `/ (root)`.
2. Le fichier `CNAME` déclare déjà `hub.caast.tv`. Côté DNS, créer un enregistrement **CNAME `hub` → `crezeo.github.io`**.
3. Une fois le DNS propagé, cocher **Enforce HTTPS** dans Settings → Pages.

Chaque push sur `main` republie le site en une minute environ.

## Tester en local

```sh
python3 -m http.server 8000
# puis http://localhost:8000
```
