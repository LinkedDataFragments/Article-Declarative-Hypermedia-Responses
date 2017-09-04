source 'https://rubygems.org'

gem 'nanoc', '~> 4.7'

# text processing
gem 'kramdown'
gem 'rubypants'

# stylesheets
gem 'sass'

# references
gem 'i18n'
gem 'bibtex-ruby'
gem 'latex-decode'
gem 'citeproc-ruby', '>= 1.1.6'
gem 'csl-styles'
gem 'bibmarkdown', '~> 1.2.1'

group :development do
  # live view
  gem 'guard-nanoc', '~> 2.1.2'
  gem 'guard-process'
  gem 'guard-livereload'
  gem 'serve'
  gem 'thin'
  gem 'rack-livereload'
  gem 'wdm', '>= 0.1.0' if Gem.win_platform?
  gem 'rb-readline'
end

group :test do
  # validation
  gem 'w3c_validators', '~> 1.3.1'
end
