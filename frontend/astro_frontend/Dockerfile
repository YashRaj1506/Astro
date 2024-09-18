# Use an official Node.js runtime as the base image
FROM node:16-alpine as build

WORKDIR /app/frontend/astro_frontend

COPY /frontend/astro_frontend/package*.json ./
RUN npm install

COPY . ./frontend/
RUN npm run build

# Production NGINX to serve the React app
FROM nginx:alpine
COPY --from=build /app/frontend/astro_frontend/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
