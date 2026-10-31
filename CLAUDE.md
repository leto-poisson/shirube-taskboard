# shirube-taskboard

## このプロジェクトについて
- しるべ（3人のリモートチーム）向けのタスクボード。目的：誰が何をいつまでにやるかを1画面で分かるようにする
- インフラ（AWS / Terraform / Docker / Kubernetes）のポートフォリオも兼ねる。アプリ部分は最小限に留める
- 詳しいゴール・スコープ外・成功の指標は README.md を参照

## 技術構成
- PHP 8.5.12（`docker/php/Dockerfile` でパッチ番号まで固定。8.5系のパッチ更新だけを追う）
- Laravel 13（`src/` 配下）
- nginx（`docker/nginx/default.conf`）、PostgreSQL 18
- ローカルは `docker compose` で起動。URL は http://localhost:8080
- 開発端末は Windows + PowerShell

## よく使うコマンド
- 起動: `docker compose up -d`（Dockerfile を変えた時は `--build` を付ける）
- 状態確認: `docker compose ps`
- artisan: `docker compose exec app php artisan <command>`
- composer: `docker compose exec app composer <command>`

## ルール
- ブランチ運用は GitHub Flow。main に直接コミットしない。作業は `feature/xxx` ブランチ → プルリクエスト → マージ
- `git add .` / `git add -A` は使わない。ファイルを指定して add し、コミット前に `git status` で `.env` が含まれていないことを確認する
- `.env` と `src/.env` は Git に上げない。DB のパスワードは両方で同じ値にする
- リポジトリ名・説明欄・コミットメッセージに、メンバー名や業務の具体的な情報を書かない
- 公開用のデータは架空のサンプルデータだけを使う
- README の「やらないこと」（チャット機能、LINE連携、ファイル共有）に入る機能は、提案する前に確認を取る

## 説明のしかた
- 開発初心者。手順は番号付きで、1ステップ＝1操作、各ステップに「完了の基準」を付ける
- コマンドは PowerShell 用に書く（コマンドプロンプト用ではない）
- 結論を最初に書く
