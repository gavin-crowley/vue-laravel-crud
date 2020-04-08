# Laravel 5.6 and Vue.js 2.5 CRUD

<p align="center">
  <img src="https://i.gyazo.com/23953e74fa86a60584b99e044a4c1b66.png" />
</p>

A basic CRUD system with Laravel 5.6 and Vue.js 2.5

## Technologies used
* Vue.js
* Vue Router
* Axios
* Laravel 5.6
* SQLite

## Basic requirements
* PHP 7 
* Composer installed
* Node.js installed
* Able to run npm
* SQLite installed on your computer

## Steps to run it

### The common way

Rename the `.env.example` file to `.env`.

Then, on your `.env` file, fill the `DB_DATABASE` variable with the absolute path to the `database.sqlite` file located in the project directory. An example might be:

```
DB_DATABASE=C:\Users\Elias\Desktop\laravel-vue-crud\database.sqlite
```

Install the dependencies:

```
npm install
composer install
```

Generate Laravel Keys:

```
php artisan key:generate
```

Migrate and seed your local database:

```
php artisan migrate --seed
```

Compile the front-end:

```
npm run prod
```

Run the server:

```
php artisan serve
```

*Note*: Is that is not working, try running this command: 
```
php -S localhost:8000 -t public
```

After this you should see the app running on http://localhost:8000. Enjoy!!
