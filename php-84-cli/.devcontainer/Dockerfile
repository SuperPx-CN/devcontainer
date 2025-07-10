# 使用 PHP 8.4（预览版）
FROM php:8.4.10-cli

# 安装依赖工具和扩展
RUN apt-get update && apt-get install -y \
    git zip unzip curl libzip-dev libpng-dev libonig-dev \
    && docker-php-ext-install zip

# 安装 Composer
RUN curl -sS https://getcomposer.org/installer | php -- \
    && mv composer.phar /usr/local/bin/composer

# 设置工作目录
WORKDIR /workspace

# 添加用户（可选）
ARG USERNAME=dev
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && chown -R $USERNAME:$USERNAME /workspace

USER $USERNAME
