source 'https://rubygems.org'

gemspec

# Add i18n support.
gem 'refinerycms-i18n', '~> 2.1.0.dev', github: 'refinery/refinerycms-i18n'

gem 'protected_attributes', github: 'rails/protected_attributes'
# Fixes uniqueness constraint on translated columns.
# See: https://github.com/svenfuchs/globalize3/pull/121
gem 'globalize3', github: 'svenfuchs/globalize3'
gem 'paper_trail', github: 'parndt/paper_trail', branch: 'rails4'
gem 'devise', '3.0.0.rc1'
gem 'awesome_nested_set', github: 'collectiveidea/awesome_nested_set'
gem 'orm_adapter', github: 'ugisozols/orm_adapter', branch: 'rails4'
gem 'database_cleaner', github: "ugisozols/database_cleaner", branch: 'rails4'
gem 'routing-filter', github: "refinery/routing-filter", branch: 'rails4'

# Database Configuration
unless ENV['TRAVIS']
  gem 'activerecord-jdbcsqlite3-adapter', platform: :jruby
  gem 'sqlite3', platform: :ruby
end

if !ENV['TRAVIS'] || ENV['DB'] == 'mysql'
  gem 'activerecord-jdbcmysql-adapter', :platform => :jruby
  gem 'jdbc-mysql', '= 5.1.13', :platform => :jruby
  gem 'mysql2', :platform => :ruby
end

if !ENV['TRAVIS'] || ENV['DB'] == 'postgresql'
  gem 'activerecord-jdbcpostgresql-adapter', :platform => :jruby
  gem 'pg', :platform => :ruby
end

gem 'jruby-openssl', platform: :jruby

group :development, :test do
  gem 'refinerycms-testing', path: '.'
end

group :test do
  gem 'generator_spec', '>= 0.8.7', github: 'stevehodgkiss/generator_spec'

  platforms :mswin, :mingw do
    gem 'win32console', '~> 1.3.0'
    gem 'rb-fchange', '~> 0.0.5'
    gem 'rb-notifu', '~> 0.0.4'
  end

  platforms :ruby do
    unless ENV['TRAVIS']
      require 'rbconfig'
      if /darwin/i === RbConfig::CONFIG['target_os']
        gem 'rb-fsevent', '~> 0.9.0'
        gem 'ruby_gntp', '~> 0.3.4'
      end
      if /linux/i === RbConfig::CONFIG['target_os']
        gem 'rb-inotify', '~> 0.8.8'
        gem 'libnotify',  '~> 0.7.2'
        gem 'therubyracer', '~> 0.10.0'
      end
    end
  end

  platforms :jruby do
    unless ENV['TRAVIS']
      require 'rbconfig'
      if /darwin/i === RbConfig::CONFIG['target_os']
        gem 'ruby_gntp', '~> 0.3.4'
      end
      if /linux/i === RbConfig::CONFIG['target_os']
        gem 'rb-inotify', '~> 0.8.8'
        gem 'libnotify',  '~> 0.7.2'
      end
    end
  end
end

# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'sass-rails', github: 'rails/sass-rails'
  gem 'coffee-rails', github: 'rails/coffee-rails'
  gem 'uglifier', '>= 1.0.3', require: false
end

gem 'jquery-rails', '~> 2.0.0'

# To use debugger
# gem 'ruby-debug', platform: :mri_18
# or in 1.9.x:
# gem 'debugger', :platform => :mri_19

# For Heroku/s3:
# gem 'fog'

# Bundle edge Rails instead:
gem 'rails', github: 'rails/rails'
if ENV['JOURNEY']
  gem 'journey', path: ENV['JOURNEY']
else
  gem 'journey', github: "rails/journey"
end

if ENV['AR_DEPRECATED_FINDERS']
  gem 'activerecord-deprecated_finders', path: ENV['AR_DEPRECATED_FINDERS']
else
  gem 'activerecord-deprecated_finders', github: 'rails/activerecord-deprecated_finders'
end

# gem 'rack', github: 'rack/rack'
# gem 'arel', github: 'rails/arel'

# Load local gems according to Refinery developer preference.
if File.exist? local_gemfile = File.expand_path('../.gemfile', __FILE__)
  eval File.read(local_gemfile)
end
