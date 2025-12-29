# базовый образ
FROM node:14-alpine
# устанавливаем рабочую директорию
WORKDIR /opt/app
# копируем все *.json - в данном случае пререквизит для установки зависимостей из package.json
ADD *.json .
# устанавливаем зависимости
RUN npm install
# копируем все в рабочую директорию
ADD . .
# собираем проект
RUN npm run build api
# запускаем проект
CMD ["node", "./dist/apps/api/main.js"]


# пояснения для самых маленьких :)
#FROM node:14-alpine        # ← СЛОЙ 1: Базовый образ (900MB)
#WORKDIR /opt/app           # ← СЛОЙ 2: Создание папки (0B)
#ADD *.json .               # ← СЛОЙ 3: Копирование package.json (5KB)
#RUN npm install            # ← СЛОЙ 4: Установка node_modules (300MB)
#ADD . .                    # ← СЛОЙ 5: Копирование кода (50MB)
#RUN npm run build          # ← СЛОЙ 6: Сборка проекта (200MB)