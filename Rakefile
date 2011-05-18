task :dev do
  c = Thread.new do
    `compass watch --sass-dir css --css-dir css`
  end
  j = Thread.new do
    `jekyll --server --auto`
  end
  sleep(1)
  c.join
  j.join
end

desc 'Generate tags page'
task :tags do
  puts "Generating tags..."
  require 'rubygems'
  require 'jekyll'
  require "fileutils"

  include Jekyll::Filters

  FileUtils.mkdir_p("tags")
  options = Jekyll.configuration({})
  site = Jekyll::Site.new(options)
  site.read_posts('')
  site.tags.sort.each do |tag, posts|
    html = ''
    html << <<-HTML
---
layout: tag
title: Posts tagged "#{tag}"
---
    <h1 id="#{tag}">Posts tagged "#{tag}"</h1>
    HTML

    html << '<ul class="posts">'
    posts.each do |post|
      post_data = post.to_liquid
      html << <<-HTML
        <li><a href="#{post.url}">#{post_data['title']}</a></li>
      HTML
    end
    html << '</ul>'

    File.open("tags/#{tag}.html", 'w+') do |file|
      file.puts html
    end
  end
  puts 'Done.'
end


task :cloud_basic do
  puts 'Generating tag cloud...'
  require 'rubygems'
  require 'jekyll'
  include Jekyll::Filters

  options = Jekyll.configuration({})
  site = Jekyll::Site.new(options)
  site.read_posts('')

  html = ''

  site.tags.sort.each do |category, posts|

    s = posts.count
    if s > 1
      font_size = 14 + (s*1.8);
      html << "<a href=\"/tags/#{category}.html\" title=\"Pages tagged #{category}\" style=\"font-size: #{font_size}px; line-height:#{font_size}px\" rel=\"tag\">#{category}</a> \n"
    end
  end

  File.open('_includes/tags.html', 'w+') do |file|
    file.puts html
  end

  puts 'Done.'
end


task :cloud do
  puts 'Generating tag cloud...'
  require 'rubygems'
  require 'jekyll'
  include Jekyll::Filters

  options = Jekyll.configuration({})
  site = Jekyll::Site.new(options)
  site.read_posts('')


  html =<<-HTML
---
layout: default
title: Tags
type: A tag cloud
---

<h1>Tag cloud for {{site.title}}</h1>

    <p>Click on a tag to see the relevant posts.</p>
  HTML

  site.categories.sort.each do |category, posts|
    html << <<-HTML
    HTML

    s = posts.count
    font_size = 12 + (s*1.5);
    html << "<a href=\"/tags/#{category}/\" title=\"Entries tagged #{category}\" style=\"font-size: #{font_size}px; line-height:#{font_size}px\">#{category}</a> "
  end



  File.open('tags/index.html', 'w+') do |file|
    file.puts html
  end

  puts 'Done.'
end
