# Travis Integration for Redmine Plugins

The goal of this project is to provide [Travis](https://travis-ci.org) support for any [Redmine](http://www.redmine.org) plugin author.

The assumption here is that your plugin will be using the standard Rails tests that derive from [ActionController::TestCase](http://api.rubyonrails.org/classes/ActionController/TestCase.html) and [ActiveSupport::TestCase](http://api.rubyonrails.org/classes/ActiveSupport/TestCase.html).

Other testing infrastructures can be used, but the ``run_tests()`` function of the ``.travis-init.sh`` file would need to be adapted.

## Prerequisites

In order to take advantage of the [Travis](https://travis-ci.org) continuous integration service, you'll need to have your plugin hosted on [Github](https://github.com).

## Installation

1. Copy the ``.travis.*`` files to the root of your plugin.
2. Edit the ``.travis.yml`` file and update the PLUGIN export with your plugin name
3. Commit the updates to your repository and push to Github
4. Register your project with Travis (see their [Getting Started](http://about.travis-ci.org/docs/user/getting-started/) guide for more info)

## Configuration

Other than providing your plugin name in the ``.travis.yml`` file, all other configuration is standard Travis configuration.


## Acknowlegements

The configuration and scripts were extracted and modified from work done by the authors of the [Redmine Backlogs](https://github.com/backlogs/redmine_backlogs) project. None of this would be possible without their original efforts, so big ups from me to them!