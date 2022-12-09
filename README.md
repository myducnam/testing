
## Environment
- [Laravel 9.0 (LTS)](https://laravel.com/docs/9.x/)
- PHP 8.1.*
- MySQL 5.7 (Amazon Aurora)

## Libraries
### Common
- [Laravel enum](https://github.com/BenSampo/laravel-enum)
- [Eloquent insert on duplicate key](https://github.com/guidocella/eloquent-insert-on-duplicate-key)
- [Eloquent Filter](https://github.com/Tucker-Eric/EloquentFilter)
- [Column sorting for Laravel](https://github.com/Kyslik/column-sortable)
### Development
- [Laravel Debugbar](https://github.com/barryvdh/laravel-debugbar)
- [PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)
- [GrumPHP](https://github.com/phpro/grumphp)
- [PHPMD](https://github.com/phpmd/phpmd)
- [PHPCPD](https://github.com/sebastianbergmann/phpcpd)

### Database Tables:
- users
- meals
- bodies
- meal_histories
- excises(not implement migration now)
- diaries(not implement migration now)
- columns(not implement migration now)
### Implement api for toppage(3 APIs)
- Get Achivement Rate:
    ### Client
    - url: {toppage_url}/api/body/get_achivement_rate
    - query params:
        - user_id
        - registered_date
    - header:
        - Authorization
    ### Server/API response
    - {
        "data": {
            "registeredAt": "2022-10-10",
            "achivementRate": "1.11"
        },
        "status": 200
       }
- Get Body Infos of User(this api using for chart):
    ### Client
    - url: {toppage_url}/api/body/search
    - query params:
        - user_id
        - registered_yearmonth_from
            (format: Y-m)
        - registered_yearmonth_to
            (format: Y-m)
    - header:
        - Authorization

    ### Server/API response
    - returned json data:
        - {
            "data": [
                {
                    "id": 1,
                    "weight": 100,
                    "bodyFat": 90,
                    "registeredAt": "2022-10-10"
                },
                {
                    "id": 2,
                    "weight": 130,
                    "bodyFat": 100,
                    "registeredAt": "2022-11-10"
                }
            ],
            "status": 200
           }
- Get Body Histories of User:
    ### Client
    - url: {toppage_url}/api/mealhistory/get
    - query params:
        - user_id
    - header:
        - Authorization

    ### Server/API response
    - returned json data:
        - {
            "data": [
                {
                    "id": 1,
                    "userId": 1,
                    "picture": "rice.jpg",
                    "mealType": "morning1",
                    "registeredAt": "10.10"
                },
                {
                    "id": 2,
                    "userId": 1,
                    "picture": "blue.jpg",
                    "mealType": "dinner",
                    "registeredAt": "10.15"
                }
            ],
            "status": 200
           }