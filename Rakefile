require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "em-s3"
    gem.summary = %Q{Extremely fast, parallelizable, function-based Amazon S3 calls with EventMachine}
    gem.description = %Q{em-s3 provides a lightweight wrapper around Amazon's S3 API for EventMachine-based applications. It's a utility library written for speed and high concurrency: MD5 and signature calculations are deferred, the HTTP connections use file streaming, and Nokogiri is used to parse the XML responses.  It is _not_ an abstraction layer, and it isn't object-oriented; you can set certain constants at the module level, but there are no Bucket or Item objects to be constructed on every request. You simply call functions, which mostly mirror those exposed by Amazon's S3 REST API. The intent is that developers will build richer, more intelligent layers on top of em-s3.}
    gem.email = "sfeley@gmail.com"
    gem.homepage = "http://github.com/SFEley/em-s3"
    gem.authors = ["Stephen Eley"]
    gem.add_development_dependency "rspec", ">= 1.2.9"
    gem.add_development_dependency "yard", ">= 0"
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.spec_files = FileList['spec/**/*_spec.rb']
end

Spec::Rake::SpecTask.new(:rcov) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :spec => :check_dependencies

task :default => :spec

begin
  require 'yard'
  YARD::Rake::YardocTask.new
rescue LoadError
  task :yardoc do
    abort "YARD is not available. In order to run yardoc, you must: sudo gem install yard"
  end
end
