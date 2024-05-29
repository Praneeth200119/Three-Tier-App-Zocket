# Stage 1: Build the application
FROM node:16 AS builder

# Create and change to the app directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install app dependencies
RUN npm install


# Copy the rest of the application code
COPY . .

# Build the application (if using a build step, e.g., for a React app)
# RUN npm run build

# Stage 2: Run the application
FROM node:16-alpine

# Create and change to the app directory
WORKDIR /usr/src/app

# Copy only the necessary files from the builder stage
COPY --from=builder /usr/src/app .

# Install only production dependencies
RUN npm install --only=production

# Expose the port the app runs on
EXPOSE 4000

# Define the command to run the application
CMD ["node", "app.js"]
