# ベースとなるイメージを指定。この場合はバージョンまで特定のタグを指定している。
FROM nginx:1.17.6-alpine

# ホストPCの設定ファイル(config/nginx.conf)を上で作成したディレクトリへコピーして送る
#RUN mkdir -p /etc/nginx
RUN mkdir -p /etc/nginx /var/www/test
COPY dockerfiles/nginx//nginx.conf /etc/nginx/nginx.conf
RUN echo "This is Test Page!" > /var/www/test/index.html
