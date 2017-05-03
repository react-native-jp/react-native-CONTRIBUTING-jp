# React Native へのコントリビュート

React Native は Facebook のはじめてのオープンソースプロジェクトのひとつです。開発が非常に活発で、 [facebook.com](https://facebook.com) のみなさんにコードを配布するためにも使われています。我々はこのプロジェクトに気軽かつ透明性高くコントリビュートしていただくためにいろいろな問題へ対処中ですが、まだそこまでいたっていません。このドキュメントがコントリビュート方法を明確にし、あなたが持っている質問を解消することを願っています。

## 開発プロセス

コアチームメンバーのうち、数名は GitHub 上で直接作業しています。これらの変更は最初から公になされます。その他の変更は Facebook 内部のソース管理ツール由来のものになります。これは Facebook 外のコアチームメンバーが慣れた環境から迅速にコントリビュートするために必要なものです。

### `master` は安定していない

`master` が安定するよう、常にテストがすべて通るよう気を使っています。しかしすばやく開発を進めるために、互換性のない API 変更をすることがあります。こういった変更やバージョンについては適切に連絡するよう気をつけていますので、必要であれば特定バージョンを使い続けることも可能です。

### プルリクエスト

コアチームメンバーはプルリクエストを見ています。プルリクエストをもらうとまず、 Facebook での統合テストを実施します。その後マージされるためには、誰かによって承認される必要があります。 API 変更については Facebook 内部での使用にあたって問題解決をする必要があるため、時間をいただくことがあります。そういったプロセスについての最新情報やフィードバックを提供できるように最善を尽くします。

**プルリクエストは `master` ブランチに送ってください。**もし修正がクリティカルなもので、 stable なブランチにも取り込まれる必要のあるものの場合、その旨を伝えてください。プロジェクトのメンテナーによって cherry-pick されます。

プルリクエストを送る*前に*、次が完了していることを確認してください。

1. リポジトリーをフォークして `master` からあなたのブランチを生やしてください。
2. **テストプランをコミットメッセージに書いてください。**
  - テストが必要なコードを追加した場合、テストも追加してください !
  - API を変更した場合、ドキュメントも更新してください。
  - ドキュメントを更新した場合、可能であれば Web サイトを手元で確認してスクリーンショットを送ってください。

  ```
  $ cd website
  $ npm install && npm start
  次をブラウザーで開いてください: http://localhost:8079/react-native/index.html
  ```

3. 新規追加したすべてのファイルの先頭に著作権表示を記載してください。
4. Travis CI / CircleCI のテストが通ることを確認してください。
5. 静的解析がとおることを確認してください (`node linter.js <変更・追加したファイル>`) 。
6. まだ同意していない場合、 [CLA](https://code.facebook.com/cla) に同意してください。
7. コミットをひとつにまとめてください (`git rebase -i`) 。

   コミットをひとつにまとめる目的はレビュー者に対してあなたの意図を理解しやすくすることです。

> **注意:** プルリクエストページの `Merge master to your branch` を押し続ける必要はありません。コンフリクトした場合、テストが通らなかった場合は master をマージする必要があります。 Facebook-GitHub-Bot は最終的にマージする前にすべてのコミットをひとつにまとめます。

#### ファイルの著作権表示

次の文面を新規追加したファイルの先頭にコピー & ペーストしてください。

```JS
/**
 * Copyright (c) 2015-present, Facebook, Inc.
 * All rights reserved.
 *
 * This source code is licensed under the BSD-style license found in the
 * LICENSE file in the root directory of this source tree. An additional grant
 * of patent rights can be found in the PATENTS file in the same directory.
 */
```

新しいモジュールを追加した場合、コメントの最後に `@providesModule <モジュール名>` を追加してください。 haste パッケージマネージャーがモジュールを見つけ出すために必要なものです。

### Contributor License Agreement (CLA)

あなたのプルリクエストを受けいれるにあたって CLA に同意していただく必要があります。これは一度やれば大丈夫です。その他のオープンソースプロジェクトですでに登録済みの場合、特になにもする必要はありません。はじめてプルリクエストを送る場合、 CLA に同意したことを教えてください。あなたの GitHub ユーザー名でクロスチェックします。

[こちらから CLA に同意してください](https://code.facebook.com/cla)

## バグ

### 既知の問題

わかっているバグは GitHub Issues を使って管理しています。我々はいつも見て、内部の問題に進展があったとき、それが公になるように努めています。新しい問題を登録する前に、同様の問題がすでに登録されていないか探してください。

### Reporting New Issues

The best way to get your bug fixed is to provide a reduced test case. Please provide either a public repository with a runnable example or a [Sketch](https://sketch.expo.io/).

### Security Bugs

Facebook has a [bounty program](https://www.facebook.com/whitehat/) for the safe disclosure of security bugs. With that in mind, please do not file public issues; go through the process outlined on that page.

## How to Get in Touch

* [Facebook](https://www.facebook.com/groups/react.native.community/)
* [Twitter](https://www.twitter.com/reactnative)

## Style Guide

### Code

#### General

* **Most important: Look around.** Match the style you see used in the rest of the project. This includes formatting, naming things in code, naming things in documentation.
* Add trailing commas,
* 2 spaces for indentation (no tabs)
* "Attractive"

#### JavaScript

* Use semicolons;
* `'use strict';`
* Prefer `'` over `"`
* Do not use the optional parameters of `setTimeout` and `setInterval`
* 80 character line length

#### JSX

* Prefer `"` over `'` for string literal props
* When wrapping opening tags over multiple lines, place one prop per line
* `{}` of props should hug their values (no spaces)
* Place the closing `>` of opening tags on the same line as the last prop
* Place the closing `/>` of self-closing tags on their own line and left-align them with the opening `<`

#### Objective-C

* Space after `@property` declarations
* Brackets on *every* `if`, on the *same* line
* `- method`, `@interface`, and `@implementation` brackets on the following line
* *Try* to keep it around 80 characters line length (sometimes it's just not possible...)
* `*` operator goes with the variable name (e.g. `NSObject *variableName;`)

#### Java

* If a method call spans multiple lines closing bracket is on the same line as the last argument.
* If a method header doesn't fit on one line each argument goes on a separate line.
* 100 character line length

### Documentation

* Do not wrap lines at 80 characters - configure your editor to soft-wrap when editing documentation.

## License

By contributing to React Native, you agree that your contributions will be licensed under its BSD license.
