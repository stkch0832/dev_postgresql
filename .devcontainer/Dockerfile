# ベース OS として Ubuntu 22.04 を使用
FROM ubuntu:22.04

# 対話プロンプトを出さないようにする設定
ENV DEBIAN_FRONTEND=noninteractive

# OS 更新と必要なパッケージ（PostgreSQL 含む）のインストール
RUN apt-get update \
    && apt-get install -y \
        postgresql \
        postgresql-contrib \
        sudo \
        git \
        vim \
        curl \
        wget \
        zip \
        unzip \
        less \
        locales \
    # 日本語ロケールを生成
    && locale-gen ja_JP.UTF-8 \
    # apt キャッシュ削除（イメージを軽量化）
    && rm -rf /var/lib/apt/lists/*

# コンテナのデフォルトロケール設定を日本語にする
ENV LANG=ja_JP.UTF-8
ENV LC_ALL=ja_JP.UTF-8

# PostgreSQL の待受ポート
EXPOSE 5432

# PostgreSQL データディレクトリ（Ubuntu デフォルト）
# 例: /var/lib/postgresql/14/main
VOLUME ["/var/lib/postgresql"]

# PostgreSQL をフォアグラウンドで起動するコマンド
# ※ postgres ユーザーで実行する
CMD ["sh", "-c", "sudo -u postgres /usr/lib/postgresql/14/bin/postgres -D /var/lib/postgresql/14/main -c config_file=/etc/postgresql/14/main/postgresql.conf"]
