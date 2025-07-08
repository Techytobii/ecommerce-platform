# Build stage
FROM node:18 as build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Production stage
FROM node:18-slim

WORKDIR /app

# Install `serve` globally
RUN npm install -g serve

COPY --from=build /app/build ./build

EXPOSE 5000

CMD ["serve", "-s", "build"]
