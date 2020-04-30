# source 'https://rubygems.org'

# gem 'jekyll'

# group :jekyll_plugins do
#   gem 'jekyll-gist'
#   gem 'jekyll-paginate'
#   gem "jekyll-asciidoc"
# end

# gem 'asciidoctor', '~> 1.5.4'
# gem 'coderay', '1.1.1'




source "https://rubygems.org"

# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
# gem "jekyll", "~> 3.8.5"  # Uncomment this when testing locally, and comment
                            # the line with "github-pages" below.

# This is the default theme for new Jekyll sites. You may change this to anything you like.
# gem "minima", "~> 2.0"

# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
gem "github-pages", "~> 3.8.5", group: :jekyll_plugins  # Uncomment this line when
                                                        # pushing to github, and
                                                        # uncomment the above line
                                                        # with "jekyll".

# If you have any plugins, put them here!
group :jekyll_plugins do
  # gem "jekyll-feed", "~> 0.6"
  gem 'jekyll-gist'
  gem 'jekyll-paginate'
  gem "jekyll-asciidoc"
end

gem 'asciidoctor', '~> 1.5.4'
gem 'coderay', '1.1.1'

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.0" if Gem.win_platform?