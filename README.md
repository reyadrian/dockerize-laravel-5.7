
# docker-laravel-5.7
Dockerize Laravel Setup

## What's inside?
* Nginx,
* PHP 7.2.2-fpm,
* composer,
* MySQL 5.7.2,
* Laravel 5.7.15

## Installation

Steps:

1. Install [Docker Toolbox](https://docs.docker.com/toolbox/overview/) or [Docker Community Edition](https://store.docker.com/search?type=edition&offering=community) 

   * **Windows 10: Install [Docker Toolbox Windows](https://docs.docker.com/docker-for-windows/)**

   * **Mac: Yosemite 10.10.3 or above Install [Docker Community Edition for Mac](https://store.docker.com/editions/community/docker-ce-desktop-mac); otherwise, Install [Docker Toolbox for Mac](https://docs.docker.com/docker-for-mac/)**



2. Once you installed the Docker, please run this codes:

```
   docker pull reyadrian/laravel5.7:app
   docker pull reyadrian/laravel5.7:web
   docker pull reyadrian/laravel5.7:mysql
```
   *You can now see the existing docker images*
   
   ![](/docker-images-view.png)   
  
3. Create a directory for the laravel application (this will be the directory for the laravel files)

4. Unzip or clone laravel repo inside your newly created folder.
```
    curl -L https://github.com/laravel/laravel/archive/v5.7.15.tar.gz | tar xz
```    

OR
  
```   
    git clone https://github.com/laravel/laravel.git --branch v5.7.15
```

5. Should execute this code inside the laravel folder root where you find the _composer.json_. 
```  
docker run --rm -v $(pwd):/app composer install
```
   *composer install will pull in all of the libraries that make up Laravel (all the vendors)*

6. Download [docker-compose.yml](/docker-compose.yml) and put it inside your laravel folder.
Then update this content:
```
   - /c/Users/dondo/Projects/mydocker/mysqldata:/var/lib/mysql
```

  Update to (*this is for persistent data for the mysql*):
```
   - [path to where you want your mysql data to be put]:/var/lib/mysql
```

7. RUN
```
   docker-compose up
```

8. Update the laravel ENVIRONMENT CONFIGURATION. _Rename .env.example to .env_

  Change the **DB_HOST=192.168.99.100**


9. RUN
```
   docker-compose exec app php artisan key:generate
   docker-compose exec app php artisan optimize
```

##
## THAT'S IT!

# Go RUN it in you browser http://192.168.99.100:80
##

▁ ▂ ▄ ▅ ▆ ▇ █ ĂĎŔĨĂŃ █ ▇ ▆ ▅ ▄ ▂ ▁



## References & Links: 
* Docker Images [https://hub.docker.com/r/reyadrian/laravel5.7/](https://hub.docker.com/r/reyadrian/laravel5.7/)
   * reyadrian/laravel5.7:app -> (php & mysql connection)
   * reyadrian/laravel5.7:web -> (nginx setup)
* This setup is based on [https://medium.com/@shakyShane/laravel-docker-part-1-setup-for-development-e3daaefaf3c](https://medium.com/@shakyShane/laravel-docker-part-1-setup-for-development-e3daaefaf3c)
   * Just change the version from php7.0.4-fpm and MySQL 5.6

