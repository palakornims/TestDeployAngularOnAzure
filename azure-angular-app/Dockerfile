#Stage 1 : build
FROM node:22 as builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

#Stage 2 : serve
FROM nginx:alpine
COPY --from=builder /app/dist/azure-angular-app /usr/share/nginx/html
EXPOSE 80
CMD ["nginx","-g","daemon off;"]
