FROM node:latest

ENV APP_ROOT=/app APP_PORT=3000

# create APP_ROOT and cd in
WORKDIR ${APP_ROOT}

# copy the files and directories into image
ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views

# install the dependencies
RUN npm install

# health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

# port to use
EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]
# CMD [ "${APP_PORT}" ]