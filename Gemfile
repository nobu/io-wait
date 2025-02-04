source 'https://rubygems.org'

# Specify your gem's dependencies in io-wait.gemspec
gemspec

group :development do
  gem "rake"
  gem "test-unit"
  gem "test-unit-ruby-core"
  gem "ruby-core-tasks", platforms: :mri, github: "ruby/ruby-core-tasks" if RUBY_ENGINE == "ruby"
  gem "rake-compiler", platforms: :jruby
  gem "ruby-maven", platforms: :jruby
end
