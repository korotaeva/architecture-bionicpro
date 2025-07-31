# Build stage
FROM --platform=$BUILDPLATFORM node:18-bullseye AS builder

WORKDIR /app

# Install ARM64 specific build dependencies
RUN apt-get update -o Acquire::http::No-Cache=True \
    -o Acquire::http::Pipeline-Depth=0 -o Acquire::BrokenProxy=true


# Configure npm
RUN npm config set fetch-retry-mintimeout 20000 && \
    npm config set fetch-retry-maxtimeout 300000 && \
    npm config set fetch-timeout 600000

# Copy package files first for better caching
COPY package.json package-lock.json ./

# Install dependencies with caching (including devDependencies)
RUN --mount=type=cache,target=/root/.npm \
    --mount=type=cache,target=/app/node_modules \
    npm ci --prefer-offline --no-audit --progress=false

# Copy source code
COPY . .

# Build the app
RUN NODE_OPTIONS="--max-old-space-size=4096" npm run build

# Production stage
FROM nginx:1.23-alpine

# Copy built assets
COPY --from=builder /app/build /usr/share/nginx/html

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 3000
CMD ["nginx", "-g", "daemon off;"]