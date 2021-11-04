# specify the base image .
FROM node:alpine as builder

#  Spicify the working directory.
WORKDIR '/app'

COPY ./package.json ./

RUN npm install

# RUN apt-get update
# RUN apt-get install vim
#RUN apk add --update vim

COPY . .

# Tell the image what to do when it starts as a container.
# default command
#CMD ["npm","run","start"]
RUN npm run build


FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
