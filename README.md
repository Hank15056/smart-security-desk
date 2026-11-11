# Smart Security Desk

MVP веб-системы для службы безопасности и IT-отдела: учёт камер (CCTV), событий IoT-датчиков и инцидентов. Оператор видит камеры (online/offline), события и инциденты, создаёт инциденты и меняет их статус.

Учебный проект по дисциплине ТРПП · Павлов А.С., группа КС 3-24.
Все организации, люди и данные в проекте вымышленные.

## Возможности

- Список камер с состоянием online/offline и ссылкой на preview.
- События IoT: motion, door_open, smoke, camera_offline.
- Инциденты: создание, приоритет, ответственный, статус (new → in_progress → resolved).
- Фильтр инцидентов по статусу.
- REST API на Express с валидацией и хранением в `data/db.json`.

## Технологии

Node.js (LTS), Express, HTML/CSS/JavaScript (fetch), Git / GitHub.

## Структура

```
smart-security-desk/
├── package.json
├── server.js
├── data/
│   └── db.json
├── public/
│   ├── index.html
│   ├── style.css
│   └── app.js
├── README.md
└── .gitignore
```

## Запуск

```
npm install
npm start
```

Приложение: `http://localhost:3000`
Health check: `http://localhost:3000/api/health`

## API

| Метод | Endpoint | Назначение |
|---|---|---|
| GET | /api/health | Проверка работоспособности |
| GET | /api/cameras | Список камер |
| PATCH | /api/cameras/:id | Изменить статус камеры (online/offline) |
| GET | /api/events | События (фильтры: severity, cameraId) |
| POST | /api/events | Создать событие |
| GET | /api/incidents | Инциденты (фильтры: status, severity) |
| POST | /api/incidents | Создать инцидент (status=new) |
| PATCH | /api/incidents/:id | Изменить статус/поля инцидента |

## Версии

- v1.0.0 — MVP: камеры, события, инциденты, фильтр, REST API.
