# Stage 1: Build the React application using Node.js
FROM node:18-alpine AS builder

# Set the working directory for the build stage
WORKDIR /app

# Copy package files first to improve Docker layer caching
COPY package*.json ./

# Install dependencies, including the Vite build tools
RUN npm install

# Copy the remaining frontend application files
COPY . .

# Build the optimized production application
RUN npm run build

# Stage 2: Serve the production files with nginx
FROM nginx:alpine

# Copy the built files from the first stage to nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose the default nginx HTTP port
EXPOSE 80

# Run nginx in the foreground to keep the container running
CMD ["nginx", "-g", "daemon off;"]