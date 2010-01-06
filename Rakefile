require "rubygems"
require "rake"
require "spec/rake/spectask"
require "spec/rake/verify_rcov"
require "rake/rdoctask"

task :default => :spec_verify_rcov

Spec::Rake::SpecTask.new do |spec|
  spec.spec_files = FileList["spec/**/*_spec.rb"]
  spec.spec_opts << "--color"
  spec.libs += ["lib", "spec"]
  spec.rcov = true
  spec.rcov_dir = "rcov"
end

RCov::VerifyTask.new(:spec_verify_rcov => :spec) do |verify|
  verify.threshold = 100.0
  verify.index_html = "rcov/index.html"
end

Rake::RDocTask.new do |rdoc|
  rdoc.title = "Savon"
  rdoc.rdoc_dir = "rdoc"
  rdoc.rdoc_files.include("lib/**/*.rb")
  rdoc.options = ["--line-numbers", "--inline-source"]
end

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gemspec|
    gemspec.name = "savon"
    gemspec.summary = "Heavy metal Ruby SOAP client library"
    gemspec.description = ""
    gemspec.email = "me@rubiii.com"
    gemspec.homepage = "http://github.com/rubiii/savon"
    gemspec.authors = ["Daniel Harrington"]
    gemspec.version = "0.6.8"
    gemspec.date = "2010-01-01"


    gemspec.files = FileList["[A-Z]*", "{lib,spec}/**/*.{rb,xml}"]
    gemspec.test_files = FileList["spec/**/*.rb"]

    gemspec.extra_rdoc_files = ["README.textile"]
    gemspec.rdoc_options = ["--charset=UTF-8", "--title", "Savon", "--line-numbers", "--inline-source"]

    gemspec.add_dependency "builder", ">= 2.1.2"
    gemspec.add_dependency "crack", ">= 0.1.4"

    gemspec.add_development_dependency "rspec", ">= 1.2.8"
    gemspec.add_development_dependency "mocha", ">= 0.9.7"
    gemspec.add_development_dependency "fakeweb", ">= 1.2.7"
    
  end
rescue LoadError
  puts "Jeweler not available. Install it with: gem install jeweler"
end