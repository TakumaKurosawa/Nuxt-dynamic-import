# Nuxt 動的コンポーネントと動的インポートの検証

## 参考文献一覧

- [VUE.JS(NUXT)でCOMPONENTを動的に追加する](https://uniblo.tech/?p=231)

- [【Nuxt.js】コンポーネントの自動インポート](https://zenn.dev/kokota/articles/14beffb9e846f0)

- [Nuxt.jsのbundleサイズを55%削減したwebpack周りの小技
  ](https://qiita.com/hareku/items/d9f92c96697163356bd3#3-vuejs%E3%81%AE-dynamic-import20kb5kb)

- [Vue.js - 非同期コンポーネント](https://jp.vuejs.org/v2/guide/components-dynamic-async.html#%E9%9D%9E%E5%90%8C%E6%9C%9F%E3%82%B3%E3%83%B3%E3%83%9D%E3%83%BC%E3%83%8D%E3%83%B3%E3%83%88)

## 検証方法

- Nuxt（v2.15.7）環境準備
- components/ 配下に A ~ G のコンポーネントを用意
- pages/index.vue にてダイナミックインポートを実装
- vueの動的コンポーネントを用いて `:is="componentName"` とすることで、表示するコンポーネントを動的に変更できるようにした
- ビルド後のファイル一覧を見てBundleのされ方を確認
- ブラウザのNetworkを確認し、動的にJSファイルが読み込まれていることを確認

## 検証結果

ビルド後の `.nuxt/dist/client` を見ると下記の画像の通り、A ~ Gの各コンポーネントがminifyされていることがわかる。

<img width="295" alt="スクリーンショット 2021-07-02 12 37 05" src="https://user-images.githubusercontent.com/39955827/124216949-45278e00-db32-11eb-995d-2fc337b103e7.png">

これらのファイルがWebページ上のNetworkコンソールで確認したときに、どのタイミングでダウンロードされるかを検証した。

その結果、下記のGIFの通り、必要になったタイミングでのみダウンロードが走り、コンポーネント生成が行われることがわかった。

![demo](https://user-images.githubusercontent.com/39955827/124217507-70f74380-db33-11eb-804c-d7775446db41.gif)

念の為、Analyze結果も載せておく。

<img width="2538" alt="スクリーンショット 2021-07-02 12 48 01" src="https://user-images.githubusercontent.com/39955827/124217695-bfa4dd80-db33-11eb-814c-146f0f55f47d.png">
