# laravel-app
```
"require": {
        "php": "^8.2",
        "jgrossi/corcel": "^9.0",
        "laravel/framework": "^12.0",
        "laravel/tinker": "^2.10.1",
        "ncc/packages-ncc": "dev-main"
    },
```
# product
```
"repositories": [
        {
            "type": "path",
            "url": "./packages-ncc",
            "options": {
                "symlink": false
            }
        }
    ],

```
# dev
```
"repositories": [
        {
            "type": "path",
            "url": "./packages-ncc",
            "options": {
                "symlink": true
            }
        }
    ],

```

composer require jgrossi/corcel

php artisan vendor:publish --provider="Corcel\Laravel\CorcelServiceProvider"

```
'corcel' => [
            'driver' => 'mariadb',
            'url' => env('DB_URL'),
            'host' => env('DB_HOST', '127.0.0.1'),
            'port' => env('DB_PORT', '3306'),
            'database' => env('DB_DATABASE', 'laravel'),
            'username' => env('DB_USERNAME', 'root'),
            'password' => env('DB_PASSWORD', ''),
            'unix_socket' => env('DB_SOCKET', ''),
            'charset' => env('DB_CHARSET', 'utf8mb4'),
            'collation' => env('DB_COLLATION', 'utf8mb4_unicode_ci'),
            'prefix' => 'wp_',
            'prefix_indexes' => true,
            'strict' => true,
            'engine' => null,
            'options' => extension_loaded('pdo_mysql') ? array_filter([
                (PHP_VERSION_ID >= 80500 ? Mysql::ATTR_SSL_CA : PDO::MYSQL_ATTR_SSL_CA) => env('MYSQL_ATTR_SSL_CA'),
            ]) : [],
        ],
```
php artisan key:generate

php artisan migrate

php artisan optimize:clear

composer update

APP_ENV=production

APP_DEBUG=false

php artisan config:cache

php artisan route:cache

php artisan view:cache

composer install --no-dev --optimize-autoloader

composer dump-autoload --no-dev --classmap-authoritative