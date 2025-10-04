# 手順

## 事前準備
- /docker/Dockerfileを使用してイメージをbuild
  - $ docker build -t agafumiya/laravel-demo:latest -f docker/Dockerfile
- 起動確認  
  - $ docker run -p 8080:8000 agafumiya/laravel-demo:latest
- イメージをdockerhubにpush
  - $ docker push agafumiya/laravel-demo:latest
- Githubにこのソースコードリポジトリをアップしておく

## kindでクラスタ作成
- $ kind create cluster --name laravel-argo --config kind-config.yaml

## ArgoCDインストール
- 名前空間を用意してインストール
  - $ kubectl create namespace argocd
  - $ kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
- 起動確認
  - $ kubectl -n argocd get pods
  - $ kubectl -n argocd port-forward svc/argocd-server 8081:443
- ArgoCDのログインパスワードを取得
  - ユーザー: admin
  - $ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

## ArgoCd起動
- $ kubectl apply -f argocd-app.yaml
- $ kubectl -n argocd get applications
- Laravel: http://localhost:8080
- Argo CD: https://localhost:30081