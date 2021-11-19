### Notice: Make sure that the permission of ./etc/mysql/my.cnf is 0444
`chmod 0444 my.cnf`

## How to use?  
### Precondition:
Install docker and docker-compose by yourself.

### One site on production (recomendation):
1. Copy docker-compose-example.yml to docker-compose.yml
1. Put your site and rename to ./html
1. Run `docker-compose up -d`
1. visit your site by server IP + nginx port (Local development is 127.0.0.1).

### Multi site in the environment:
1. Copy docker-compose-example.yml to docker-compose.yml
1. Change `- ./html:/var/www/html` to `- ./www:/var/www`
1. Run `docker-compose up -d`
1. Put your drupal code to www, like www/drupalsitea, www/drupalsiteb  
    **Optional ( Use composer to download a new site ):**  
    Run `docker exec -it d9 bash` to get into the php/nginx container,   
    Swich to /var/www `cd /var/www`,  
    Then use composer to create a new drupal site  `composer create-project drupal/recommended-project my_site_name_dir`
1. The d9 container has a nginx config to direct <directory_name>.dpw /var/www/directory_name, so you can visit your site by drupalsitea.dpw, drupalsiteb.dpw after put it to your composer's hosts(Linux/Mac: /etc/hosts).
