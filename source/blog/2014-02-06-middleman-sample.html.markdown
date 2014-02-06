---
title: Middleman - Sample 01
date: 2014-02-06
tags: [middleman, livereload]
---

# Live Reload

[http://livereload.com/](http://livereload.com/) refreshed den Browser, sobald Änderungen an den Sourcen gemacht wurden. 

Zur Aktivierung muss lediglich das Kommentar `#` in der entsprechende Zeile in der `config.rb` entfernt werden. 


Hier in 3 Schritten CLI.

    $ grep -A1 -B1 livereload config.rb
    # Reload the browser automatically whenever files change
    # activate :livereload
    $ sed -i.$(date -u +"%Y-%m-%dT%H:%M:%S") '/# activate :livereload/s/^#//' config.rb
    $ grep -A1 -B1 livereload config.rb
    # Reload the browser automatically whenever files change
     activate :livereload

Damit `middleman` LiveReload findet, muss das `Gemfile` entsprechend ergänzt werden. 

    echo 'gem "middleman-livereload"' >> Gemfile

