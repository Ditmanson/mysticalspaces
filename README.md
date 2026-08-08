+++
date = '2026-03-01T18:31:04-07:00'
title = 'Simplest Theme'
+++

# Start
I didn't design this like most themes, but you can install it like any other theme. Git clone it into your themes folder or whatever. What I'd prefer is after you clone this you just remove the .git repo and start with this. The themes folder is pointless if you're someone starting here.
```

├── archetypes  
│   └── default.md  # useful for command `hugo new <path><file>`
├── assets
├── content # {{ .Content }}
│   ├── _index.md {{ Content for home.html}}
│   └── posts
│       ├── _index.md # {{ Content for root of a section. Section.html }}
│       └── first-post.md #{{ page.html }}
├── data # haven't used. i think you can put code and json in here
├── hugo.yaml # config file. set Sitewide variables
├── i18n # I don't know
├── layouts
│   ├── _partials  # These are called within the layouts as {{ .partials <partial> }}
│   │   ├── footer.html 
│   │   ├── head.html # Not needed but this is where you'd put cdn's and stuff like that
│   │   └── header.html # where i put the navbar
│   ├── baseof.html # boiler plate
│   ├── home.html # like  page.html but specifically for the index
│   ├── page.html # For non list view. How a single file is displayed
│   └── section.html # for list view
├── public # rendered for deployment
│   ├── categories
│   │   ├── index.html
│   │   └── index.xml
│   ├── index.html
│   ├── index.xml
│   ├── posts
│   │   ├── first-post
│   │   ├── index.html
│   │   └── index.xml
│   ├── sitemap.xml
│   └── tags
│       ├── index.html
│       └── index.xml
├── static # static
└── themes # pointless
```

# Additionally I have examples of a couple other files.

`_markup/render-heading.html`
---
```html
<h{{ .Level }} class="{{ if eq .Level 1 }}title is-1{{ else if eq .Level 2 }}title is-2{{ else if eq .Level 3 }}title is-3{{ else if eq .Level 4 }}title is-4{{ else }}title is-5{{ end }}">
  {{ .Text }}
</h{{ .Level }}>
```

This is for overwriting the use of a header tag. I used this to get headear tags to work with Bulma css.

`_markup/render-image.html`
---
```html
<div class="block">
  <figure class="image {{ .Title }} mt-2 mb-2" >
    <img src="{{ .Destination | safeURL }}"
      {{- with .PlainText }} alt="{{ . }}"{{ end }}>
  </figure>
</div>

```

Similar except for this is for image tags. Taking advantage of how you can set title field of image hyperlinks in markdown to control the class.

More render hooks and shortcodes that can be overwritten are in the docs. I think this is enough for you to create something.

# mysticalspaces
