# Experimenting with Composer, Version control, Configuration management, and Paragraphs

I have used the drupal-composer/drupal-project template to build this project.
I'm (obviously) using Git for version control.
I'm using paragraphs to define structured data for "components" of a web page.
I have built a simple custom theme to render the paragraph components.
The theme is hosted on github and is managed with my composer configuration.
I'm keeping track of all of my site building with configuration management.

## Usage

First you need to [install git ](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [install composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx).

After that you can create the project:

```
git clone https://github.com/vegantriathlete/drupal-composer.git
cd drupal-composer
```

In order to use configuration management, you'll need to build your site
with the same database as I've built the site. I have included a database
backup at /database/drupal_composer.tar.gz. Import this database into
your database server.

I have committed a settings.php that looks for settings.local.php. You will
need to create your own settings.local.php and specify your database
credentials as well as the hash salt. You might also want to define your
trusted hosts. Here is an example of the information you might use.
You *do* want to use the exact same hash salt as I have specified.
You will need to modify the trusted host and database credentials
to match your own environment.

```
<?php

// @codingStandardsIgnoreFile

/**
 * @file
 * Local development override configuration feature.
 *
 * For more options you might wish to set see
 * web/sites/example.settings.local.php.
 */

$settings['hash_salt'] = 'dJNE4KCEspkO-trVXzEAg4QMYNufhXe0XVIUP-FEm13r9_AAJbNJOT4UKs6dfd9R_I4arxh9og';

$settings['trusted_host_patterns'] = [
  '^drupal-composer$',
];
$databases['default']['default'] = array (
  'database' => 'drupal_composer',
  'username' => 'marc',
  'password' => 'marc',
  'prefix' => '',
  'host' => 'localhost',
  'port' => '3306',
  'namespace' => 'Drupal\\Core\\Database\\Driver\\mysql',
  'driver' => 'mysql',
);
```

## Logging in to the site

The database backup has just the user 1 account.

username: drupal

password: drupal

## Updating to the latest version of this project

I will apply all updates to the master branch only.

Follow the steps below to update the project.

1. cd into the project
1. Run `git checkout master`
1. Run `git fetch origin`
1. Run `git merge origin/master`

## Updating your site
1. Ensure you have first udpated to the latest version of this project
1. Run `composer update`
1. Run `drush cim`
1. Run `drush cr`
