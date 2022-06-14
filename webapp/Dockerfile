# 使用 node 镜像
FROM node:16 AS build
# 容器内的目录
WORKDIR /webapp
COPY . .

# 下载依赖包，并构建打包文件
RUN yarn && yarn build

FROM nginx
EXPOSE 3000
COPY ./nginx/web_default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /webapp/build /usr/share/nginx/html
