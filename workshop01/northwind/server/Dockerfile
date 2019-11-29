FROM node:latest

## How an image is build
# Set environment variables
ENV APP_ROOT=/app 
ENV APP_PORT=3000
ENV DB_HOST=localhost

# create the directory and cd into in
WORKDIR ${APP_ROOT}

# Copy files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
ADD public public
ADD views views
ADD config config

# run some command
# RUN is only used in building
# create node module directory
RUN npm install

## How an image is provision/run

# What port our container will be exposing
# EXPOSE ${APP_PORT}/udp for udp but default is tcp
EXPOSE ${APP_PORT}

# add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

# ENTRYPOINT/CMD is used in execution
# node main.js 3000
ENTRYPOINT ["node", "main.js"]

# is an option, with reference to node main/js 3000, 3000 is the option.
#CMD [""]