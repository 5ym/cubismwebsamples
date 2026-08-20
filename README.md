# cubismwebsamples

[Cubism Web Samples](https://github.com/Live2D/CubismWebSamples) のデモを GitHub Pages に公開するためだけのリポジトリ。

公開先: https://5ym.github.io/cubismwebsamples/

## 何が入っているか

SDK のソースコードは持っていない。持っているのはワークフローだけ。

```
.github/workflows/pages.yml   # SDK を取得してビルドし、Pages に配信する
```

`pages.yml` が実行時に [Cubism SDK for Web](https://www.live2d.com/download/cubism-sdk/download-web/) の
公式配布 zip を取得し、`Samples/TypeScript/Demo` をビルドして `dist` をそのまま Pages の
ルートとして配信する。

GitHub の [Live2D/CubismWebSamples](https://github.com/Live2D/CubismWebSamples) には
Cubism Core の本体 (`Core/live2dcubismcore.js`) が含まれておらず、リポジトリを clone しただけでは
ビルドできない。一方で公式配布 zip には Core / Framework / Samples がすべて揃っているため、
zip だけを唯一の取得元にしている。

## バージョンを上げる

`pages.yml` の `CUBISM_SDK_VERSION` を書き換えて develop に push するだけ。

```yaml
env:
  CUBISM_SDK_VERSION: "5-r.5"
```

指定できる値は [Live2D/CubismWebSamples のタグ](https://github.com/Live2D/CubismWebSamples/tags)
と同じ形式 (`5-r.5`, `5-r.4`, ...)。Core と Framework と Resources のバージョンが zip 内で
揃っているので、組み合わせのズレ (Core が古くて新しい `.moc3` を読めない等) は起きない。

## ライセンス

このリポジトリは Live2D の配布物を一切含まない。デモに含まれるコードやモデルの利用条件は
配布元のライセンスに従う。

* [Live2D Open Software License Agreement](https://www.live2d.com/eula/live2d-open-software-license-agreement_ja.html) (Framework / Samples)
* [Live2D Proprietary Software License Agreement](https://www.live2d.com/eula/live2d-proprietary-software-license-agreement_ja.html) (Cubism Core)
