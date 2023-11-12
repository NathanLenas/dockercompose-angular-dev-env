# Use this dockerfile to build the production image of the angular app
# Needs to be run from the root of the project
# Stage 1: Compile and Build angular codebase

FROM node:latest as build

WORKDIR /usr/local/app

COPY ./ /usr/local/app/

RUN npm install

RUN npm run build


# Stage 2: Serve app with nginx server

FROM nginx:latest

COPY --from=build /usr/local/app/dist/angular-15-crud /usr/share/nginx/html

EXPOSE 80