## Building Documentation Site Locally
To update and view changes locally on your computer:
1. Ensure you have all the [prerequisites installed](https://jekyllrb.com/docs/installation/#requirements)
2. Clone this repository to your machine.
3. Configure bundler to load gems locally:

   `bundle config set --local path vendor/bundle`

4. Run Bundle install:

   `bundle install`

5. Build the site and make it available on a locally at http://localhost:4000

   `bundle exec jekyll serve --livereload`
