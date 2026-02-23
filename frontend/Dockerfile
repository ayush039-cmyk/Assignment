FROM node:18-alpine

WORKDIR /app

COPY package.json ./

COPY package-lock.json ./

RUN npm install

COPY . .

RUN npm install -g @angular/cli

EXPOSE 8081

CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "8081"]
