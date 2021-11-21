# Hubspot challenger in WP

Here is a wordpress site that uses a hubsport form integration. If you want to watch a live demo, you can in this link:
http://hubspotchallenge.jessicaviajes.esy.es/challenge/

## Installation

First at all, you will need an environment for php 7.4.21 support and mysql. You can use tools like LAMP for these propose.

- Download this repo at the folder location that you will host your site.
- Create an empty database (it should be utf8_general_ci) who will be used to store the data for the wordpress site.
- In your database run the script that is in /extras/script.sql in the repo you have downloaded.
- Edit the /wp-config.php file and replace the credentials with those from your database (DB_NAME, DB_USER, DB_PASSWORD).
```sh
/** The name of the database for WordPress */
define( 'DB_NAME', 'my_db' );

/** MySQL database username */
define( 'DB_USER', 'my_user' );

/** MySQL database password */
define( 'DB_PASSWORD', 'my_password' );
```
- Finally replace the base url in the database, executing these script in your db:
```sh
UPDATE wp_options SET option_value = replace(option_value, 'http://localhost:8888/hubspot2', 'YOUR_URL') WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET guid = replace(guid, 'http://localhost:8888/hubspot2', 'YOUR_URL');
UPDATE wp_posts SET post_content = replace(post_content, 'http://localhost:8888/hubspot2', 'YOUR_URL'); 
UPDATE wp_postmeta SET meta_value = replace(meta_value,'http://localhost:8888/hubspot2', 'YOUR_URL');
```

Now you can watch the hubspot integration in your browset at: YOUR_URL/challenge

> :warning: WARNING: The structure of the page is done with Elementor, and sometimes only in fresh installations, it could retrieve 404. To solve these issue you should unactivate and then activate the elementor plugin just once. You could do these throught the dashboard. In the next session you will know how to access it.

## Dashboard

If you want to access the wordpress dashboard, you can do it throught YOUR_URL/wp-admin using these credentials:

```sh
admin
admin2o2i_bright
```

If you want to manage the plugins, you could do these at YOUR_URL/wp-admin/plugins.php

THANKS, and enjoy the road.
