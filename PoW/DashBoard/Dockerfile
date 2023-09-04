# Use an official Node.js runtime as the base image
FROM node:latest

# Declare the build argument
ARG WS_SECRET

# Set the working directory inside the container
WORKDIR /usr/src/app

# Clone the git repository
RUN git clone https://github.com/Kerala-Blockchain-Academy/ethstats-server .

# Install dependencies
RUN npm install && \
    npm install -g grunt-cli && \
    npm install grunt --save-dev

# Build the project for monitoring the proof of work
RUN npx grunt pow

# Use the build argument to set the environment variable
ENV WS_SECRET=$WS_SECRET

# Expose port 3000 for the app
EXPOSE 3000

# Command to run the app
CMD ["npm", "start"]