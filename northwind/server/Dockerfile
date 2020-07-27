# the environment
FROM node:14

# environment variable to define my workspace
ENV APP_DIR=/app APP_PORT=3000 

#for database
ENV DB_PORT=3306 DB_USER='root' DB_PASSWORD='changeit'

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
ADD config config
                                                           
# install the dependencies - package.json
RUN npm install 

# Add healthcheck
HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \  
    CMD curl -s -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

#CMD mysqladmin ping -uroot -pchangeit > /dev/null || exit 1

# the port the application is exposing 
EXPOSE ${APP_PORT}

# run the application
ENTRYPOINT ["node", "main.js" ]