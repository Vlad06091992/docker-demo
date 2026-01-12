FROM node:14-alpine as build
WORKDIR /opt/app
ADD *.json ./
RUN npm install
ADD . .
RUN npm run build api

# 2 шаг -
FROM node:14-alpine
WORKDIR /opt/app
ADD package.json ./
RUN npm install --only=prod
COPY --from=build /opt/app/dist/apps/api ./dist/
CMD ["node", "./dist/main.js"]


# пояснения для самых маленьких :)
#FROM node:14-alpine        # ← СЛОЙ 1: Базовый образ (900MB)
#WORKDIR /opt/app           # ← СЛОЙ 2: Создание папки (0B)
#ADD *.json .               # ← СЛОЙ 3: Копирование package.json (5KB)
#RUN npm install            # ← СЛОЙ 4: Установка node_modules (300MB)
#ADD . .                    # ← СЛОЙ 5: Копирование кода (50MB)
#RUN npm run build          # ← СЛОЙ 6: Сборка проекта (200MB)