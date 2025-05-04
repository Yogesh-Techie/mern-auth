# Stage 1: Build React app
FROM node:18 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (or yarn.lock) to leverage Docker cache
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Build the React app
RUN npm run build

# Stage 2: Set up Nginx to serve the app
FROM nginx:alpine

# Copy custom nginx.conf (optional)
COPY nginx.conf /etc/nginx/nginx.conf

# Copy the build files from the first stage to Nginx's HTML directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 to access the app
EXPOSE 80

# Command to run Nginx
CMD ["nginx", "-g", "daemon off;"]
