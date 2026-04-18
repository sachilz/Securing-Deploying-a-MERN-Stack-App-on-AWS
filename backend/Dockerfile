# ---- Build Stage ----
FROM alpine:latest AS build
WORKDIR /app

# Install Node.js and npm
RUN apk add --no-cache nodejs npm

# Copy dependency files first (important for caching)
COPY package*.json ./

# Install only production dependencies securely
RUN npm install --omit=dev && npm cache clean --force

# ---- Production Stage ----
FROM alpine:latest AS production
WORKDIR /app

# Install Node.js only (no npm) to aggressively reduce size
RUN apk add --no-cache nodejs

# Set environment to production
ENV NODE_ENV=production

# Run as non-root user for better security
RUN addgroup -S node && adduser -S node -G node
USER node

# Copy dependencies from the build stage
COPY --from=build --chown=node:node /app/node_modules ./node_modules

# Copy application source code
COPY --chown=node:node . .

EXPOSE 5000

# Use node instead of nodemon for production
CMD ["node", "server.js"]