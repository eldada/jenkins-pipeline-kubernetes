# Small base image pulled from private Artifactory,
# which had a remote repository proxying dockerhub
FROM docker-artifactory-webinar.jfrogdev.co/node:12.4.0-alpine AS builder

LABEL Author="eldada@jfrog.com"

ARG NPM_AUTH
ARG NPM_EMAIL="eldada@jfrog.com"
ARG NPM_REGISTRY="https://artifactory-webinar.jfrogdev.co/artifactory/api/npm/npm/"

# Set app directory
WORKDIR /usr/src/app

# Copy the .npmrc with the credentials for the provate Artifactory npm registry
#COPY ./.npmrc /root/.npmrc

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
COPY demo.js .

RUN echo "_auth = ${NPM_AUTH}" > .npmrc && \
    echo "always-auth = true" >> .npmrc && \
    echo "email = ${NPM_EMAIL}" >> .npmrc && \
    echo "registry = ${NPM_REGISTRY}" >> .npmrc && \
    npm install && \
    rm -rfv .npmrc /root/.npmrc

# Main build
FROM docker-artifactory-webinar.jfrogdev.co/node:12.4.0-alpine
WORKDIR /usr/src/app

COPY --from=builder /usr/src/app /usr/src/app

EXPOSE 8080
CMD [ "npm", "start" ]
