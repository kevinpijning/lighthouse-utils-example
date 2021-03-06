# lighthouse-utils-example
An example implementation of an auto-generated GraphQL CRUD API with Laravel.

Included with this example:
* [Laravel 5.7](https://laravel.com/docs/5.7) 
* [Laravel Lighthouse](https://github.com/nuwave/lighthouse)
* [Lighthouse Utils](https://github.com/deInternetJongens/Lighthouse-Utils/)
* [GraphQL Playground](https://github.com/mll-lab/laravel-graphql-playground)

## Installation

Run the following script in the root of this project:

`./install.sh`

Alternatively, you can run the following commands yourself:

* `composer install`
* `cp -r .env.example .env`

Update the `DB_*` values in the `.env` file to the database you want to use, 
then run the migrations and seeds using the following command:

`php artisan migrate --seed`

When that's finished run `php artisan serve` and go to the URL provided in your console.
(Usually localhost:8000)

## GraphQL

Now that everything is up and running, you can try out the GraphQL API by navigating to:
http://localhost:8000/graphql-playground

On the right you will see a button `Schema`, you can inspect all the available queries and mutations there.

Some example queries:

##### Retrieve all articles and the corresponding author
```
{
  articles {
    title
    author{
      name
    }
  }
}
```

##### Retrieve all articles with a certain word in the title
```
{
  articles(title_contains: "turtle") {
    title
  }
}
```

##### Retrieve user with ID 1 and all articles they have commented on
```
{
  user(id: 1) {
    name
    comments {
      article {
        title
      }
    }
  }
}
```
