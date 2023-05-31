$composer create-project laravel/laravel BaliFit
->Installing laravel/laravel (v10.2.2)

$cd BaliFit

$git init

$git add .

$git commit -m "Za Warudo, Tomare! Toki wo!"

$git branch -M main

$git remote add origin https://github.com/Happy-Franck/BaliFit.git

$git push -u origin main

$php artisan migrate

//SANCTUM
$composer require laravel/sanctum
$php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
->/config/sanctum.php
$php artisan migrate

//SPATIE
$composer require spatie/laravel-permission
$php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
->/config/permission.php
$php artisan migrate

//Creates roles with spatie
$php artisan make:seeder RolePermissionSeeder
$php artisan migrate:fresh --seed

//Configurer le model role
use Spatie\Permission\Traits\HasRoles;
class User extends Authenticatable
{
    use HasApiTokens, HasFactory, Notifiable, HasRoles;
    ...
}

//create login register and logout
$php artisan make:controller AuthController
configurer les routes login, register et logout
$php artisan route:list --path=api


//PRODUIT
User 1-->N Produit
$php artisan make:model Produit -crm
