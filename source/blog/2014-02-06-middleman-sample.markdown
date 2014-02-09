---
title: Middleman - Live Reload
date: 2014-02-06
tags: [middleman, livereload]
---

[Livereload](http://livereload.com/) refreshed den Browser sobald Änderungen an den Sourcen gespeichert werden. 

Zur Aktivierung muss in `config.rb` lediglich das Kommentar (`#`) in der folgenden Zeile entfernt werden. 

    # activate :livereload

Hier in per `sed`: 

    $ grep -A1 -B1 livereload config.rb
    # Reload the browser automatically whenever files change
    # activate :livereload
    $ sed -i.$(date -u +"%Y-%m-%dT%H:%M:%S") '/# activate :livereload/s/^#//' config.rb
    $ grep -A1 -B1 livereload config.rb
    # Reload the browser automatically whenever files change
     activate :livereload

Damit `middleman` LiveReload findet, muss das `Gemfile` entsprechend ergänzt werden. 

    echo 'gem "middleman-livereload"' >> Gemfile

