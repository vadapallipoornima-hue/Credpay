FROM node:22-alpine AS build
WORKDIR /build
COPY package*.json ./        
RUN npm install
COPY . .
RUN npm run build     # builds the application and creates a build directory
FROM nginx:stable-alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /build/dist /usr/share/nginx/html
EXPOSE 80






#