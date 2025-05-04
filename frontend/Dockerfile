# Use the official Nginx image
FROM nginx:alpine

# Copy custom nginx configuration (optional)
COPY nginx.conf /etc/nginx/nginx.conf

# Set the working directory
WORKDIR /app

# Copy the build files from your React app's build directory
COPY build/ /usr/share/nginx/html

# Expose port 80 to access the app
EXPOSE 80

# Default command to run nginx
CMD ["nginx", "-g", "daemon off;"]
