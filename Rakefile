require 'bundler/setup'
require 'stringex'
require 'fileutils'

def ask(message)
  print message
  STDIN.gets.chomp
end

desc 'Create a new post in _draft'
task :draft do
  title = ask("Title: ")
  filename = "_drafts/#{title.to_url}.markdown"

  abort("File already exists!") if File.exist?(filename)

  description = ask('Description: ')
  keywords    = ask('Keywords: ')

  open(filename, 'w') do |post|
    post.puts '---'
    post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
    post.puts "description: #{description}"
    post.puts "keywords: #{keywords}"
    post.puts 'layout: articles'
    post.puts '---'
  end
end

desc 'Publish posts in _draft'
task :publish do
  title = ask("Title: ")
  Dir.glob("_drafts/*") do |post|
    if post =~ /#{title}/ && ask("Publish #{post}? ") =~ /Y(es)?/i
      FileUtils.mv(post, "_posts/#{Time.now.strftime('%Y-%m-%d')}-#{File.basename post}")
    end
  end
end

task default: :draft
