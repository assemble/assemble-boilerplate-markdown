

> Layouts are used for "wrapping" the content of individual pages with common HTNL, such as a "header" and "footer". 


## Layout example

Layouts are optional, but the `\{{> body }}` tag is required for content to be pulled into a layout.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>\{{title}}</title>
  </head>
  <body>
    <!-- the body tag is used to "pull in" content from pages -->
    \{{> body }}
  </body>
</html>
```


## Granular control

1. **Task options**: Great for defining a "project-wide" default. 
2. **Target options**: Override the "project default" in the `options` for each target. Offers greater control over which "types" of pages get which `layout`. 
3. **Page-by-page**: If you require more granularity you can define a layout in the [YFM][yaml-front-matter] of a page




### Multiple layouts

Since you can create as many [targets][] as you require, defining layouts in the Gruntfile is a great way of quickly setting up your layout "defaults". In the `assemble` task in your Gruntfile.js, you can define a layout at the task-level, and/or a different layout for each build target:

``` javscript
assemble: {
  options: {
    layout: 'layouts/default.hbs'
  },
  site: {
    files: {
      'site/': ['templates/pages/*.hbs']
    }
  },
  blog: {
    options: {
      layout: 'layout/post.hbs'
    },
    files: {
      'blog/': ['templates/posts/*.hbs']
    }
  },
  docs: {
    options: {
      layout: 'layouts/docs.hbs'
    },
    files: {
      'docs/': ['templates/docs/*.hbs']
    }
  }
}
```

## Page-specific Layouts

If you require a higher level of granularity than defining layouts in the Gruntfile, you may also define layouts on a page-by-page basis, thus overriding both the task-level ("global") defaults and the target-level defaults.

To do so, just add the layout to the [YFM][yaml-front-matter] of the page like this:

``` yaml
---
layout: path/to/layout.hbs
---
```
 
## Disabling Layouts

* **Pages**: add `layout: false` to the YAML front matter of any page that should build without a layout. 
* **Targets**: add `layout: false` to the options of any target that should build pages without a layout. 


## Example usage
Your imagination is the only limit to what can be done with layouts, so these are just examples.


### Basic layout
This is something you might use to wrap basic pages for a demo, documentation, etc.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>\{{title}}</title>
  </head>
  <body>
    <header class="page-header">
      <h1>\{{title}} </h1>
      <p class="lead">\{{description}}</p>
    </header>
    <!-- the body tag is required to pull in content from pages -->
    \{{> body }}
  </body>
</html>
```

### Advanced layout

``` html
<!DOCTYPE html>
  <html>
  <head>
    <title>\{{page.title}} &middot; \{{ site.title }}</title>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    \{{> head-extras }}
    <script src="jquery.js"></script>
    <script src="site.js"></script>
  </head>
  <body class="\{{ page.modifier }}" id="\{{ page.id }}">

    <!-- HEADER -->
    <header id="header">

      <!-- SITE TITLE OR LOGO -->
      \{{#section main-header}}
      <h1 data-content-field="site-title">
        <a href="/">
          \{{#if site.logo}}
          <img src="\{{ assets }}/img/\{{ site.logo }}" alt="\{{ site.title }}">
          \{{else}}
          \{{ site.title }}
          \{{/if}}
        </a>
      </h1>
      \{{/section}}

      <!-- SITE TAGLINE -->
      \{{#section tagline}}
      <p>\{{.}}</p>
      \{{/section}}

      <!-- MAIN NAVIGATION -->
      \{{> main-navigation }}
    </header>

    <!-- CONTENT -->
    <section id="content">
      \{{> body }}
    </section>

    <!-- FOOTER -->
    <footer id="footer">
      \{{> footer }}
    </footer>

  </body>
</html>
```

### Markdown layout

Layouts don't have to be HTML, they can be whatever language you want them to be. If you're generating markdown pages instead of HTML, maybe for a project wiki or other markdown documentation, then you'll want to use a markdown formatted `layout`. 

In this example, instead of adding adding the traditional head and footer we'll add some link references to make sure the same ones are used on every generated page. This makes it easier to maintain links and it also cuts down on potential for broken links:

``` markdown
\{{> body }}

---

_This page was generated using Grunt and [assemble][repo] on \{{ today }}._

[org]: https://github.com/assemble
[repo]: https://github.com/assemble/assemble
[issues]: https://github.com/assemble/assemble/issues
[wiki]: https://github.com/assemble/assemble/wiki
```

## Layout FAQ
* Layouts are optional
* When a layout is specified, _it must include a `\{{> body }}` tag to render content_ from any file that uses the layout. 
* Layouts may be defined in the Gruntfile or in [YFM][yaml-front-matter] of a page. 
* A layout defined for a target will override a layout defined at the task level.
* A layout defined in [YFM][yaml-front-matter] will override a layout defined in the Gruntfile
* [Lo-dash templates][templates] can be used in YAML front-matter ayout. Path, file name and extension can be determined


## Related info
* [options.layout][options-layout]
* [Pages][pages]
* [Partials][partials]
* [Templates][templates]
* [YFM][yaml-front-matter]


