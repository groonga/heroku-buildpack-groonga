# Heroku buildpack: Groonga

This is a Heroku buildpack of [Groonga](http://groonga.org/).

## Usage:

    heroku create --buildpack https://codon-buildpacks.s3.amazonaws.com/buildpacks/groonga/groonga.tgz

Create `groonga` directory on the root of your project and place `*.grn` files in the directory.
`*.grn` files will be loaded in the dictionary order of their file names.

    mkdir -p groonga
    vi groonga/0-schema.grn
    vi groonga/1-data.grn
    vi groonga/9-indexes.grn

Then push them to Heroku.

    git push heroku master

## Environment variables

You can use the following environment variables:

  * `GROONGA_BASE_PATH`: The directory path to be placed Groogna
    related files such as database. You can use the directory to put
    Groonga related files.
  * `GROONGA_DATABASE_PATH`: The Groonga database path for your
    application. The path exists under `GROONGA_BASE_PATH` directory.
