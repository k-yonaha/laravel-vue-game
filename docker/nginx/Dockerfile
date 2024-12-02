FROM nginx:alpine

# Nginxの設定ファイルをコピー
COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf

# 本番用
#COPY ./frontend/dist /usr/share/nginx/html