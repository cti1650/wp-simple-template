FROM wordpress:latest

# 必要なツール郡をインストール
RUN apt-get update
RUN apt-get -y install wget unzip

# WP テーマ (zip) ダウンロード
WORKDIR /tmp/wp-themes

# WP プラグイン (zip) ダウンロード
WORKDIR /tmp/wp-plugins
RUN wget https://downloads.wordpress.org/plugin/contact-form-7.4.6.zip
RUN wget https://downloads.wordpress.org/plugin/syntaxhighlighter.zip
RUN wget https://downloads.wordpress.org/plugin/wp-emmet.zip
RUN wget https://downloads.wordpress.org/plugin/all-in-one-seo-pack.4.4.7.zip
RUN wget https://downloads.wordpress.org/plugin/all-in-one-wp-migration.7.78.zip
RUN wget https://downloads.wordpress.org/plugin/wp-multibyte-patch.2.9.zip
RUN wget https://downloads.wordpress.org/plugin/stops-core-theme-and-plugin-updates.9.0.17.zip
RUN wget https://downloads.wordpress.org/plugin/broken-link-checker.2.2.2.zip

# Zip ファイルを解凍してインストール
RUN unzip './*.zip' -d /usr/src/wordpress/wp-content/plugins

# 不要になった一時ファイルを削除
RUN apt-get clean
RUN rm -rf /tmp/*

# サーバが読めるように wp-content 以下の所有者を変更
RUN chown -R www-data:www-data /usr/src/wordpress/wp-content

WORKDIR /var/www/html