# App Policies

複数アプリのプライバシーポリシーを private repository で管理し、公開してよい HTML だけを別の public repository に置くための作業用リポジトリです。

## Recommended Repository Setup

```text
app-policies/              # private repository
  apps/
    example-app/
      app-info.md
      privacy-policy-ja.md
  templates/
    privacy-policy-ja.md
  dist/                    # generated files, not committed

app-policies-public/       # public repository for GitHub Pages
  example-app/
    privacy-policy.html
  index.html
```

## Workflow

1. `templates/privacy-policy-ja.md` を元に、アプリごとのポリシーを `apps/<app-id>/privacy-policy-ja.md` に作成する。
2. `apps/<app-id>/app-info.md` に、公開URL、問い合わせ先、利用SDK、収集データなどを整理する。
3. HTML化したファイルだけを public repository に配置する。
4. public repository で GitHub Pages を有効化する。

## Public Repository Rules

public repository には、以下だけを置く運用にします。

- `privacy-policy.html`
- 必要な `index.html`
- 公開してよい CSS や画像

以下は置かないようにします。

- 下書き
- 内部メモ
- テンプレート
- 生成スクリプト
- 未公開アプリ名
- APIキー、秘密情報、管理用ID

## App Folder Naming

`apps/<app-id>/` の `<app-id>` は、URLに使いやすい小文字の英数字とハイフンがおすすめです。

```text
apps/my-timer/
apps/photo-notes/
apps/habit-calendar/
```

公開URLも同じ名前にすると管理しやすくなります。

```text
https://<github-user>.github.io/app-policies-public/my-timer/privacy-policy.html
```

## Notes

このリポジトリのテンプレートは一般的な雛形です。アプリの実態、利用SDK、対象地域、ストア要件に合わせて必ず内容を調整してください。
