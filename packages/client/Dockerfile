#Builder
FROM node:18-alpine as builder

#Copy client packages
WORKDIR /usr/src/capacitor-react-nest-boilerplate
COPY package.json .
COPY packages/client packages/client


#install dependencies
RUN yarn install


#Build client
WORKDIR /usr/src/capacitor-react-nest-boilerplate/packages/client
#Install ionic cli
RUN yarn global add @ionic/cli
RUN ionic build

#Webserver
FROM public.ecr.aws/nginx/nginx:1.20-alpine
#Copy the nginx configuration
COPY packages/client/nginx.conf /etc/nginx/nginx.conf

COPY --from=builder /usr/src/capacitor-react-nest-boilerplate/packages/client/build /usr/share/nginx/html
EXPOSE 80

