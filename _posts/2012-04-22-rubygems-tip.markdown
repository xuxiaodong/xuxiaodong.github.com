---
layout: post
title: 避免 RubyGems 自动生成文档
date: 2012-04-22 22:50
post-link: http://ruby.railstutorial.org/ruby-on-rails-tutorial-book
---

要避免 RubyGems 在安装 gems 时自动生成 ri 和 rdoc 文档，只需在 ~/.gemrc
中加入如下两行即可：

    install: --no-rdoc --no-ri
    update: --no-rdoc --no-ri
