# WP-Composer

Installs most recent version of wordpresss with with some initial plugins and settings for the rapid deployment of wordpress projects.

## How to

    composer install

# Plugins:



Adds the following plugins:

- Advanced Custom Fields
- Contact form 7
- Google Analytics for Wordpress (Yoast)
- Google XML Sitemap
- W3 Cache
- Wordpress SEO (Yoast)

# More Examples

## No plugins or themes

    {
      "repositories": [
        {
          "type": "composer",
          "url": "http://wpackagist.org"
        },
        {
          "type": "package",
          "package": {
            "name": "wordpress/wordpress",
            "type": "webroot",
            "version": "4.1",
            "source": {
              "type": "git",
              "url": "https://github.com/WordPress/WordPress.git",
              "reference": "4.1"
            },
            "require": {
              "fancyguy/webroot-installer": "1.0.0"
            }
          }
        }
      ],
      "require": {
        "php": ">=5.3.0",
        "wordpress/wordpress": ">=4.1"
      },
      "extra": {
        "installer-paths": {
            "public_html/wp-content/themes/{$name}/": ["type:wordpress-theme"],
            "public_html/wp-content/plugins/{$name}/": ["type:wordpress-plugin"]
        },
        "webroot-dir": "public_html/wp",
        "webroot-package": "wordpress/wordpress"
      },
      "scripts": {
          "post-install-cmd": [
            "cp public_html/wp-config-sample.php public_html/wp-config.php"
          ]
      }
    }


## How to add themes using a github zip

    {
      "type": "package",
      "package": {
        "name": "roots/roots-sass",
        "type": "wordpress-theme",
        "version": "7.0.0",
        "dist": {
          "type": "zip",
          "url": "https://github.com/roots/roots-sass/archive/7.0.0.zip"
        },
        "require": {
          "composer/installers": "~1.0"
        }
      }
    }


## How to add from from private bitbucket

        {
        "require": {
            "username/reponame": "dev-master"
        },
        "repositories": [
            {
                "type": "vcs",
                "url":  "git@bitbucket.org:username/reponame.git"
            }
        ]
    }

## How to add from from git

    {
      "type": "package",
      "package": {
          "name": "username/theme-name",
          "version": "dev-master",
          "source": {
              "url": "git@bitbucket.org:username/theme-name.git",
              "type": "git",
              "reference": "origin/master"
          }
      }
    }

#### Installing composer:

using Brew:

    brew update
    brew tap homebrew/homebrew-php
    brew tap homebrew/dupes
    brew tap homebrew/versions
    brew install php55-intl php55-mcrypt
    brew install homebrew/php/composer
