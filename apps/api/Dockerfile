# базовый образ
FROM node:14
# устанавливаем рабочую директорию
WORKDIR /opt/app
# копируем все в рабочую директорию
ADD . .
# устанавливаем зависимости
RUN npm install
# собираем проект
RUN npm run build api
# запускаем проект
CMD ["node", "./dist/apps/api/main.js"]