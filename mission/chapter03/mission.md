### 1. 홈 화면

| 항목            | 내용                             |
|-----------------|----------------------------------|
| API Endpoint    | `/home`                          |
| Method          | `GET`                            |
| Request Body    | x                                |
| Request Header  | `Authorization = "Access Token"` |
| query String    | x                                |
| Path variable   | x                                |


### 2. 마이 페이지

| 항목            | 내용                                 |
|-----------------|--------------------------------------|
| API Endpoint    | `/user/{nickname}`                   |
| Method          | `GET`                                |
| Request Body    | x                                    |
| Request Header  | `Authorization = "Access Token"`     |
| query String    | x                                    |
| Path variable   | `nickname(varchar(20))`              |


### 3. 리뷰 작성

| 항목            | 내용                                               |
|-----------------|----------------------------------------------------|
| API Endpoint    | `/restaurant/{restaurant_id}/review/`             |
| Method          | `POST`                                            |
| Request Body    | `{ "star": Integer, "content": "text", "img_url_list": string[] }` |
| Request Header  | `Authorization = "Access Token"`                  |
| query String    | x                                                 |
| Path variable   | `restaurant_id(Long)`                             |



### 4. 미션 목록 조회

| 항목            | 내용                                               |
|-----------------|----------------------------------------------------|
| API Endpoint    | `/user/{user_id}/mission`                          |
| Method          | `GET`                                              |
| Request Body    | x                                                  |
| Request Header  | `Authorization = "Access Token"`                   |
| query String    | `?completed=true` 또는 `?completed=false` (`enum`) |
| Path variable   | `user_id(Long)`                                    |



### 5. 미션 성공 누르기

| 항목            | 내용                                               |
|-----------------|----------------------------------------------------|
| API Endpoint    | `/user/{user_id}/mission/{mission_id}`            |
| Method          | `PATCH`                                            |
| Request Body    | x                                                  |
| Request Header  | `Authorization = "Access Token"`                   |
| query String    | x                                                  |
| Path variable   | `user_id(Long)`, `mission_id(Long)`               |


### 6. 회원가입 하기

| 항목            | 내용                                                    |
|-----------------|---------------------------------------------------------|
| API Endpoint    | `/user/join`                                            |
| Method          | `POST`                                                  |
| Request Body    | `{                                                     |
|                 |    "username": "varchar(20)",                          |
|                 |    "password": "text",                                 |
|                 |    "nickname": "varchar(20)",                          |
|                 |    "phone_number": "varchar",                          |
|                 |    "birth_date": "datetime(6)",                        |
|                 |    "gender": "enum('MAN', 'WOMAN')",                   |
|                 |    "email": "text"                                     |
|                 | }                                                      |
| Request Header  | x                                                       |
| query String    | x                                                       |
| Path variable   | x                                                       |
