# docker-laravel-5.7

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

   * **Mac: Yosemite 10.10.3 or above Install [Docker Community Edition for Mac](https://store.docker.com/editions/community/docker-ce-desktop-mac) otherwise, Install [Docker Toolbox for Mac](https://docs.docker.com/docker-for-mac/)**



2. Once you installed the Docker, please run this code

```
   docker pull reyadrian/laravel5.7:app
   docker pull reyadrian/laravel5.7:web
   docker pull reyadrian/laravel5.7:mysql
```
   ![Image of docker view](/docker-images-view.png)   
  
3. Create a directory/folder for the laravel application (this will be the directory for the laravel files)

4. Unzip or clone laravel repo inside your newly created folder.
```
    curl -L https://github.com/laravel/laravel/archive/v5.7.15.tar.gz | tar xz
```    
    OR
```   
    git clone https://github.com/laravel/laravel.git --branch v5.7.15
```

5. When executing this, YOu should be inside the laravel folder root:
```  
docker run --rm -v $(pwd):/app composer install
```

6. Download docker-compose.yml and put it inside your laravel folder.
Then update the content inside accordingly:

  Original
```
   - /c/Users/dondo/Projects/mydocker/mysqldata:/var/lib/mysql
```

  Update to
```
   - [path to your mysql data here]:/var/lib/mysql
```


RUN
```
   docker-compose up
```
