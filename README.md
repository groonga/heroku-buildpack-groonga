# Heroku buildpack: groonga

This is a Heroku buildpack of [groonga](http://groonga.org/).

## Usage:

    heroku create --stack cedar --buildpack https://github.com/groonga/heroku-buildpack-groonga.git

Create `groonga` on the root of your project and place `*.grn` files in the directory.
`*.grn` files will be loaded in the dictionary order of their file names.

    mkdir -p groonga
    vi groonga/0.grn
    vi groonga/1.grn

Then push them to heroku.

    git push heroku master
