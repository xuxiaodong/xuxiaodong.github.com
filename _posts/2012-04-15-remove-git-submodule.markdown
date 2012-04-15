---
layout: post
title: 移除 Git Submodule
date: 2012-04-15 11:03
post-link: http://stackoverflow.com/questions/1260748/how-do-i-remove-a-git-submodule
---

遗憾的是，Git 没有专用的移除 submodule 的命令，一切必须手工完成。为方便计，还
是写个脚本吧。

    #!/usr/bin/env ruby
    
    require 'fileutils'
    
    def remove(path)
      system "git rm --cached #{path}"
    
      files = [".git/config", ".gitmodules"]
      files.each { |file| system "git config -f #{file} --remove-section submodule.#{path}" }
    
      FileUtils.rmtree(path)
    end
    
    if ARGV.empty?
      puts "Usage: rm_submod <path>"
    else
      ARGV.each { |path| remove(path) }
    end
