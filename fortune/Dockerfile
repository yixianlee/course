# the environment
FROM node:14

# environment variable to define my workspace
ENV APP_DIR=/app APP_PORT=3000

# create and cd into APP_DIR
# mkdir /app
# cd /app
WORKDIR ${APP_DIR}

# copy the file fortune into /app
# ADD local image
# copy the files
ADD main.js .
ADD package.json .
ADD package-lock.json .

#copy the directories
ADD public public
ADD views views

# install the dependencies - package.json
RUN npm install 

# Add healthcheck
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \  
    CMD curl -s -f http://localhost:${APP_PORT}/health > /dev/null || exit 1


# the port the application is exposing 
EXPOSE ${APP_PORT}

# run the application
ENTRYPOINT ["node", "main.js" ]