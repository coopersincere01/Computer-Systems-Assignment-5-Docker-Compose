# Use the required lightweight Node.js 18 Alpine base image
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package files first to improve Docker layer caching
COPY package*.json ./

# Install the backend dependencies
RUN npm install

# Copy the remaining backend application files
COPY . .

# Create a directory for persistent SQLite database storage
RUN mkdir -p /app/data

# Document the port used by the Express API server
EXPOSE 5000

# Start the backend using the npm start script
CMD ["npm", "start"]
