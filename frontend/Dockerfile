# ---- Build Stage ----
FROM node:20-alpine AS build
WORKDIR /app

# Copy dependency files first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application for production
RUN npm run build

# ---- Production Stage ----
FROM nginx:alpine
# Remove default nginx static assets
RUN rm -rf /usr/share/nginx/html/*

# Copy the static React build files from the build stage
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 to the Docker host
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]