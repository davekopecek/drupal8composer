# Docksal powered Drupal 8 Composer Installation

This is a sample vanilla Drupal 8 installation using drupal-composer/drupal-project:8.x-dev pre-configured for use with Docksal.

Features:

- Vanilla Drupal 8
- `fin init` example

## Setup instructions

### Step #1: Docksal environment setup

**This is a one time setup - skip this if you already have a working Docksal environment.**

Follow [Docksal environment setup instructions](http://docksal.readthedocs.io/en/master/getting-started/env-setup)

### Step #2: Project setup

1. Clone this repo into your Projects directory

    ```
    git clone git@github.com:davekopecek/drupal8composer.git
    cd drupal8composer
    ```

2. Initialize the site

    This will initialize local settings and install the site via drush

    ```
    fin init
    ```

3. **On Windows** add `192.168.64.100  drupal8.docksal` to your hosts file

4. Point your browser to

    ```
    http://drupal8.docksal
    ```

When the automated install is complete the command line output will display the admin username and password.

## Composer Speed-up and Caching

Composer tweaks:

1. Uses [prestissimo composer](https://github.com/hirak/prestissimo) parallel install plugin
2. Mounts cli container cache direcory to persistent docker volume. Cached composer files will survive `fin reset`

Volume created with `fin docker volume create composer-cache`
Volume mapped in docksal-local.yml with:

    ```
    cli:
      volumes:
      - composer-cache:/home/docker/.composer/cache
    ```
