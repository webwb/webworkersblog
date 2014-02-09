---
title: Middleman - Setup
date: 2014-02-02
category: code
tags: [middleman]
---

# Middleman - Entwicklungsumgebung in wenigen Schritten 

Für die Frontend Entwicklung gibt es mittlerweile viele großartige Tools. Mein aktueller Favorit ist Middleman; bietet SASS, Compass, Erb, Haml, Slim, Coffeescript, ... und Blogging ... und und und. 

Mit dem Standard Setup kommt man sehr schnell nach vorne.

    gem install middleman
    gem install middleman-blog
    middleman init prototype --template=blog
    cd prototype

Obige Befehle haben folgende Struktur angelegt. 

    $ tree -F
    .
    ├── Gemfile
    ├── Gemfile.lock
    ├── config.rb
    └── source/
        ├── 2012-01-01-example-article.html.markdown
        ├── calendar.html.erb
        ├── feed.xml.builder
        ├── images/
        ├── index.html.erb
        ├── javascripts/
        ├── layout.erb
        ├── stylesheets/
        └── tag.html.erb

Wie man hier sieht gibt es eine Konfigurationsdatei `config.rb` und ein Arbeitsordner `soruce/`. 

## Start 

Mit `middleman` kann ein lokaler Webserver gestartet werden, der auf lokal auf Port 4567 erreichbar ist [http://localhost:4567/](http://localhost:4567/). 

![first start](2014-02-03_mm001.png)


## Anpassungen

Wie häufig kann man mit wenigen Anpassungen noch mehr aus Dingen herausholen. Ich werde in den nächsten Posts einige Standards anpassen und ihre Funktion dabei beschreiben. 

Wen interessiert was gerade geladen ist, kann unter [http://localhost:4567/__middleman/](http://localhost:4567/__middleman/) nachschauen. 




