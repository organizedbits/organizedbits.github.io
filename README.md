# organizedbits.github.io

# Initialize BundlerPermalink
mkdir my-jekyll-website
cd my-jekyll-website
bundle init

# Configure Bundler
bundle install --path vendor/bundle

# Add JekyllPermalink
bundle add jekyll

# Create A Jekyll ScaffoldPermalink
bundle exec jekyll new --force --skip-bundle .
bundle install

# bundle exec jekyll serve
bundle exec jekyll serve --watch

bundle exec jekyll serve --watch --incremental --config _config.yml,_config_dev.yml

http://127.0.0.1:4000


