begin
  require 'bundler/setup'
rescue LoadError
  puts 'You must `gem install bundler` and `bundle install` to run rake tasks'
end

begin
  require 'rdoc/task'

  RDoc::Task.new(:rdoc) do |rdoc|
    rdoc.rdoc_dir = 'rdoc'
    rdoc.title    = 'CodeNotes'
    rdoc.options << '--line-numbers'
    rdoc.rdoc_files.include('README.md')
    rdoc.rdoc_files.include('lib/**/*.rb')
  end
rescue LoadError, StandardError => e
  warn "Setting up rdoc failed #{e.class}: #{e.message}: #{__FILE__}:#{__LINE__}"
end



Bundler::GemHelper.install_tasks

require 'rake/testtask'
require 'code_notes'

Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.libs << 'test'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = false
end


task default: :test
