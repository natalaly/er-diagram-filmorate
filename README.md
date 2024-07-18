# [FILMORATE](https://github.com/natalaly/java-filmorate) 

1. [ER - diagram](#er-diagram)
2. [Description](#tables-description)

## ER diagram
![](er-diagram.png)

## Tables Description
<details>
<summary>Users</summary>

The `Users` table stores information about the users of the Filmorate application.

| Column   | Type    | Constraints      | Notes                 |
|----------|---------|------------------|-----------------------|
| id       | integer | PK               | unique identification |   
| email    | varchar | not null, unique | user email            |
| login    | varchar | not null, unique | user login            |
| name     | varchar |                  | user name             |
| birthday | date    | not null         | user birthday         |

</details>

<details>
<summary>Friendships</summary>

The `Friendships` table captures the friendship relationships between users.

| Column    | Type    | Constraints      | Notes                                             |
|-----------|---------|------------------|---------------------------------------------------|
| id        | integer | PK, FK(users.id) | part of composite PK, references user ID          |   
| friend_id | integer | PK, FK(users.id) | part of composite PK, references friend's user ID |
| status    | bool    | default = false  | defines if friendship is confirmed                |

</details>

<details>
<summary>Films</summary>

The `Films` table holds information about the films available in the application.

| Column        | Type    | Constraints        | Notes                           |
|---------------|---------|--------------------|---------------------------------|
| id            | integer | PK                 | unique identification for films |   
| name          | varchar | not null           | film name                       |
| description   | varchar |                    | film description                |
| release_date  | day     | not null           | film release date               |
| duration      | integer |                    | film duration in minutes        |
| mpa_rating_id | integer | FK(mpa_ratings.id) | references MPA rating ID        |

</details>

<details>
<summary>Users_Likes</summary>

The `Users_Likes` table records the "likes" that users give to films.

| Column  | Type    | Constraints      | Notes                                    |
|---------|---------|------------------|------------------------------------------|
| user_id | integer | PK, FK(users.id) | part of composite PK, references user ID |   
| film_id | integer | PK, FK(films.id) | part of composite PK, references film ID |

</details>

<details>
<summary>Film_Genres</summary>

The `Film_Genres` table establishes a many-to-many relationship between films and genres.

| Column   | Type    | Constraints       | Notes                                     |
|----------|---------|-------------------|-------------------------------------------|
| film_id  | integer | PK, FK(films.id)  | part of composite PK, references film ID  |   
| genre_id | integer | PK, FK(genres.id) | part of composite PK, references genre ID |



</details>

<details>
<summary>Genres</summary>

The `Genres` table lists the various genres that films can belong to.

| Column | Type    | Constraints | Notes                           |
|--------|---------|-------------|---------------------------------|
| id     | integer | PK          | unique identification for genre |   
| name   | varchar | not null    | genre name                      |

| id | name           |
|----|----------------|
| 1  | Комедия        |
| 2  | Драма          |
| 3  | Мультфильм     |
| 4  | Триллер        |
| 5  | Документальный |
| 6  | Боевик         |

</details>

<details>
<summary>Mpa_Ratings</summary>

The `Mpa_Ratings` table contains the various Motion Picture Association (MPA) ratings 
that can be assigned to films, indicating the appropriate age restrictions. 

| Column | Type    | Constraints | Notes                            |
|--------|---------|-------------|----------------------------------|
| id     | integer | PK          | unique identification for rating |   
| name   | varchar | not null    | rating name                      |

| id | name  |                                               
|----|-------|
| 1  | G     |                                              
| 2  | PG    |                        
| 3  | PG-13 |                                  
| 4  | R     | 
| 5  | NC-17 |

</details>