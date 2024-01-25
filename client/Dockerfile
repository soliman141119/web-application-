# Use the official Node.js base image
FROM node:18.0.0-alpine as build
# Set working directory
WORKDIR /app
# Copy the Nuxt.js client code to the container
#COPY package*.json ./
COPY package*.json  ./
# Install dependencies
RUN npm  install
COPY .   ./
# Build the Nuxt.js app
RUN npm run build

FROM node:alpine as main

COPY --from=build /app /
# Expose port 3000 (default Nuxt.js port)

EXPOSE 3000

# Start the Nuxt.js app
CMD ["npm","run","serve"]
