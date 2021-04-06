# Wordpress Petshop Demo

Due to the nature of wordpress it doesn't make sense to put the entire codebase on github.
I have added the wp-content folder so that code for themeing and custom plugins can be used. I have also included a pdf with some screenshots of the functionality TODO.

To see the site live please use this link: http://pet-shop-demo.onlinewebshop.net/ 

Below is instructions on how to run localy with Docker and a backup image of the site.

## How to run local dev with Docker

### First time run on Ubuntu

Note due to local dev on a Debian machine there will be some issues with user permissions from the containers and the local Debian fs. A workaround for accessing the WP files:

`sudo userdel www-data`
`sudo useradd -u 33 www-data`

Note don't do this if you have a local server in use such as Apache2 (Ubuntu default).

Start the containers:

`docker-compose up -d`

access at `http://localhost:8080`

### To install the site

Install the plugin: All-In-One WP Migration (must be older version 6.7)

Update the .htaccess file to increase the maximum upload size so we can use the backup file. (.htaccess is located in the wordpress folder).

Append the following:
```

php_value upload_max_filesize 128M
php_value post_max_size 128M
php_value memory_limit 256M
php_value max_execution_time 300
php_value max_input_time 300

```

Now activate the plugin in the WP dashboard and import the backup (.wpress) located in `wp-content/ai1wm-backups`

### Login details

Username: `jack`

Password: `dig31#jeLUNAR`

# .gitignore 

Mainly for my own reference:

```

# ignore everything (dirs, files, sub-dirs, sub-files) 
/*
# but do not ignore the following in root dir
!.gitignore
!screenshots.pdf
!readme.md
!docker-compose.yml

# do not ignore wp-content directory
!wordpress/
wordpress/*
!wordpress/wp-content/

```
