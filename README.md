# Babashka book

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Build

``` shell
$ script/compile
```

これは `asciidoctor` を使って、HTMLファイルを `gh-pages` ディレクトリに吐き出すものです。
`aciidoctor` をインストールするには、ドキュメント [ここ](https://asciidoctor.org/)を参照してください。

## Release

asciidoctorで作成したファイルはGithubで公開しています。これは[こちら](https://medium.com/linagora-engineering/deploying-your-js-app-to-github-pages-the-easy-way-or-not-1ef8c48424b7)のように設定されています。

以下のすべてのコマンドは、すでにgitプロジェクトが初期化されていて、そのルートフォルダにいることを前提としています。

```
# Create an orphan branch named gh-pages
git checkout --orphan gh-pages
# Remove all files from staging
git rm -rf .
# Create an empty commit so that you will be able to push on the branch next
git commit --allow-empty -m "Init empty branch"
# Push the branch
git push origin gh-pages
```

ブランチが作成され、オリジンにプッシュされたので、ワークツリーを正しく設定しましょう。

```
# Come back to master
git checkout master
# Add gh-pages to .gitignore
echo "gh-pages/" >> .gitignore
git worktree add gh-pages gh-pages
```

以上で、通常通り npm run build でアプリをビルドできるようになりました。gh-pages フォルダに cd してみると、現在は gh-pages ブランチになっていて、ルートフォルダに戻ると master に戻っていることがわかります。

Github Pagesにデプロイするには。

```
cd gh-pages
git add .
git commit -m "update build"
git push
```

## License

著作権 © 2020-2021 Michiel Borkent

Licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0)を使用しています。
