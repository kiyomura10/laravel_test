FROM nginx:1.27.5

#UTC +9
RUN apt-get update && \
    apt-get install -y tzdata && \
    ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

#パッケージのインストール
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    bash \
    curl \
    vim \
    openssl && \
    rm -r /var/lib/apt/lists/*

#設定ファイルの配置
COPY nginx-conf/nginx.conf /etc/nginx/nginx.conf
COPY nginx-conf/dev-laravel.techbull.cloud.conf /etc/nginx/conf.d/dev-laravel.techbull.cloud.conf
COPY ssl/dev-laravel.techbull.cloud-key.pem /etc/ssl/dev-laravel.techbull.cloud-key.pem
COPY ssl/dev-laravel.techbull.cloud.pem /etc/ssl/dev-laravel.techbull.cloud.pem

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
