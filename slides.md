---
theme: geist
layout: cover
class: 'text-center justify-center'
---

<style>
.cover h1 {
  line-height: 1.2;
  font-size: 50px;
}
.common h1 {
  line-height: 1.5;
}
.two-columns {
  gap: 20px;
}
.two-columns h1 {
  font-size: 30px;
}
</style>

# デザインシステムとは何を解決する仕組みなのか

takeda.k  

---
class: text-25px leading-normal
---

<style>
.slidev-vclick-target {
  padding-top: 20px
}
</style>

# はじめに
<div class='mt-8'>
最近デザインシステムやデザインエンジニアという言葉をよく目にするようになったけど。。。

<v-clicks>

- そもそもデザインシステムとは何なのか？

- どんな問題を解決するものなのか？

</v-clicks>

</div>

---
class: text-25px leading-normal
---

# デザインシステムとは

<div v-click="1">
  <p style="text-indent: -25px" class="-pl-15px">
  ・UIを構築する上で決められたデザインのルールや規則
  </p>
  <p class="text-14px mt-0 pt-0">例: 使用するfont, space, colorなどの値</p>
</div>

<div v-click="2">
  <p style="text-indent: -25px" class="-pl-15px mt-6">
    ・再利用可能なコンポーネントや定数など
  </p>
</div>

<div v-click="3">
  <p class="">
    ↑これらの集合体を指してデザインシステムと呼ぶ
  </p>
  <p class="text-14px mt-0 pt-0">（ここは現場によって多少解釈が異なりそうなので大体こういうものって分かっていればよさそう）</p>
</div>


---
layout: cover
class: text-center justify-center
---

# デザインシステムの目的

---
class: text-25px leading-normal
---

<style>
  ol {
    list-style: decimal!important;
  }
  blockquote {
    font-size: 12px;
    text-align: end;
    opacity: 0.5;
  }
</style>

1. 一貫性のあるデザインを実現し、プロダクトの体験を向上させる

<div class="mt-12" />

2. 判断基準を統一し、意思決定のスピードと質を高める

<div class="mt-12" />

3. 再利用可能な規則やコンポーネントを整備し、開発効率を向上させる

<div class="mt-8" />

> WEB + DB PRESS VOL.129 「小さく始めるデザインシステム」から引用


---
layout: cover
class: text-center justify-center
---

# もう少し具体的に考えてみる

---
class: common text-25px leading-normal
---

# 一貫性のあるデザインを実現し、プロダクトの体験を向上させる

<div v-click="1" class="leading-relaxed">
  → ここでいう「一貫性」とはどのように決まるものか
</div>

<div v-click="2" class="leading-relaxed">
  → ユーザーの認知負荷を軽くする（迷わずに利用させる）ために検証されたパターンをもとに決められるもの
</div>

<div v-click="3" class="leading-relaxed">
  → ユーザーに対する検証<sup>※</sup> によって決められた一貫性の実現でプロダクトの体験の向上を目指す
  <span class="text-16px block mt-4">※ A/Bテストやユーザビリティテストなどを想定しています</span>
</div>


---
class: common text-25px leading-normal
---

# 判断基準を統一し、意思決定のスピードと質を高める

<div v-click="1" class="leading-relaxed">
  → プロダクトに関わる人が増える・初期から関わっていたメンバーが抜けるなどのケースで判断基準（font, space, colorなど）がない場合、意思決定のコストが上がる
</div>

<div v-click="2" class="leading-relaxed">
  → メンバーがそれぞれ個人の解釈で意思決定をした結果、一貫性のあるデザインの維持が難しくなる
</div>

<div v-click="3" class="leading-relaxed">
  → 判断基準があることで開発における意思決定のコストを下げられる
</div>


---
class: common text-25px leading-normal
---

# 再利用可能な規則やコンポーネントを整備し、開発効率を向上させる

<div v-click="1" class="leading-relaxed">
  → 判断基準があるだけでは開発者同士が同じUIを作ってしまう（車輪の再発明が起きる）可能性がある
</div>

<div v-click="2" class="leading-relaxed">
  → 同じUIでも作る人が違えば差が出てしまい、一貫性を損ねる
</div>

<div v-click="3" class="leading-relaxed">
  → 開発においては共通部分のコンポーネント化、デザイナーとエンジニアのコミュケーションにおいては「Primary Button」といった共通言語などの整備をしておくことで一貫性を保ちつつ開発効率の向上を目指す
</div>

---
layout: cover
class: text-center justify-center
---

# 実際にデザインシステムをやってみる

---
layout: cover
class: text-center justify-center
---

# Style Dictionaryで<br>デザイントークンを実装する


---
class: common text-25px leading-normal
---

# デザイントークンとは何か

デザイントークンは、スペーシング、カラー、タイポグラフィー、オブジェクトスタイル、アニメーションなど、デザインシステムを構築し維持するために必要なすべての値をデータとして表現したものです。カラーはRGB値、不透明度は数値、アニメーションはベジェ座標など、デザインで定義されたあらゆるものを表現することができます。ハードコーディングされた値の代わりに使用することで、すべての製品体験において柔軟性と統一性を確保します。

> Adobe Spectrumから引用(https://spectrum.adobe.com/page/design-tokens/#What-are-design-tokens?)

<p class="text-16px mt-8 leading-relaxed">スタイルを直書きするのではなく変数や定数にして使い回すものという認識でok<br>デザインシステムの目的のうち「判断基準の統一」と「再利用可能な規則」を達成できる</p>


---
class: common text-25px leading-normal
---

# Style Dictionaryとは何か

Amazonが開発しているライブラリ  
JSONで定義したスタイルから（webに限らず）様々なプラットフォームに対応したデザイントークンを出力してくれるライブラリ

---
class: 'common text-20px leading-normal gap-2'
---

# 初期化コマンド

```bash
$ yarn init -y
$ npx style-dictionary init basic
```

<p class="text-16px">※ 公式のbasicテンプレートを使用</p>

---
class: 'common text-20px leading-normal gap-2'
---

# 初期化後のディレクトリ構造

<div class="flex gap-20px">
<div class="w-250px">

![style dictionary init](/style-dictionary-init.png)

</div>

- build → デザイントークンの出力先
- tokens → スタイルが定義されたJSON群
- config.json → style-dictionaryの設定ファイル（commonJS形式でも書ける）

</div>

---
layout: cover
class: text-center justify-center
---

# tokensの中身を覗いてみる👀

---
class: 'common text-20px leading-normal gap-2'
---

colorディレクトリの中では主に色に関するスタイルを定義している  

<div class="flex gap-20px">

![color](/color.png)

![color font](/color-font.png)

</div>

base.jsonでは汎用的な値を定義していることから**Primitive Token**、  
font.jsonでは意味的に定義していることから**Semantic Token**と呼ばれる。  
Semantic Tokenでは値をハードコーディングしないようにするため、必ずPrimitive Tokenから参照する。

---
layout: cover
class: text-center justify-center
---

# ビルドしてみる🔧

---
class: common text-20px leading-normal gap-2
---

## ビルドコマンド

```bash
$ npx style-dictionary build
```

## 出力例（SCSS）

<div class="w-400px">

![scss](/build-scss.png)
  
</div>
  
<p class="text-16px">※ CSS、JSもサポートしている</p>

---
class: common text-20px leading-normal gap-2
---

# まとめ

・デザインシステムとはデザインのルールや規則、再利用可能なコンポーネントの集合体のこと。

<p class="mb-0">・デザインシステムによって、</p>
<p class="pl-5　m-0">判断基準を統一し、意思決定のスピードと質を高め</p>
<p class="pl-5 m-0">一貫性のあるデザインを実現し</p>
<p class="pl-5 m-0">開発効率とプロダクトの体験を向上させることができる。</p>

・デザイントークンはデザインの規則を決められるのと同時に再利用可能にできる仕組み

---
class: common text-20px leading-normal gap-2
---

# もっと知りたい人へのおすすめ

・[WEB + DB PRESS VOL.129 「小さく始めるデザインシステム」](https://www.amazon.co.jp/WEB-DB-PRESS-Vol-129-%E3%81%86%E3%81%B2%E3%82%87/dp/429712890X?crid=2BQT0G3QQAPBA&keywords=web+db+press&qid=1656296002&sprefix=web%2Bdb,aps,188&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExTzhUT1ZBUzBYWVRLJmVuY3J5cHRlZElkPUEwMzIxNDI3MlRSWVhNTUkxVU9IMCZlbmNyeXB0ZWRBZElkPUEzTDBPVjhKUFgwNEJPJndpZGdldE5hbWU9c3BfYXRmJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ%3D%3D&linkCode=shr&tag=keisuke6906-22&language=ja_JP&ref_=as_li_ss_shr&creativeASIN=429712890X&camp=1207&creative=undefined&linkId=686e7e1c8cb8052cec9684276b6cfcfa)

・[デザインシステムの目的を考える](https://note.com/seyanote/n/ne8b5a0576f5e)

・[グッドパッチエンジニアが選ぶ、推しデザインシステム10選](https://goodpatch.com/blog/i-love-design-systems)
