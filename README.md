# R5.Crea.06_25

# Astro JS le retour

**Astro** est un framework JavaScript moderne conçu pour créer des sites web statiques et dynamiques ultra-rapides
(Générateur de Sites Statiques SSG).

## Rappels configuration VSCode

- Installer l'extension **Astro** pour **VSCode** pour bénéficier de la coloration syntaxique et des suggestions de code.

- Modification des settings de VSCode

```json
{
  "emmet.includeLanguages": {
    "astro": "html"
  },
  "tailwindCSS.includeLanguages": {
    "astro": "astro"
  },
  "prettier.documentSelectors": ["**/*.astro"],
  "[astro]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

## A\_ Créez et déployez votre premier site Astro

### A_1 Installation et Configuration

#### \_Créez votre premier projet Astro

- Créer un répertoire pour votre projet Astro, l'ouvrir dans VSCode et ouvrir le Terminal.

- Créez un nouveau projet Astro en utilisant la commande suivante :

```bash
  # create a new project with npm
  npm create astro@latest
```

- Confirmer `y` pour installer `create-astro`

- Lorsque l'invite vous demande où créer le projet, saisissez le nom d'un dossier pour créer un nouveau répertoire pour votre projet, par exemple `./td_Astro` ou `.` pour créer le projet dans le répertoire actuel.

- Lorsque l'invite vous demande si vous souhaitez ou non installer des dépendances, saisissez ou sélectionnez `y`.

- Lorsque l'invite vous demande si vous souhaitez ou non initialiser un nouveau référentiel git, saisissez ou sélectionnez `y`.

Remarque : il est possible de créer un projet Astro avec un modèle spécifique en utilisant l'option `--template` suivi du nom du modèle. Par exemple, pour créer un projet Astro avec le modèle minimal, utilisez la commande suivante :

```bash
  # create a new project with npm & template
  npm create astro@latest -- --template minimal
```

- Prettier :

```bash
  npm install --save-dev prettier prettier-plugin-astro
```

Ajouter un fichier`.prettierrc`:

```json
{
  "plugins": ["prettier-plugin-astro"],
  "overrides": [
    {
      "files": "*.astro",
      "options": {
        "parser": "astro"
      }
    }
  ]
}
```

#### \_Démarrer le serveur de développement

L'installation de votre projet Astro est maintenant terminée. Pour démarrer votre projet exécutez la commande suivante :

```bash
  npm run dev
```

Vous devriez maintenant voir la confirmation dans le terminal qu'Astro fonctionne en mode développement. 🚀

Ouvrir votre projet sur `http://localhost:4321` dans votre navigateur pour voir votre site Astro en action.

#### \_Structure du projet

Astro suit une structure de projet standard pour les applications web modernes. Voici un aperçu de la structure de votre projet Astro :

```bash
  my-project/
  │── public/ (Fichiers statiques)
  │── src/ (contient tous les fichiers sources de votre projet Astro)
  │ ├── assets/ (Fichiers)
  │ ├── components/ (Composants réutilisables)
  │ ├── content/ (Collections de contenu. Ex: articles md, mdx ou json)
  │ ├── layouts/ (Templates globaux)
  │ ├── pages/ (Contient les routes du site)
  │ ├── styles/ (Fichiers de styles)
  │── astro.config.mjs (Configuration Astro)
  │── package.json
```

<!-- GITHUB -->

### A_2 Stockez votre repo en ligne

#### \_Créer un dépôt sur GitHub

#### \_Envoyez votre code local sur GitHub
```bash
git remote add origin https://github.com/[...]
git branch -M main
git push -u origin main
```

#### \_Déployer votre site

Vous pouvez déployer un site Astro sur **GitHub Pages** en utilisant GitHub Actions pour créer et déployer automatiquement votre site.

[doc](https://docs.astro.build/en/guides/deploy/github/)

---

<!-- TailwindCss -->

### A_3 Styling : TailwindCSS

La prise en charge de **Tailwind** dans Astro est fournie par un plugin Vite.

- 1/ Installer le plugin dans Astro

```bash
npx astro add tailwind
```

- 2/ Importez tailwindcss dans `src/styles/global.css`
  (ou un autre fichier CSS de votre choix) pour rendre les classes Tailwind disponibles pour votre projet Astro.
  Ce fichier incluant l’importation sera créé par défaut si vous avez utilisé la commande astro add tailwind pour installer le plugin Vite.

```css
/* src/styles/global.css */
@import "tailwindcss";
```

- 3/ Importez ce fichier dans les pages où vous souhaitez appliquer Tailwind. Cette opération est souvent effectuée dans un composant de mise en page afin que les styles Tailwind puissent être utilisés sur toutes les pages partageant cette mise en page :
  `src/layouts/Layout.astro`

```jsx
---
import "../styles/global.css";
---
```

- Prettier pour TailwindCSS:

```bash
  npm install --save-dev prettier-plugin-tailwindcss
```

Modifier le fichier `.prettierrc`

```json
{
  "plugins": ["prettier-plugin-astro", "prettier-plugin-tailwindcss"],
  "overrides": [
    {
      "files": "*.astro",
      "options": {
        "parser": "astro"
      }
    }
  ]
}
```

## B\_ Rappels Astro Basics

### B_1 Routage Astro

**Astro** utilise un **routage basé sur des fichiers** pour générer vos URL de build en fonction de la disposition des fichiers de votre répertoire de projet `src/pages/`.

Différents types de fichiers de routage Astro :

- `.astro`
- `.md`
- `.html`

Structure de la page `.astro` :

```jsx
---
// Component Script (JavaScript) - FrontMatter
---

<!-- Component Template (HTML + JS Expressions) -->
```

Les clôtures `---` `Code Fences` - **FrontMatter** - sont la partie script de votre composant Astro. Vous pouvez utiliser une clôture pour écrire n'importe quelles expressions JavaScript

#### \_Modifier pages/index.astro

Modifier le fichier `src/pages/index.astro` pour afficher un message de bienvenue.

```jsx
---
---

<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content="{Astro.generator}" />
    <title>Home</title>
  </head>
  <body>
    <h1>Hello MMI 🚀</h1>
    <p>Créative Coding.</p>
  </body>
</html>
```

#### \_Créer une nouvelle page

- Créez un nouveau fichier `about` dans `src/pages/` avec l'extension `.astro`, `.md` ou `.html`.

```jsx
---
---

<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content="{Astro.generator}" />
    <title>About</title>
  </head>
  <body>
    <h1>About me 🧑‍🚀</h1>
    <p>Créative Coding.</p>
  </body>
</html>
```

> Ce fichier est accessible à l'URL `http://localhost:4321/about`.

- Pour pouvoir naviguer facilement entre les pages, il faut ajoutez une navigation aux différents fichiers `index.astro` et `about.astro`

```jsx
...
<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
  </ul>
</nav>
...
```

### B_2 Composants Astro

Astro utilise des **composants** pour réutiliser du code et créer des éléments de page modulaires.

- Créez un répertoire `components` dans `src/` pour stocker vos composants Astro.
- Créez un nouveau fichier `Header.astro` dans `src/components/` avec une **majuscule** et l'extension `.astro`.

```astro
---
---
<header>
  <nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
  </ul>
  </nav>
</header>

```

- L'étape suivante consiste à ajouter le composant à nos pages. Pour ce faire, nous devons importer le composant.

```jsx
---
import Header from ‘../components/Header.astro’;
---

<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content="{Astro.generator}" />
    <title>About</title>
  </head>
  <body>
    <!-- Ajouter le composant <Header/> -->
    <Header />
    <h1>About</h1>
    <p>MMI Crea</p>
  </body>
</html>
```

### B_3 Ajouter du code JavaScript à un composant Astro

Il peut être nécessaire d'ajouter du code **Javascript** à un composant Astro pour ajouter des fonctionnalités supplémentaires : dynamiser le contenu, ajouter des animations, des intérations etc.

```jsx
---
import Header from ‘../components/Header.astro’;
// Définir une variable title
const title = 'About';
---

<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content="{Astro.generator}" />
    <title>About</title>
  </head>
  <body>
    <Header />
    <h1>{title}</h1>
    <p>MMI Crea</p>
  </body>
</html>
```

> Pour untiliser la variable `title` dans le composant Astro, il suffit de l'entourer de `{}`.

### B_4 Création de modèles de page avec Astro Layouts

Astro **Layouts** est un composant permettant de créer des **modèles globaux** de page pour votre site Astro.

- Créez un répertoire `layouts` dans `src/` pour stocker vos modèles Astro.

- Créez un nouveau fichier `BaseLayout.astro` dans `src/layouts/` avec une **majuscule** et l'extension `.astro`.

```jsx
---
const title = 'Astro BaseLayouts';
---

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content="{Astro.generator}" />
    <title>{title}</title>
  </head>
  <body></body>
</html>
```

#### `_slot`

Astro utilise une **balise `slot`** pour insérer le contenu de la page dans le modèle.

`<slot/>`élément est un espace réservé pour le contenu HTML externe. Il spécifie où les éléments enfants d'autres fichiers doivent être injectés dans votre modèle de composant.

```jsx
---
const title = 'Astro BaseLayouts';
---

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content="{Astro.generator}" />
    <title>{title}</title>
  </head>
  <body>
    <Header />
    <slot />
  </body>
</html>
```

#### \_Utilisation de BaseLayout

- Importez le modèle `BaseLayout` dans votre fichier `about.astro`.

```jsx
---
import BaseLayout from '../layouts/BaseLayout.astro';
const title = 'About';
---

<BaseLayout>
  <h1>{title}</h1>
  <p>MMI Crea</p>
</BaseLayout>
```

#### \_Props

Astro utilise des **props** (propriétés) pour passer des données entre les composants Astro.

Dans le fichier `BaseLayout.astro`, ajoutez une prop `title` pour afficher le titre de la page.

```jsx
---
import Header from '../components/Header.astro';
const {title="default"}= Astro.props
---

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content="{Astro.generator}" />
    <title>{title}</title>
  </head>
  <body>
    <Header />
    <slot />
  </body>
</html>
```

Dans le fichier `about.astro`, passez le titre de la page en tant que prop `title` au modèle `BaseLayout`.

```jsx
---
import BaseLayout from '../layouts/BaseLayout.astro';
const title = 'About';
---

<BaseLayout title="{title}">
  <h1>{title}</h1>
  <p>MMI Crea</p>
</BaseLayout>
```

## C - Astro Advanced

### C_1 Astro Data

Astro Data est un moyen de charger des données externes dans vos composants Astro.

**Astro Data** prend en charge les sources de données suivantes :

- JSON
- Markdown
  ...

#### \_Charger des données JSON

- Créez un nouveau fichier `data.json` dans `src/dat` avec des données JSON.

```json
{
  "title": "Astro Data",
  "description": "Astro Data is a way to load external data into your Astro components."
}
```

- Importez les données JSON dans votre composant Astro.

```astro
---
import data from '../data/data.json';
---
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <title>{data.title}</title>
  </head>
  <body>
    <Header />
    <h1>{data.title}</h1>
    <p>{data.description}</p>
  </body>
</html>
```

#### \_Charger des données JSON et les mapper

- Créez un nouveau fichier `data.json` dans `src/data` avec des données JSON.

```json
[
  {
    "name": "HTML",
    "level": "Advanced"
  },
  {
    "name": "CSS",
    "level": "Intermediate"
  },
  {
    "name": "JavaScript",
    "level": "Advanced"
  }
]
```

- Importez les données JSON dans votre composant Astro et mappez-les pour afficher les compétences.

```astro
---
import compet from '../data/compet.json';
---
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <title>Compétences</title>
  </head>
  <body>
    <Header />
    <h1>Compétences</h1>
    <ul>
      {compet.map((item) => (
        <li>{item.name}: {item.level}</li>
      ))}
    </ul>
  </body>
</html>
```

### Ref :

[Style doc Astro](https://docs.astro.build/en/guides/styling/)

[link tailwindCSS](https://tailwindcss.com/docs/installation/framework-guides/astro)

[Prettier](https://astro-tips.dev/tips/prettier/)

## À SUIVRE

- MCP serveur

- Images et icons

https://www.astroicon.dev

## MÉMO

### Création d'un nouveau projet Astro

```bash
  # create a new project with npm
  npm create astro@latest
```

### Installation de Prettier

```bash
  # install Prettier and the Astro plugin
  npm install --save-dev prettier prettier-plugin-astro
```

Ajouter un fichier`.prettierrc`:

```json
{
  "plugins": ["prettier-plugin-astro"],
  "overrides": [
    {
      "files": "*.astro",
      "options": {
        "parser": "astro"
      }
    }
  ]
}
```

### Installation de Tailwind CSS

```bash
  # install Tailwind CSS pour Astro
  npx astro add tailwind
```

- Prettier pour TailwindCSS:

```bash
  npm install --save-dev prettier-plugin-tailwindcss
```

Modifier le fichier `.prettierrc`

```json
{
  "plugins": ["prettier-plugin-astro", "prettier-plugin-tailwindcss"],
  "overrides": [
    {
      "files": "*.astro",
      "options": {
        "parser": "astro"
      }
    }
  ]
}
```
