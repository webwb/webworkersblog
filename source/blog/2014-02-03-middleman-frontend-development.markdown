---
title: middleman - design umsetzen
tags: [middleman, slim]
---

# Design umsetzen

Andre hat mir ein Design geschickt, dass ich jetzt prototypisch in HTML und CSS umsetze. 

![PSD](andres-design.png)

## Struktur

Zuerst wird die Vorlage grob unterteilt. Es gibt einen Header mit Logo, eine Navigation, eine Liste mit Teasern und einen Footer. Als Liste: 

    header
      h1 
      h2
    nav
    section
      article
      article
    footer

In ein [Slim](http://slim-lang.com)-Tempalte gegossen. Erstmal wurde hier die Datei `source/layouts/layout.html.slim` missbraucht. 

    doctype html
    html
      head
        meta charset="utf-8"
        meta http-equiv='X-UA-Compatible' content='IE=edge;chrome=1'
        title Prototype
      body
        .container
        header
          h1 the webworkers blog
          h2 Developer / Frontend-Developer / Webdesigner / Nerds
        nav
          ul
            li
              a href="#" Blog
            li
              a href="#" Über uns
            li
              a href="#" Projekte
            li
              a href="#" Kontakt
        #main
          section
           - 5.times
            article
              header 2014 — Rückblick. Vorausschau. Whatever. Preview
              p Da ist es wieder, das neue Jahr und die Leute da draußen nehmen
              footer
                .author André Borges
                time{pubdate date="2014-12-24"} 24.12.2014
            article
        footer

## Design

Anstatt CSS direkt zu schreiben, wird [SASS](http://sass-lang.com) via [compass](http://compass-style.org) genutzt. Middleman konvertiert SASS Dateien on-the-fly. 

    touch source/stylesheets/style.css.scss

### Reset / Normalize

Für das CSS wird [normalize.css](https://github.com/necolas/normalize.css/blob/master/normalize.css) statt eines klassischen CSS-Reset genutzt. 

    mkdir source/stylesheets/vendor
    cd source/stylesheets/vendor
    wget https://raw.github.com/necolas/normalize.css/master/normalize.css

In unserem SCSS sieht es dann so aus: 

    $ cat screen.css.scss
     // import normalize https://raw.github.com/necolas/normalize.css/master/normalize.css
    @import 'vendor/normalize';

Im Browser sieht es jetzt so aus. 
![Seite mit normalize](2014-02-03_html-normalize.png)




In die Gemfile gem "compass-normalize-plugin"

