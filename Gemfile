source ENV['GEM_SOURCE'] || 'https://rubygems.org'

def location_for(place)
  if place =~ /^((?:git[:@]|https:)[^#]*)#(.*)/
    [{ git: Regexp.last_match(1), branch: Regexp.last_match(2), require: false }]
  elsif place =~ %r{^file://(.*)}
    ['>= 0', { path: File.expand_path(Regexp.last_match(1)), require: false }]
  else
    [place, { require: false }]
  end
end

gem 'artifactory'
gem 'json'
gem 'octokit'
gem 'packaging', *location_for(ENV['PACKAGING_LOCATION'] || '~> 0.99.43')
gem 'rake'
gem 'rubocop'
gem 'vanagon', *location_for(ENV['VANAGON_LOCATION'] || '~> 0.15.17')

eval_gemfile("#{__FILE__}.local") if File.exist?("#{__FILE__}.local")
