require 'rubygems'
require 'bundler/setup'
require 'stringex'

desc 'create a new post in _posts'
task :post, :title do |t, args|
  title = args.title
  filename = "_posts/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.markdown"
  if File.exist?(filename)
    abort("File already exists!")
  end
  category = ask('Category: ')
  description = ask('Description: ')
  keywords = ask('Keywords: ')
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts '---'
    post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
    post.puts "description: #{description}"
    post.puts "keywords: #{keywords}"
    post.puts "category: #{category}"
    post.puts 'layout: blog'
    post.puts '---'
  end
end

def ask(message)
  print message
  STDIN.gets.chomp
end
