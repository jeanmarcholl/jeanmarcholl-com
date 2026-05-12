# jeanmarcholl.com

Site personnel de Jean-Marc Holl — Consultant IA & Coach Exécutif HEC.

## Stack

- HTML statique + Tailwind CSS (CDN) + Geist (Google Fonts)
- Firebase Hosting
- 3 pages : `/`, `/coaching`, `/consulting-ia`

## Structure

```
.
├── firebase.json            ← Config Firebase Hosting (clean URLs, cache headers)
├── .firebaserc              ← Lien vers le projet Firebase
├── .gitignore
└── public/                  ← Tout ce qui est servi (webroot Firebase)
    ├── index.html           → /
    ├── coaching.html        → /coaching
    ├── consulting-ia.html   → /consulting-ia
    ├── styles.css
    ├── favicon.svg
    └── photos/
        └── jeanmarc-pro.jpg
```

> Firebase Hosting est configuré avec `cleanUrls: true` : les fichiers
> `.html` sont servis sans extension (`/coaching` plutôt que `/coaching.html`).

## Développement local

Aucun build, juste ouvrir `public/index.html` dans un navigateur.
Ou avec un serveur statique :

```bash
npx serve public
# puis http://localhost:3000
```

## Déploiement Firebase

```bash
# Une seule fois
firebase login
firebase use --add        # sélectionner le projet Firebase

# À chaque déploiement
firebase deploy --only hosting
```

## Changer la photo

Remplacer `public/photos/jeanmarc-pro.jpg`. Si le cadrage change, ajuster
`object-position` dans les 3 fichiers HTML (recherche `object-position`).

## Changer le contenu

Tout est en HTML statique éditable directement. Pas de CMS, pas de build.

## TODO éventuels

- [ ] Compresser la photo en WebP avec fallback JPG (`<picture>`)
- [ ] Remplacer Tailwind CDN par un build minifié pour Lighthouse
- [ ] Ajouter une image Open Graph (1200×630) en `public/og.jpg`
