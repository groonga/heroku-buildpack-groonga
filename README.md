# Heroku buildpack: groonga

This is a Heroku buildpack of groonga(http://groonga.org/).

## Usage:

    heroku create --stack cedar --buildpack https://github.com/groonga/heroku-buildpack-groonga.git

Create `data.grn` on the root of your project and push it to heroku.

    git push heroku master
