<!-- Complete this Manual -->

# Wordpress 

## Steps:

1. Create a folder for wordpress application 
    - `$> mkdir wordApp`
2. Move to the new directory
    - `$> cd wordApp`
3. Create a docker compose file named `compose.yaml` inside the directory.
4. Use this script
    ```
    version: '3'
    services:
    db:
        image: mysql:5.7
        volumes:
        - db_data:/var/lib/mysql
        restart: always
        environment:
        MYSQL_ROOT_PASSWORD: your_mysql_root_password
        MYSQL_DATABASE: wordpress
        MYSQL_USER: wordpress
        MYSQL_PASSWORD: your_mysql_password

    wordpress:
        depends_on:
        - db
        image: wordpress:latest
        ports:
        - 8000:80
        restart: always
        environment:
        WORDPRESS_DB_HOST: db:3306
        WORDPRESS_DB_USER: wordpress
        WORDPRESS_DB_PASSWORD: your_mysql_password
    volumes:
    db_data: {}
    ```
5. Make sure the indentation is correct(2 spaces).
6. Run the command `$wordApp> docker compose up`