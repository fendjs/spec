Fend Specification
==================

# About

This document is written specifications and design policy.


# Document History

See also `HISTORY.md`.


# Concepts

- Rails のようなアプリケーション構造による Webアプリケーション開発の Rail 化
- クライアントサイドとサーバサイドで動作する isomorphic 的な JavaScript コード
- クライアントサイドとサーバサイドのレンダリングによる SEO のサポート
- クライアントサイドとサーバサイドで同じ HTML テンプレートの利用
- クライアントサイドとサーバサイドで同じルーティングロジックの利用
- Rails の Asset Pipeline のような、concat、minify された JavaScript、CSS などのリソース配信
- データバインディングによる View のレンダリング
- Pluggable なモジュール (Ex: View、Model、etc...) のサポート


# Architecture
Fend のアーキテクチャを以下の図に示す。

![Architecture](images/architecture.png) 

TODO: write description


# Components

![components](images/components.png) 

## App

## Routes

```js
module.exports = {
  // 'path/to' {
  //   method: 'controller#action'
  // }
  'users': {
    get: 'users#index',
    post: 'users#create'
  },
  'users/new': {
    get: 'users#new'
  },
  'users/:id/edit': {
    get: 'users#edit'
  },
  'users/:id': {
    get: 'users#show',
    put: 'users#update',
    delete: 'users#destroy'
  }
}
```

## Router

## Controller

```js
module.exports = {
  routes: {
    show: function *() {
      // route handling
    }
  },
  actions: {
    onSubmit: function () {
      // user intaraction handling
    }
  }
};
```

## Model

## Adapter

## View 

### Template Engine
デフォルトで使用するテンプレートエンジンの採用基準は以下のとおり。

- Running on the client and the server
- Fast
- Logic less
- Pure HTML markup

### Data Binding Engine
`component/reactive`を利用する。

## Template
レンダリングする際に必要なHTMLテンプレート。
テンプレートSyntaxはテンプレートエンジンに依存する。
レンダリング高速化のためにプリコンパイルする。


# Fundamental Technology
- Koa
- Component

# Application Directory Structure

# Module System
モジュールシステムは、CommonJS の `require()` スタイル。Component の `require()` を利用する。AMD 最初の段階ではサポートしない。


# Resource Build System
クライアントへ配信するリソースは、Component の builder を利用。Component の標準の builder がこちらの望むユースケースと合わなければ Component の bulder のプラグイン作って対応する。それでもできなければ、Grunt にするかも。


# Package Manager
## Client Side
クライアントサイドのパッケージマネジャーは Component。

## Server Side
サーバサイドは Node の npm をそのまま利用。


# Generator
プロジェクトファイルの生成は、これも Component のプラグインで対応。


# Test Enviroment
テスト環境は Rails のような環境は提供しない(と思う)。めんどい、いやユーザー側が自分で構築したいと思うので。


# TODO
- クライアントサイドのMV\*モデルはAngularスタイルにするか？それとも古典的なMVCにするか？
- クライアントサイドのgenerator対応はどうするか。`facebook/regenerator`で対応する？パフォーマンスが気になる。
- この `README.md` の英訳


# License

[MIT license](http://www.opensource.org/licenses/mit-license.php).


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/fendjs/spec/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
