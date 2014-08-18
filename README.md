# JoliCi

JoliCi is a free and open source Continuous Integration Client written in PHP and powered by Docker. It has been written to be easy to use.
Thanks to the use of Docker, all kind of projects can be tested with this CI (not just PHP) : you are completely free.

**This project is still in beta, there may be bugs and missing features**

[![Build Status](https://travis-ci.org/jolicode/JoliCi.png?branch=master)](https://travis-ci.org/jolicode/JoliCi) [![Scrutinizer Quality Score](https://scrutinizer-ci.com/g/jolicode/JoliCi/badges/quality-score.png?s=1ba180546468c07ca8fc0996dcdc4a740dcf23fc)](https://scrutinizer-ci.com/g/jolicode/JoliCi/)

## Features

* Support `.travis.yml` file
* Secured and isolated build on your local computer
* Multiple builds by project
* Override test command

## Usage

* [Download `jolici.phar`](https://github.com/jolicode/JoliCi/releases/download/v0.2.2/jolici.phar)
* [Add some dockerfiles](docs/strategies/JoliCiStrategy.md), skip this if you use a [.travis.yml file](docs/strategies/TravisCiStrategy.md)
* Run it under your project `php jolici.phar run`

![JoliCi Demo](https://github.com/jolicode/JoliCi/raw/master/docs/jolici-terminal.gif "JoliCi Demo")

First run can be quite long since it has to build everything from the beginning. Subsequent build should be faster thanks to docker caching.

If you want to run a different command for test instead of the one set by default (like script parameter in .travis.yml file) you just need to set the new command at the end :

```
php jolici.phar run "phpunit -c a-different-file.xml"
```

This will run `phpunit -c a-different-file.xml` for your tests.

### Run options

* --project-path : Path where your project is, default to current directory
* --docker-host : Set the API entrypoint for Docker
* -v|-vv|-vvv : Verbose, more verbose and very verbose, by default it only show the test command. By increasing verbosity you will also see the build output
* --no-cache : Do not use docker cache when building image

## Strategies

JoliCi need to know how to create builds from your project a.k.a. `BuildStrategy`. 

For the moment, only [TravisCiBuildStrategy](docs/strategies/TravisCiStrategy.md) and [JoliCiBuildStrategy](docs/strategies/JoliCiStrategy.md) are supported, but more strategy (like reading a circle.yml file) will be supported in the future.

This strategies are determined by reading your project directory.

## Install globally on unix-based systems (manual)

You can run these commands to easily access ``jolici`` from anywhere on
your system:

    $ sudo wget https://github.com/jolicode/JoliCi/releases/download/v0.2.2/jolici.phar -O /usr/local/bin/jolici

or with curl:

    $ sudo curl https://github.com/jolicode/JoliCi/releases/download/v0.2.2/jolici.phar -o /usr/local/bin/jolici

then:

    $ sudo chmod a+x /usr/local/bin/jolici

Then, just run ``jolici``.

## Requirements

* [Docker](http://docker.io) (a recent version is better and encouraged)
* PHP 5.4 at least

## Contributing

Here are a few rules to follow in order to ease code reviews, and discussions before maintainers accept and merge your work.

* You **MUST** follow the [PSR-1](http://www.php-fig.org/psr/1/) and [PSR-2](http://www.php-fig.org/psr/2/).
* You **MUST** run the test suite.
* You **MUST** write (or update) unit tests.
* You **SHOULD** write documentation.

Please, write [commit messages that make sense](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html), and [rebase your branch](http://git-scm.com/book/en/Git-Branching-Rebasing) before submitting your Pull Request.

One may ask you to [squash your commits](http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html) too. This is used to "clean" your Pull Request before merging it (we don't want commits such as `fix tests`, `fix 2`, `fix 3`, etc.).

Also, when creating your Pull Request on GitHub, you **MUST** write a description which gives the context and/or explains why you are creating it.

Thank you!

## Credits

* Some parts of this project are inspired by :
	* [Docker Client](https://github.com/dotcloud/docker/blob/master/commands.go)
* This README is heavily inspired by a @willdurand [blog post](http://williamdurand.fr/2013/07/04/on-open-sourcing-libraries/).
* [@ubermuda](https://github.com/ubermuda) for accepting many pull requests on [docker-php](https://github.com/stage1/docker-php) library

## Licence

View the [LICENCE](LICENCE) file attach to this project.
