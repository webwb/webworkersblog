---
title: middleman - slim template
date: 2014-02-02
tags: [middleman, slim]
category: code
---

# Slim - schicke schlanke Template-Engine

[Slim](http://slim-lang.com) ist ein Template-Engine, die versucht die häufig sperrige Syntax zu vereinfachen; Spritzeklammern, schliessende Tags, ade. 

Middleman unterstüzt via `tilt` u.a. auch Slim <http://middlemanapp.com/basics/templates/#toc_9>. 

Allerdings muss Middleman einmal im Gemfile und zum anderen in der config.rb bescheid geben, dass man Slim nutzen will. Das geht so ...

    echo 'gem "slim"' >> Gemfile

    sed -i.$(date -u +"%Y-%m-%dT%lH:%M:%S") '1{x;s/$/require "slim"/;G;}' config.rb

## Standard layout.erb ersetzten

Die erb dient erstmal als Vorlagen; das Original wird gesichert. 

    cp source/layouts/layout.erb source/layouts/layout.html.slim
    mv source/layouts/layout.erb source/layouts/original.layout.erb

Nach ein der Umwandlung sieht das Layout jetzt so aus: 

    doctype html
    html
      head
        meta charset="utf-8"
        meta http-equiv='X-UA-Compatible' content='IE=edge;chrome=1'
        title Blog Title #{'- ' + current_article.title unless current_article.nil?}
        = feed_tag :atom, "#{blog.options.prefix.to_s}/feed.xml", title: "Atom Feed"
      body
        #main role="main"
          == yield    
        aside
          h2 Recent Articles
          ol
            - blog.articles[0...10].each do |article| 
              li = link_to article.title
                span = article.date.strftime('%b %e')
          h2 Tags
          ol
            - blog.tags.each do |tag, articles| 
              li 
                  = link_to tag, tag_path(tag) 
                  |  (
                  = articles.size
                  | )
          h2 By Year
          ol
            - blog.articles.group_by {|a| a.date.year }.each do |year, articles| 
              li 
                = link_to year, blog_year_path(year) 
                |  (
                = articles.size
                | )


