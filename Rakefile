ROOT = File.expand_path('../', __FILE__)

trap("SIGINT") { exit! }

task :default do
  exec 'rake -T'
end

def puts_and_exec command
  puts command
  exec command
end

desc 'Build site (production)'
task :build do
  puts_and_exec 'jekyll build --config _config.yml,_config.production.yml --trace'
end

desc 'Preview and watch changes on local machine (development)'
task :preview do
  puts_and_exec 'jekyll serve --watch --trace'
end

namespace :edit do
  desc 'Start editing besides products (development)'
  task :start do
    Dir.chdir ROOT
    system "echo > _layouts/product_article.haml"
    puts_and_exec 'rake preview'
  end

  desc 'Finish editing besides products (development)'
  task :finish do
    Dir.chdir ROOT
    system "git checkout HEAD _layouts/product_article.haml"
  end
end
