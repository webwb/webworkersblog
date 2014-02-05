---
title: Middleman - Layout
tags: [middleman, layouts, partials, blog]
---

# Middleman - Ordnung schaffen

## Layouts 

Die Standard-Installation hat das Layout in `source` erstellt. Middleman akzeptiert jedoch auch Layouts in `source/layouts` zu haben. Zwecks Ordnung erstellen wir den Ordner und verschieben die Datei. 

    mkdir source/layouts
    mv source/layout.erb source/layouts

## Blogposts

Die Blogpost liegen per defaullt ebenfalls im `source/`. Schöner ist hier ein eigener Ordner. Also Ordner erstellen und die vorhandenen Post hineinkopieren. 

    mkdir source/blog
    mv source/201*.html.markdown source/blog/

Damit Middleman die Posts auch findet ist in der `config.rb` die Konfiguration `blog.prefix = "blog"` zu aktivieren. 

Das geht entweder manuell oder per CLI [fn1]. 

    sed -i.$(date -u +"%Y-%m-%dT%lH:%M:%S") '/# blog.prefix = "blog"/s/#//' config.rb

In beiden sollte die config.rb ungefähr so aussehen:

    ...
    # Blog settings
    ###

    # Time.zone = "UTC"

    activate :blog do |blog|
      # This will add a prefix to all links, template references and source paths
       blog.prefix = "blog"

      # blog.permalink = "{year}/{month}/{day}/{title}.html"
      # Matcher for blog source files
      # blog.sources = "{year}-{month}-{day}-{title}.html"
      # blog.taglink = "tags/{tag}.html"
    ...

## Ergebnis 

Der Dateibaum sieht jetzt schon etwas sauberer aus. 

    $ tree -F
    .
    ├── Gemfile
    ├── Gemfile.lock
    ├── config.rb
    ├── config.rb.2014-02-03T10H:27:19
    ├── config.rb.2014-02-03T11H:27:21
    └── source/
        ├── blog/
        │   ├── 2012-01-01-example-article.html.markdown
        │   ├── 2014-02-02-middleman-layouts.html.markdown
        │   ├── 2014-02-02-middleman-livereload.html.markdown
        │   └── 2014-02-02-middleman-setup.html.markdown
        ├── calendar.html.erb
        ├── feed.xml.builder
        ├── images/
        │   ├── 2014-02-03_mm001.png
        │   └── upload.png
        ├── index.html.erb
        ├── javascripts/
        ├── layouts/
        │   └── layout.erb
        ├── stylesheets/
        └── tag.html.erb

[fn1]: Da noch keine Versionskontrolle eingeführt wurde, manuelle Sicherungen. 

