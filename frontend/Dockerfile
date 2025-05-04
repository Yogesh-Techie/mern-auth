# Use the official Node.js image to build the React app
FROM node:18 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (or yarn.lock)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Build the React app
RUN npm run build

# Use the official Nginx image to serve the app
FROM nginx:alpine

# Copy custom nginx.conf (optional)
COPY nginx.conf /etc/nginx/nginx.conf

# Copy the build files from the previous stage into Nginx's HTML directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 to access the app
EXPOSE 80

# Command to run Nginx
CMD ["nginx", "-g", "daemon off;"]
