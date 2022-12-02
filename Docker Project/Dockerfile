# Build Phase
FROM node:16-alpine as builder
# Switch workdir to '/usr/app'
WORKDIR /usr/app
# Copy package.json into container
COPY ./package.json .
# Install all the deps
RUN npm install
# Copy the all other files into the container
COPY . .
# Build the production files
RUN npm run build

# Run Phase
FROM node:16-alpine
WORKDIR /usr/app
COPY package.json ./
RUN npm install
COPY --from=builder /usr/app/dist .
CMD ["node", "server.js"]
