# build stage
FROM node:latest as build-stage
WORKDIR /app

COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build 


# production stage
FROM nginx as production-stage
RUN mkdir /app
COPY --from=build-stage /app/dist /app
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80
EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]
# sudo docker build -t simplyonline:ui
# sudo docker run -it -p 8081:8080 simplyonline:ui