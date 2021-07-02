# Twill - CodeSpaces

Inspired by `microsoft/vscode-remote-try-php` template, you can use the .devcontainer files to start a Twill project into GitHub CodeSpaces.

## Instructions for generating the Codespace
1. Copy .devcontainer folder to your project root
1. Push to repo
1. Access repo GitHub page, open in CodeSpaces
1. Container should build and IDE should open ready for use

2. Create a `.env` file from the example.
```bash
    cp .env.example .env
```
3. Add the DB env variables to the following to use the MariaDB docker container
```env
DB_CONNECTION=mysql
DB_HOST=mariadb
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=secret
```

4. Install the packages
```bash
    composer install
```

5. Generate Key. Migrate DB structure and create Twill superadmin
```bash
    php artisan key:generate
    php artisan migrate
    php artisan twill:superadmin
```

6. Build the FE. Assuming NPM by default. Adjust it to your needs if you are using yarn or anything else.
```bash
    npm install
    npm run dev
```

# Accesing the Site.
1. In order to access the site use the alias
```bash
    serve
```
or port forwarding by serving the application with
```bash
    php artisan serve --port=8000 --host=0.0.0.0
```


## Notes
- CodeSpaces is currently in Closed Beta, you need access to use .devcontainer files
- Includes the following PHP extensions, you can add your own by adjusting the DOCKERFILE
    - bcmath mysqli pdo pdo_mysql zip
- To access your site you need to run the following alias:
    ```php
    serve
    ```

# Dockerfile and devcontainer.json based on:
https://github.com/PMessinezis/vscode.laravel.devcontainer/
