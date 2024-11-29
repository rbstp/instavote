FROM node:8.9-alpine

# Set ENV variables
ENV PORT=80
ENV NPM_CONFIG_PREFIX=/app/.npm-global

# Create app directory and set permissions
RUN mkdir -p /app /app/.npm-global && \
  chown -R node:node /app

WORKDIR /app

# Switch to non-root user
USER node

# Install global packages
RUN npm config set registry https://registry.npmjs.org && \
  npm install -g nodemon

# Install dependencies
COPY --chown=node:node package*.json ./
RUN npm install && \
  npm ls && \
  npm cache clean --force

# Copy app source
COPY --chown=node:node . .

EXPOSE 80

CMD ["node", "server.js"]
