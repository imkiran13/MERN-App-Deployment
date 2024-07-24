# Stage 1: Build
FROM node:14 AS build

# Set working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application (optional, depends on your application)
# RUN npm run build

# Stage 2: Runtime
FROM node:14-alpine AS runtime

# Set working directory
WORKDIR /usr/src/app

# Copy only the necessary files from the build stage
COPY --from=build /usr/src/app /usr/src/app

# Expose the application port (if needed)
EXPOSE 3000

# Command to run the application
CMD ["npm", "start"]
