require 'rake/clean'
require 'rake/testtask'
require 'fileutils'

require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "sinatra-formhelpers"
    gem.summary = %Q{use basic form helpers for generic form management}
    gem.email = "tom@jackrussellsoftware.com"
    gem.homepage = "http://github.com/twilson63/sinatra-formhelpers"
    gem.authors = ["twilson63"]
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
    gem.add_runtime_dependency 'sinatra', ['>= 0.9.2.0']
    gem.add_runtime_dependency 'activesupport', ['>= 2.3.2.0']
    
    
  end
  
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

task :spec => :test

# SPECS ===============================================================

Rake::TestTask.new(:test) do |t|
  t.test_files = FileList['test/*_test.rb']
  t.ruby_opts = ['-rubygems'] if defined? Gem
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/*_test.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end


task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML.load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end
  
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "test-gem #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end



