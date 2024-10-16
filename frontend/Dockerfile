# Frontend Dockerfile
FROM node:14-alpine as build-stage

# Arbeitsverzeichnis festlegen
WORKDIR /app

# Abhängigkeiten kopieren
COPY package.json ./

# Abhängigkeiten installieren
RUN npm install

# Quellcode kopieren
COPY . .

# Anwendung bauen
RUN npm run build

# Produktions-Image
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html

# Port freigeben
EXPOSE 80

# Startbefehl
CMD ["nginx", "-g", "daemon off;"]
