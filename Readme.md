
## Installation

If you want to use it you will need a server who can execute php 8+ and a mysql database.

1.- Execute the script hosted at extras/script.sql in your database. Remember to use utf8.  
2.- Download all the files and add those to the server.  
3.- Edit the wp-config.php with the credentials of your database.  
4.- Run the next script in the database:  

```
update wp_options set option_value = <myurl> 
where option_name = "siteurl" or option_name = "home"
```

    
