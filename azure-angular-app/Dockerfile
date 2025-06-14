# Stage 1: Build
FROM node:22 AS builder

# Set absolute workdir path
WORKDIR /azure-angular-app

# Copy package files and install
COPY azure-angular-app/package*.json ./
RUN npm install

# Copy rest of the source and build
COPY azure-angular-app/ ./
RUN npm run build

# Stage 2: Serve with NGINX (optional)
FROM nginx:alpine
COPY --from=builder /azure-angular-app/dist/azure-angular-app /usr/share/nginx/html
