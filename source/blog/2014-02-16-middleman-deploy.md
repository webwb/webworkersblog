---
title: Automating Middleman Deployments with middleman-deploy
date: 2014-02-16
tags: [middleman]
category: code
---

Tom Vaughan maintains [middleman-deploy](https://github.com/tvaughan/middleman-deploy) a middleman extension for various easy deployments, such as rsync via ssh, github-pages, sftp. 
This my small documentation of the installation and configuration. 

## Installation

Add  `gem "middleman-deploy"` to the Gemsfile and run `bundle install`. 

```ruby
activate :deploy do |deploy|
  deploy.method = :rsync
  deploy.host   = "blsn.de"
  deploy.path   = "/var/www/virtual/blsn/html/build/"
  # Optional Settings
  deploy.clean = true # remove orphaned files on remote host, default: false
  deploy.build_before = true # default: false
end
```




