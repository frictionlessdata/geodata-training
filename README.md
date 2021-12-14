# GeoData Training

## Development

Here is a quick instruction for working with the project.

### Getting Started

Create a virtual environment (optional):

```bash
$ python3.8 -m venv .python
$ source .python/bin/activate
```

Intall dependencies:

```
$ pip install -r requirements.txt
```

Start livereload server:

```bash
$ livemark start
# will open http://localhost:7000
```

Build the project (usually you don't need this command if you use `livemark start`):

```bash
$ livemark build
```

### Configuring the Project

> https://livemark.frictionlessdata.io/pages/getting-started/configuration.html

There is a `livemark.yaml` file that provides a full project configuration. Optionally, you can add configuration to individual pages but usually `livemark.yaml` in the root directory is enough. Using this file you can add and remove pages, change their in-navigation titles, and tweak other settings.

To disable some plugin set it to `false`:

> livemark.yaml

```
search: false
```

It will remove the search block from all the pages. See feature reference to figure out a plugin name you want to disable - https://livemark.frictionlessdata.io/pages/feature-reference/general.html.

### Editing the Contents

The main plugin to support multiplage sites is called `pages`. You can see its settings in `livemark.yaml`:

> livemark.yaml

```yaml
pages:
  items:
    - path: index
      name: Introduction
    - path: pages/before
    - path: pages/during
    - path: pages/mentoring
    - path: pages/completing
    - path: pages/examples
```

Here is you can configure which markdown documents will be built to HTML pages. You are not tied to any naming conventions so you can move `pages` to a different directory or to the root directory just updating the corresponding definitions.

### Adding HTML blocks

Anytime you need to add raw HTML to your markdown files just use the codeblock syntax with the `html markup` header (replace single quotes "'" by back ticks "`"):

> document.md

```md
My markdown paragrap 1

'''html markup
<div class="container">
  <div class="row">
    <div class="col-sm">
      One of three columns
    </div>
    <div class="col-sm">
      One of three columns
    </div>
    <div class="col-sm">
      One of three columns
    </div>
  </div>
</div>
'''

My markdown paragrap 2
```

By default Livemark includes these client-side libraries:
- Bootstrap 4 (currently migrating to v5)
- Font Awesome 5
- Lodash 4
- jQuery 3

### Styling the Project

The main plugin for rendering project as HTML pages called `site`. You can see its settings in `livemark.yaml`:

> livemark.yaml

```yaml
site:
  favicon: assets/favicon.ico
  layout: layout.html
  styles:
    - style.css
```

To update the layout change `layout.html` (e.g. adding a footer) and to change the CSS styles change `style.css`'s rules. You need to run `livemark build` even though your livereload server is running (currently it's a limitation of the livereload server -- it doesn't update styles automatically).

### Deploying the Project

Both `livemark build` and `livemark start` build the project as a set of HTML pages (you can see near your markdown sources). Once it's built you can just enable Github Pages to server from the `main` branch and it will be automatically deployed on every push to Github.

An examplar deployment is set up here:

- https://github.com/frictionlessdata/geodata-training

### Extending the Project

You can hook basically into any aspect of Livemark build using the plugin system:
- https://livemark.frictionlessdata.io/pages/plugin-system/adding-plugin.html
- https://livemark.frictionlessdata.io/pages/plugin-system/writing-plugin.html

### Solving Problems

Please file an issues or a question - https://github.com/frictionlessdata/livemark
