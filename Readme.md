# Hubspot challenger in WP

Here's a wordpress site that uses a hubsport form integration. If you want to see a live demo [click here](http://hubspotchallenge.jessicaviajes.esy.es/challenge/):

## Installation

First of all, you will need an environment that supports php 7.4.21 and mysql. You can use tools like [XAMP](https://www.apachefriends.org/es/index.html) for this purpose.

- Download this repository to the server location where you will host your site
- Create an empty database (it should be utf8_general_ci) that will be used to store the wordpress site data
- In your database, run the script hosted at /extras/script.sql
- Edit the /wp-config.php file in order to replace the credentials with those of your database (DB_NAME, DB_USER, DB_PASSWORD).
```sh
/** The name of the database for WordPress */
define( 'DB_NAME', 'my_db' );

/** MySQL database username */
define( 'DB_USER', 'my_user' );

/** MySQL database password */
define( 'DB_PASSWORD', 'my_password' );
```
- Finally replace the base URL in the database, running this script (don't forget to replace 'YOUR_URL' by your url site):
```sh
UPDATE wp_options SET option_value = replace(option_value, 'http://localhost:8888/hubspot2', 'YOUR_URL') WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET guid = replace(guid, 'http://localhost:8888/hubspot2', 'YOUR_URL');
UPDATE wp_posts SET post_content = replace(post_content, 'http://localhost:8888/hubspot2', 'YOUR_URL'); 
UPDATE wp_postmeta SET meta_value = replace(meta_value,'http://localhost:8888/hubspot2', 'YOUR_URL');
```

You can now see the hubspot integration in your browser at: YOUR_URL/challenge

> :warning: WARNING: The page structure is done with Elementor and sometimes only on fresh installs some pages might return 404. To solve this problem you need to deactivate the Elementor plugin and then activate it, this will be only one time. You can do this through the dashboard. Here's how to enter the wordpress dashboard.

## Dashboard

If you want to access the WordPress dashboard, you can do it through YOUR_URL/wp-admin using these credentials:

```sh
admin
admin2o2i_bright
```

If you want to manage plugins you can do it in YOUR_URL/wp-admin/plugins.php

THANK YOU, and enjoy the road.
