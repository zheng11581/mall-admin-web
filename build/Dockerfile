FROM node:12.14.0 as build
WORKDIR /mall-admin-web
COPY . .
RUN npm config set registry https://registry.npm.taobao.org
RUN SASS_BINARY_SITE=https://npm.taobao.org/mirrors/node-sass/ npm install node-sass
RUN npm install
RUN npm run build

FROM nginx:1.22
WORKDIR /usr/share/nginx/html/
COPY --from=build /mall-admin-web/dist /usr/share/nginx/html/mall-admin-web
COPY --from=build /mall-admin-web/build/nginx.conf /etc/nginx/nginx.conf
CMD [ "nginx","-g","daemon off;" ]
