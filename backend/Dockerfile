# 1. Use a lightweight official Node.js base image
FROM node:22

# 2. Set the working directory inside the container
WORKDIR /app

# 3. Copy dependency definitions first to leverage Docker cache
# Only re-installs dependencies if these files change
COPY package*.json ./

# 4. Install production dependencies (omit devDependencies)
RUN npm ci --only=production

# 5. Copy the rest of your application code
COPY . .

# 6. Use a non-root user for security (provided by the node image)
USER node

# 7. Expose the port your app runs on
EXPOSE 4000

# 8. Define the command to run your app
CMD ["node", "server.js"]

