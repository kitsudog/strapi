FROM node:18-alpine3.18
# Installing libvips-dev for sharp Compatibility
RUN apk update && apk add --no-cache build-base gcc autoconf automake zlib-dev libpng-dev nasm bash vips-dev git
ARG NODE_ENV=development
ENV NODE_ENV=${NODE_ENV}

WORKDIR /opt/
RUN npm install -g node-gyp
COPY package.json package-lock.json /opt/
RUN npm config set fetch-retry-maxtimeout 600000 -g && npm install
ENV PATH=/opt/node_modules/.bin:$PATH
EXPOSE 1337
ENV HOST=0.0.0.0 \
    PORT=1337 \
    DATABASE_CLIENT=sqlite
COPY sample /opt/
CMD npm run develop
