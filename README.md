# Практическая работа №9: Регистрация и вход пользователей (bcrypt)

## Описание проекта
Учебный проект на языке Go, реализующий безопасную регистрацию и аутентификацию пользователей. Пароли не хранятся в открытом виде, а хэшируются с помощью алгоритма **bcrypt** со встроенной солью. Проект подготавливает базу для выдачи JWT-токенов в следующей работе.

## Функционал
Сервер предоставляет два эндпоинта:
*   `POST /auth/register` — регистрация нового пользователя (email + password). Пароль валидируется (мин. 8 символов) и хэшируется.
*   `POST /auth/login` — проверка пары email+password. Возвращает `200 OK` при успехе и `401 Unauthorized` при ошибке.

## Стек технологий
*   **Язык:** Go (Golang)
*   **База данных:** PostgreSQL
*   **ORM:** GORM (`gorm.io/gorm`, `gorm.io/driver/postgres`)
*   **Маршрутизация:** Chi (`github.com/go-chi/chi/v5`)
*   **Безопасность:** Bcrypt (`golang.org/x/crypto/bcrypt`)

## Структура проекта
```text
pz9-auth/
│
├── cmd/
│   └── api/
│       └── main.go         
│
├── internal/
│   ├── core/
│   │   └── user.go       
│   │
│   ├── http/
│   │   └── handlers/
│   │       └── auth.go      
│   │
│   ├── platform/
│   │   └── config/
│   │       └── config.go   
│   │
│   └── repo/
│       ├── postgres.go      
│       └── user_repo.go     
│
├── go.mod                 
├── go.sum                  
└── README.md
