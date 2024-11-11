#FROM node:18.17-alpine AS FRONTEND
#
#WORKDIR /app
#COPY . /app
#RUN yarn && yarn build

# FRONTEND EXPOSE
FROM nginx:stable-alpine

#ARG VUE_APP_VERSION=production

#COPY --from=FRONTEND /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]