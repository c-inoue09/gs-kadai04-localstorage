# コーデ記録アプリ 〜井上以外誰も得しない、略して「daretoku」〜
<img src ="https://user-images.githubusercontent.com/113824527/201226971-c443ebf2-055e-4af2-a551-2a8701a8906b.png" width="600px">

## ①課題内容（どんな作品か）
- もしかして同じ服ばかり着ているのかもという自覚があります。服装を記録することで、次の日のコーディネートの参考になるかと思って作りました。

- 主な機能
  - カレンダービューから任意の日時を押下すると詳細画面が開く
  - 詳細画面でトップスとボトムスを選択して保存すると、カレンダービューにその日のコーディネートが反映される
  - カレンダービューはローカルストレージに保存される

## ②工夫した点・こだわった点
- ローカルストレージに配列を記録
  - 服以外の要素も記録したかったので、拡張性を考えて1日ぶんのレコードは配列でもたせ、stringify/parseで操作できるようにしました
  - 実装が間に合わなかったけど、仕事/飲み会/原宿校 etc...の情報を記録するための「occasion」という残骸が残っていたりします

- ゴリっとカレンダービュー
  - カレンダーの基本的な部分はコピペです
  - 一定期間のコーディネートを俯瞰して見たい！という趣旨のアプリなので、改造して上下のアイテムが視覚的にわかるようにしました

- モバイル前提のUI
  - 自分は面倒くさがりで、こういうジャーナルっぽいアプリは絶対にPC立ち上げてまで記録したりしないので、UIはモバイルだけ考えました

## ③難しかった点・次回トライしたいこと(又は機能)
### 難しかったこと・シェアしたいこと
- 【4時間溶けた】日付のdivのidを動的に「YYMMDD」の形式で生成する
  - いちど数字を文字列にする→文字列操作とif文を使って整形
  - カレンダーが生成されたタイミングでidを付与する

- 【3時間溶けた】ロードしたタイミングでローカルストレージから画像読み出し
  - 今も実はうまくいっていない…

- 【2時間溶けた】後から追加したDOM要素に.click()をかけると効かない
  - 要素に対してではなく、documentに対してイベントを設定する必要がある

### 次回トライしたい機能
- アイテムをGUIで追加できるような機能(ユーザがカスタムできると良い)
- コーディネート保存後、同じ日を選択するとリセットされる仕様。本当は設定内容を呼び出したい
- 上下に分かれていない服(ワンピース)や靴も記録したかった

## ④質問・疑問・感想、シェアしたいこと等なんでも
### 質問・疑問
- 同じような変数名やクラス名やidをたくさん作ってしまって、いつか絶対ミスするな〜〜と思いました。どう設計するのが良いでしょう？
  - 具体例: outfitForTheDay, jsonOutfitForTheDay, savedOutfit, parsedOutfitForTheDay
  - 具体例: yymmdd, yymmddMin, yymmddForClass

###  参考記事
 - ローカルストレージ関連
   - [JSON.stringify](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
   - [[javscript]ローカルストレージにjson形式でデータを保存し、取得する](https://qiita.com/w-tdon/items/81034bd3006806f7d7c3)

 - jQuery
   - [jQueryでclickイベントが効かない場合の対処法！](https://qumeru.com/magazine/401)
   - [【保存版】jQueryセレクタの種類を指定方法を網羅的に徹底解説！](https://pengi-n.co.jp/blog/jquery-selecter/#i-2)
   - [addClassに変数を指定したらclassに設定されない](https://teratail.com/questions/335676)
   - [【jQuery入門】parent(), parent(), closestで親要素を取得する方法！](https://www.sejuku.net/blog/36261)
   - [jQueryでセレクタの指定で変数を使う方法を解説！](https://qumeru.com/magazine/250)
   - [ページ読み込み時にjavascript(jQuery)を実行する方法](https://arts-factory.net/javascript_load/)


 - JavaScript
   - [【初心者向け】JavaScriptでカレンダー作成【サンプル】](https://nyanblog2222.com/programming/javascript/2749/)
   - [JavaScriptの文字列操作（サンプル集でマスター）](https://qiita.com/saka212/items/11ce1f1d6316c1fbf15b)
   - [日付が1桁の時に0を追加して二桁にする方法！Javascriptの勉強](https://programmer-life.work/javascript/adjust-date)
   - [jQuery で複数のクラスをまとめて追加する方法](https://gotohayato.com/content/33/)
   - [jQueryのattr()でHTML属性の設定･取得･削除](https://www.flatflag.nir87.com/attr-1803)
   - [【JavaScript】動的にid属性を追加する方法](https://konoti.com/website/javascript/dynamic-id.html)
     - [【JavaScript】要素のid属性の値を取得する](https://into-the-program.com/javascript-get-value-element-id-attribute/#:~:text=API%2FElement%2Fid-,getAttribute%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%81%A7%E8%A6%81%E7%B4%A0%E3%81%AEid%E5%B1%9E%E6%80%A7%E3%81%AE%E5%80%A4%E3%82%92,%E3%81%99%E3%82%8B%E3%81%93%E3%81%A8%E3%81%8C%E3%81%A7%E3%81%8D%E3%81%BE%E3%81%99%E3%80%82)

 - HTML / CSS
   - [画像の高さを固定して横幅だけ伸縮させる方法](https://www.design-memo.com/coding/object-fit-property#:~:text=%E8%83%8C%E6%99%AF%E7%94%BB%E5%83%8F%E3%81%A7%E8%A1%A8%E7%A4%BA%E3%81%95%E3%81%9B%E3%82%8B,%E3%81%8C%E3%81%A7%E3%81%8D%E3%82%8B%E3%81%A8%E3%81%84%E3%81%86%E3%81%93%E3%81%A8%E3%81%A7%E3%81%99%E3%80%82&text=%E3%81%93%E3%81%AE%E3%82%88%E3%81%86%E3%81%AB%E3%80%81object%2Dfit,%E3%81%99%E3%82%8B%E3%82%88%E3%81%86%E3%81%AB%E3%81%AA%E3%82%8A%E3%81%BE%E3%81%99%E3%80%82)
   - [details/summaryタグでアコーディオンを作る](https://code-kitchen.dev/html/details-summary/)
