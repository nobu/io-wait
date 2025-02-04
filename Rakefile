require "bundler/gem_tasks"
require "rake/testtask"

name = "io/wait"

case
when RUBY_ENGINE == "jruby"
  require 'rake/javaextensiontask'
  Rake::JavaExtensionTask.new("wait") do |ext|
    require 'maven/ruby/maven'
    ext.source_version = '1.8'
    ext.target_version = '1.8'
    ext.ext_dir = 'ext/java'
    ext.lib_dir = 'lib/io'
  end
  task "build" => "lib/io/wait.jar"
  task "lib/io/wait.jar" => "compile"
  libs = ["ext/java/lib", "lib"]
when RUBY_VERSION < "2.6"
  task :compile do
    # noop
  end

  libs = []
else
  require "ruby-core/extensiontask"
  libs = RubyCore::ExtensionTask.new(Bundler::GemHelper.instance.gemspec).libs
end

Rake::TestTask.new(:test) do |t|
  t.libs = libs
  t.libs << "test/lib"
  t.ruby_opts << "-rhelper"
  t.test_files = FileList["test/**/test_*.rb"]
end

task :test => :compile

task :default => :test
