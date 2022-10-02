#This line defines the node version and uses node container. 
#I defined image that will be used for the app.
FROM node:9.9.0-alpine

#This line defines default work directory of the container.
WORKDIR /usr/src/app

#This line copies node configuation files into the work directory. (package.json and package-lock.json)
COPY package*.json ./

#This line runes npm command that installs npm packages needed for running application with specified version.
RUN npm install npm@5.6.0
#This line removes all the node packages not needed for the application, after the application is built.
RUN rm -rf /usr/local/lib/node_modules/npm
#This line moves the correct and needed (predefined version) packages to the default node modules directory.
RUN mv node_modules/npm /usr/local/lib/node_modules/npm

#This line copies entire source code from repo to my node container.
COPY . .

#This line exposes port 8081 for node app.
EXPOSE 8081
#This line start our application (index.js file).
CMD [ "node", "index.js" ]


#Node container by default has /usr/local/lib/node_modules/npm directory. 
#If I didnt remove this package I would get an error.
#This is related only to this specified version of npm. If I ran just npm install I wouldnt have to do it.