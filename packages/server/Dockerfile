# Builder
FROM node:18-alpine as builder

# Copy server and domain + lib packages
WORKDIR /usr/src/capacitor-react-nest-boilerplate/
COPY package.json .
COPY yarn.lock .

COPY packages/server packages/server
COPY packages/server/.env packages/server/.env

# Install domain + lib + server dependencies
RUN yarn install --pure-lockfile --non-interactive

# Build server then
WORKDIR /usr/src/capacitor-react-nest-boilerplate/packages/server
RUN yarn build

# Runner
FROM node:18-alpine AS runner

WORKDIR /usr/src/capacitor-react-nest-boilerplate
# Copy the dist builds from builder
COPY --from=builder /usr/src/capacitor-react-nest-boilerplate/package.json .
COPY --from=builder /usr/src/capacitor-react-nest-boilerplate/yarn.lock .

COPY --from=builder /usr/src/capacitor-react-nest-boilerplate/packages/server/package.json packages/server/package.json
COPY --from=builder /usr/src/capacitor-react-nest-boilerplate/packages/server/dist packages/server/dist
COPY --from=builder /usr/src/capacitor-react-nest-boilerplate/packages/server/.env packages/server.env


# Install production dependencies
RUN yarn install --pure-lockfile --non-interactive --production

# Move to the server app
WORKDIR /usr/src/capacitor-react-nest-boilerplate/packages/server
# Set the correct ownership for the app folder
RUN chown -R node:node /usr/src/capacitor-react-nest-boilerplate/packages/server/

# Launch the server with container
CMD ["yarn", "start:prod"]
EXPOSE 3000
