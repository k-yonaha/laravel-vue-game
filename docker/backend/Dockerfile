FROM php:8.1-fpm

# 作業ディレクトリ
WORKDIR /var/www/html

RUN apt-get update && apt-get install -y \
    libpng-dev libjpeg-dev libfreetype6-dev zip unzip git \
    && docker-php-ext-install pdo pdo_mysql

# Composerインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# プロジェクトファイルをコピー
COPY ./backend/ /var/www/html

# パーミッション設定
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html \
    && chmod -R 775 /var/www/html/storage \
    && chmod -R 775 /var/www/html/bootstrap/cache

# キャッシュをクリーンアップしてイメージサイズを減らす
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Composerで依存関係をインストール
RUN composer install --no-dev --optimize-autoloader

# デフォルトコマンド
CMD ["php-fpm"]