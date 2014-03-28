require 'bundler/setup'
require 'stringex'

def ask(message)
  print message
  STDIN.gets.chomp
end

desc 'Create a new post in _posts'
task :post do
  title = ask("Title: ")
  filename = "_posts/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.markdown"

  abort("File already exists!") if File.exist?(filename)

  category    = ask('Category: ')
  description = ask('Description: ')
  keywords    = ask('Keywords: ')

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

task default: :post
