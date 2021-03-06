# Sheffood website

Sheffood is a static website, built using [Hugo](https://gohugo.io/) and [Webpack](https://webpack.js.org/) as the asset pipeline.

Sheffood is setup to use [PostCSS](http://postcss.org/) and [Babel](https://babeljs.io/) for CSS and JavaScript compiling/transpiling.

This project is released under the [MIT license](LICENSE). Please make sure you understand its implications and guarantees.

## To do
    
- [ ] README
    - contact form (Review submissions at https://app.netlify.com/sites/friendly-keller-6bc5e3/forms/5d985d459d5c5600089a3b04)
    - ID
    - editing - GH
    - editing Netlify
    
## To check with the team

- [ ] 2-column layout change in About/Contact/Sustainable cities
- [ ] Need for Lead para?
- [ ] Newsletter sign-up – preferably not on contact page, and not as delayed popover...
- [ ] Form submission destination


### To do stretch items

- [ ] Add analytics
- [ ] Add menu frontmatter to Netlify CMS page template
- [ ] Footer - resize images
- [ ] Review accessibility
- [ ] Review `head` matter
- [ ] Remove Netlify identity widget from default template, and only load on homepage & CMS page.
- [ ] Responsive images
- [ ] Events - show start to end (date, time, etc.)

## Usage

### Prerequisites

- Node >10
- NPM 

Next step, clone this repository and run:

```bash
npm install
```

This will take some time and will install all packages necessary to run Sheffood.

### :construction_worker: Development

While developing, use:

```bash
npm run preview
```

Then visit http://localhost:3000/ _- or a new browser windows popped-up already -_ to preview your new website. Webpack Dev Server will automatically reload the CSS or refresh the whole page, when stylesheets or content changes.

### :package: Static build

To build a static version of the website inside the `/dist` folder, run:

```bash
npm run build
```

To get a preview of posts or articles not yet published, run:

```bash
npm run build:preview
```

See [package.json](package.json#L8) for all tasks.

## Structure

```
|--site                // Everything in here will be built with hugo
|  |--content          // Pages and collections - ask if you need extra pages
|  |--data             // YAML data files with any data for use in examples
|  |--layouts          // This is where all templates go
|  |  |--partials      // This is where includes live
|  |  |--index.html    // The index page
|  |--static           // Files in here ends up in the public folder
|--src                 // Files that will pass through the asset pipeline
|  |--css              // Webpack will bundle imported css seperately
|  |--index.js         // index.js is the webpack entry for your css & js assets
```

## Basic Concepts

You can read more about Hugo's template language in their documentation here:

https://gohugo.io/templates/overview/

The most useful page there is the one about the available functions:

https://gohugo.io/templates/functions/

For assets that are completely static and don't need to go through the asset pipeline,
use the `site/static` folder. Images, font-files, etc, all go there.

Files in the static folder end up in the web root. So a file called `site/static/favicon.ico`
will end up being available as `/favicon.ico` and so on...

The `src/index.js` file is the entrypoint for webpack and will be built to `/dist/main.js`

You can use **ES6** and use both relative imports or import libraries from npm.

Any CSS file imported into the `index.js` will be run through Webpack, compiled with [PostCSS Next](http://cssnext.io/), and
minified to `/dist/[name].[hash:5].css`. Import statements will be resolved as part of the build.

## Environment variables

To separate the development and production _- aka build -_ stages, all gulp tasks run with a node environment variable named either `development` or `production`.

You can access the environment variable inside the theme files with `getenv "NODE_ENV"`. See the following example for a conditional statement:

    {{ if eq (getenv "NODE_ENV") "development" }}You're in development!{{ end }}

All tasks starting with _build_ set the environment variable to `production` - the other will set it to `development`.

## Credit

This is based on the [Victor Hugo](https://github.com/netlify-templates/victor-hugo) boilerplate.

## Enjoy!! 😸
