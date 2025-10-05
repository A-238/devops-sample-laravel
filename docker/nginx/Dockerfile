# nginx用のDockerfile
FROM nginx:alpine

# nginx設定ファイルをコピー
COPY docker/nginx/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]