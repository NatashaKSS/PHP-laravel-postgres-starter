# PHP, Postgres web app with Laravel as a framework

## Online Tutorials
[Learn all about Laravel in 1 hour](https://www.youtube.com/watch?v=lnf1GdNxDbc&list=PL_UnIDIwT95NUvLU14l_QFFV2ZxO1phpQ)

# SETUP
## What you'll need
* Download & install PHP's dependency management tool [Composer](https://getcomposer.org/download/)
* Install [Laravel](https://laravel.com/docs/5.5/installation)
* Download / Clone this repo
* Fresh database (you can create a new one using pgAdmin4)

## 1. Setting up your credentials, schemas & seed data for DB
**Note:** I did not upload my `.env` file since it contains my own local DB credentials, but you can refer to the uploaded `.env.example` file for an example of what fields to change. All fields in `[]` square brackets are what you'll need to change for your project.

1. Run `php artisan migrate` to create the tables `users` & `password_resets` & `tasks`. `users` and `password_resets` are used for simple authentication and `tasks` is a simple table which will contain our tasks.

2. Run `php artisan db:seed --class=TasksTableSeeder` which creates 3 rows in the `tasks` table.


## 2. Run this project
1. Run `php artisan key:generate` to generate an `APP_KEY` for your project. Your `APP_KEY` is located in 3rd line of your `.env` file.

2. Run `php artisan serve`. Verify that your app running at `http://localhost:8000`.

3. Your DB doesn't contain any users, so register for an account by clicking on 'Register' on the top right hand corner of the page. Log in, and you'll be brought to your dashboard where you should see all the tasks that are currently in the `tasks` table (those that you ran `php artisan db:seed --class=TasksTableSeeder`).

## Important files
Explanation of some of the files I edited & what they're for. These files have in-code documentation too. 
There are many other files in this project but these are the important ones to demonstrate the app's current functionalities.
```
.env.example                  # environment variables. Set APP_KEY & your DB credentials here & remember to rename this to '.env' once you've set your credentials!
├── app                       # contains controllers (app logic) and middleware classes
  ├── Http                     
    ├── Controllers           # app-specific logic
        HomeController.php    # app logic for the /Home page. Contains the methods to display all tasks from the tasks table and to add a task to the tasks table
├── database                  # DB logic
  ├── migrations              # DB table creation classes. These are executed when you run 'php artisan migrate'.
      2017_09_21_131359_create_tasks_table  # Creates tasks table
  ├── seeds                   # DB data seeder classes. These help us generate dummy data & insert rows into a table. These are executed when you run 'php artisan db:seed --class=[some_class_name_you_created]'
      TasksTableSeeder        # inserts 3 tasks into the tasks table
├── resources                 # static assets, our UI files
  ├── views                   # UI PHP files. Blade is the default UI template engine for Laravel and you'll find some of these files here
      welcome.blade.php       # 1st page of the app
      home.blade.php          # user dashboard page seen once a user logs in. Displays some user info, a form for adding tasks and all the tasks currently in the tasks table
    ├── layouts
        app.blade.php         # a reusable layout for the entire application. You'll find the HTML for the nav bar here.
├── routes
    web.php                   # routes for the app. Routing logic for the welcome page, user's dashboard and auth routes.  
└── composer.json             # Composer's specification file containing our Laravel-specific project dependencies. I didn't edit anything in here though.
```

## Done!
* We'll probably need to change lots of the stuff in this project, if we're using this, but I hope this helps us create a simple starter project more easily.


## Common Problems

