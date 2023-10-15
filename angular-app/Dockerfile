# Use an official Node.js runtime as the base image
FROM node:16.14.0 as node

# Set the working directory inside the container
WORKDIR /app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Build the application (assuming you have a build script defined in package.json)
RUN npm run build

# Expose the port your application will listen on
EXPOSE 4200

# Define the command to start your application
CMD ["npm", "start"]
