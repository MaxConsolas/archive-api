# archive-api
Используется 
"axios": "^0.21.1"
"core-js": "^3.6.5",
"material-design-icons-iconfont": "^6.1.0",
"module": "^1.2.5",
"vue": "^2.6.11",
"vuetify": "^2.4.0"

## Запуск проекта
Для запуска проекта установить Node.js https://nodejs.org/en/
Желательное LTS

Установка зависимостей
```
npm install
```

Далее создаем в корне проекта файл .env
В нем создаем переменные окружения
```
VUE_APP_NAME=Archive API
VUE_APP_HOST=http://ВНЕШНИЙ_IP_НА_API 
```

### Сборка для разработки
```
npm run serve
```

### Сборка на продакшен
```
npm run build
```

### Линтинг
```
npm run lint
```
