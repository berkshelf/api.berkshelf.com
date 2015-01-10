# api.berkshelf.com

This repository houses the Heroku container for running api.berkshelf.com

## Configuring

1. Register for an account on Heroku
2. Setup the [Heroku Toolbelt](https://toolbelt.heroku.com)
3. Request collaborator access from [Jamie Winsor](jamie@vialstudios.com)

## Deploying

    $ git remote add heroku git@heroku.com:berkshelf-api.git
    $ heroku stack:set cedar
    $ git push heroku master

## Compiling libraries

1. Download [Vulcan](https://github.com/heroku/vulcan)
2. Make sure your Heroku account is verified
3. Setup a vulcan build server

        $ vulcan create vulcan-<your_name>

4. Download and extract the library you want to compile

        $ curl -O http://www.libarchive.org/downloads/libarchive-3.1.2.tar.gz
        $ tar xzvf libarchive-3.1.2.tar.gz

5. Build and output the library to this project

        $ vulcan build -s ./libarchive-3.1.2

6. Download the archive containing the compiled library in the URL returned
7. Extract the contents of the archive into a sub directory of the `vendor` directory in this project

## Making compiled libraries available

Add the lib path to LD_LIBRARY_PATH

    $ heroku config:add LD_LIBRARY_PATH=/app/vendor/libarchive-3.1/lib

Check the previous config to make sure you are building the path and not destroying what is already there

    $ heroku config
    === berkshelf-api Config Vars
    LD_LIBRARY_PATH: /app/vendor/libarchive-3.1/lib

# Authors

* Jamie Winsor (<jamie@vialstudios.com>)
