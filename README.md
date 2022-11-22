サンプル

https://user-images.githubusercontent.com/118511327/203225837-4b15edfe-4c98-4204-9212-523d82522dd2.mov

# go_docker_sample

## Start with...
`go mod init`

or

`go mod init github.com.YOUR_REPOSITORY/REPOSITORY_NAME`


## Creating main.go
Just for checking, make a simple page:
```
package main

import (
	"fmt"
	"log"
	"net/http"
)

func homePage(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Welcome to the HomePage!")
	fmt.Println("Endpoint Hit: homePage")
}


func main() {
	http.HandleFunc("/", homePage)
	log.Fatal(http.ListenAndServe(":8080", nil))
}
```

Run the file and Check if the connection works.
```
go run main.go
```

## Migration file

```
mkdir database
```
```
touch migration.sql
```


## docker へのインストール

```
docker-compose exec go ash
```

```
go get github.com/gin-gonic/gin
```

```
go get github.com/jinzhu/gorm
```


# golang-migrations

```
docker exec -it todo_api ash

migrate create -ext sql -dir db/migrations -seq create_todos

migrate -path db/migrations -database="mysql://tester:secret@tcp(db:3306)/test" up 1
```

```
CREATE TABLE `todos` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `text` TEXT NOT NULL,
  `status` VARCHAR(255) NOT NULL,
  `deleted_at` DATETIME,
  `updated_at` DATETIME,
  `created_at` DATETIME,
  PRIMARY KEY (`id`)
);

INSERT INTO `todos` (`text`, `status`,`deleted_at`, `updated_at`, `created_at`)
VALUES ('Shopping', '0', NULL, '2020-01-01 10:10:10', '2020-01-01 10:10:00'),
       ('Laundry', '1', '2020-01-01 10:10:10', '2020-01-01 10:10:10', '2020-01-01 10:10:00');
       ('Laundry', '0', NULL, '2020-01-01 10:10:10', '2020-01-01 10:10:00');
```

# CRUD

## Edit
https://user-images.githubusercontent.com/118511327/203226260-6442fcdf-eb32-4e8d-a00e-1acd6a9a6bed.mov

## Delete
https://user-images.githubusercontent.com/118511327/203226277-dad79fe1-6295-4faf-a2d4-3c46e5b50853.mov


