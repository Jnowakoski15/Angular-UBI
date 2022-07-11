FROM node as build
WORKDIR /app
COPY package*.json /app/
RUN npm install -g @angular/cli && \
    npm install
COPY . /app
RUN ng build

FROM nginx
COPY --from=build /app/dist/ubi-app /usr/share/nginx/html
COPY /nginx-custom.conf /etc/nginx/conf.d/default.conf