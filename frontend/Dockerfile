# Building a Docker image for a React application using Nginx
FROM node:16-alpine as builder
WORKDIR /app
COPY package*.json ./
RUN npm install 

COPY . .
# Add --force flag to bypass errors
RUN npm run build 

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
