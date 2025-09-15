# Usamos uma imagem base oficial do PHP 8.3 com FPM, que é ideal para o Nginx.
# Laravel 12 provavelmente exigirá no mínimo PHP 8.2 ou 8.3.
FROM php:8.3-fpm

# Define o diretório de trabalho
WORKDIR /var/www

# Instala dependências do sistema necessárias para as extensões PHP
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    unzip \
    libzip-dev \
    libonig-dev \
    libxml2-dev

# Limpa o cache do apt
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Instala as extensões PHP mais comuns para Laravel
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd zip

# Instala o Composer (gerenciador de dependências do PHP)
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Altera o proprietário dos arquivos para o usuário do FPM para evitar problemas de permissão
RUN chown -R www-data:www-data /var/www

# Expõe a porta 9000 para o FPM
EXPOSE 9000

# O comando padrão para iniciar o PHP-FPM
CMD ["php-fpm"]