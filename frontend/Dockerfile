FROM node:18 AS build

# Install Angular CLI globally
RUN npm install -g @angular/cli@15

WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps

COPY . .

RUN ng build --configuration production

FROM nginx:alpine
COPY --from=build /app/dist/* /usr/share/nginx/html
EXPOSE 80
