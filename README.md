# Travis Integration for Redmine Plugins

The goal of this project is to provide [Travis](https://travis-ci.org) support for any [Redmine](http://www.redmine.org) plugin author.

The assumption here is that your plugin will be using the standard Rails tests that derive from [ActionController::TestCase](http://api.rubyonrails.org/classes/ActionController/TestCase.html) and [ActiveSupport::TestCase](http://api.rubyonrails.org/classes/ActiveSupport/TestCase.html).

Other testing infrastructures can be used, but the ``run_tests()`` function of the ``.travis-init.sh`` file would need to be adapted.

## Prerequisites

In order to take advantage of the [Travis](https://travis-ci.org) continuous integration service, you'll need to have your plugin hosted on [Github](https://github.com).

## Installation

1. Copy the ``.travis*`` files to the root of your plugin.
2. Edit the ``.travis.yml`` file and update the PLUGIN export with your plugin name
3. Commit the updates to your repository and push to Github
4. Register your project with Travis (see their [Getting Started](http://about.travis-ci.org/docs/user/getting-started/) guide for more info)

## Configuration

An annotated sample is provided below to help get everything up and running.

``` yml
language: ruby          # has to be ruby, as Redmine is a Ruby on Rails application ;)
rvm:
  - 2.0.0               # versions of ruby to test against
  - 1.9.3
branches:               # if we're building against something other than the master
  only:                 # branch on Github
    - testing
env:
  - REDMINE_VERSION=2.3.3 VERBOSE=yes      # The version of redmine to use when testing
script:
  - export PLUGIN=<add plugin name here>   # The name of the plugin that we're testing
  - export WORKSPACE=$(pwd)/workspace
  - export PATH_TO_PLUGIN=$(pwd)
  - export PATH_TO_REDMINE=$WORKSPACE/redmine
  - mkdir $WORKSPACE
  - bash -x ./.travis-init.sh -r || exit 1
  - bash -x ./.travis-init.sh -i || exit 1
  - bash -x ./.travis-init.sh -t || exit 1
  - bash -x ./.travis-init.sh -u || exit 1
```

See the Travis CI configuration guide for more advanced options.


## Acknowlegements

The configuration and scripts were extracted and modified from work done by the authors of the [Redmine Backlogs](https://github.com/backlogs/redmine_backlogs) project. None of this would be possible without their original efforts, so big ups from me to them!

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/alexbevi/redmine_plugins_travis-ci/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

