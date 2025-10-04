# nginx用のDockerfile
FROM nginx:alpine

# nginx設定ファイルをコピー
COPY docker/nginx/nginx.conf /etc/nginx/nginx.conf

# Laravelのpublicディレクトリをマウントするための準備
RUN mkdir -p /var/www/laravel/public

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]