# ---- Build stage: compile the React app into static files ----
FROM node:22-alpine AS build

WORKDIR /app

# Install dependencies first (layer caching)
COPY package*.json ./
RUN npm install

# Copy the source and build — produces /app/dist
COPY . .
RUN npm run build

# ---- Serve stage: hand the static files to nginx ----
FROM nginx:alpine

# Copy only the built files from the build stage into nginx's web root
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
