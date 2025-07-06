# Laravel プロジェクトのセットアップ手順


## 1. リポジトリをクローンする
1. GitHub で対象リポジトリの **URL** をコピーします。 
2. cd <プロジェクト名> 
3. git clone <リポジトリのURL>

## 2. パッケージのインストール、設定ファイルの作成

```bash
# PHPパッケージのインストール
composer install
# 設定ファイルのテンプレートから新しい設定ファイルを作成
cp .env.example .env
# Laravelアプリケーションの暗号化キーを生成。.envのAPP_KEYに設定。セッションや暗号化に使用される。
php artisan key:generate
