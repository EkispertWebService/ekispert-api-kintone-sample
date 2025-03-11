# 駅すぱあと API HTML5インターフェースkintone連携サンプルプログラム

「駅すぱあと API」の[HTML5インターフェースサンプル](https://github.com/EkispertWebService/GUI)とkintoneアプリを連携するサンプルプログラムです。

kintoneアプリに「駅すぱあと API」のGUIパーツを利用し、駅検索、経路検索、経路の料金取得といった交通費申請に必要な機能を組み込むことができます。

サンプルプログラムは、kintoneがサンプルアプリとして提供している「交通費申請サンプルアプリ」に組み込むものになっており、すぐに試すことができます。<br>
また、ソースコードは自由に改変することが可能となっており、どのkintoneアプリにも組み込んで利用していただくことができます。
  
なお、サンプルとしてのご提供のため、動作保証やお問い合わせ等のサポートは承っておりません。  
利用条件については[こちら](https://github.com/EkispertWebService/ekispert-api-kintone-sample/blob/main/LICENSE.md)をご確認ください。

# 前提条件
* kintoneのアカウントを所持している
* 「駅すぱあと API」の、kintone用として利用可能なスタンダードプランのアクセスキーを所持している
    * アクセスキーの発行はドメイン毎です。別用途で使っているキーの転用はできません。
    * アクセスキーをお持ちでない場合は[こちら](https://api-info.ekispert.com/form/trial/)からお申込みいただけます。
* [駅すぱあと API HTML5インターフェース](https://github.com/EkispertWebService/GUI)（GUIパーツ）をダウンロードしている
* 本リポジトリをダウンロードしている

# 利用方法
## 1. サンプルアプリの追加
* 以下のサイトを参考に「交通費申請」サンプルアプリをkintone上に作成します。
    * [サンプルアプリを追加する | kintone ヘルプ](https://jp.cybozu.help/k/ja/user/create_app/add_app_store.html)
    * 「交通費申請」サンプルアプリ: [交通費申請 - kintone（キントーン）- すぐに使えるサンプルアプリ | サイボウズの業務改善プラットフォーム](https://kintone-sol.cybozu.co.jp/apps/027-kotsuhi.html)
## 2. 駅すぱあと APIのアクセスキーの設定
* 「本リポジトリ」の「ekispert-api-kintone-sample.js」の以下の部分にアクセスキーを設定
```ekispert-api-kintone-sample.js
        // 駅すぱあとWebサービスのアクセスキー
        var ekispertAccessKey = 'アクセスキーを指定してください';
```
## 3. サンプルアプリの変更
※ kintoneの操作については以下を参照

 [フォームを設定する | kintone ヘルプ](https://jp.cybozu.help/k/ja/app/form/design/set_form.html)

 [JavaScriptやCSSでアプリをカスタマイズする | kintone ヘルプ](https://jp.cybozu.help/k/ja/app/customize/js_customize.html)

1. 「フォーム」の変更
    * 「タイトル」の横に「スペース」を追加
        * 「要素ID」に「course-result-space」を設定
    * テーブルに「交通手段」の「ドロップテーブル」の設定を変更
        * 「項目と順番」に「駅すぱあと」を作成
        * 「フィールドコード」に「交通手段」を設定
    * テーブルの「訪問先」の列の横に「文字列（1行）」の列を追加
        * 「フィールド名」に「経路」を設定
        * 「フィールドコード」に「経路」を設定
2. 「設定」> 「JavaScript / CSSでカスタマイズ」の変更
    * PC用のJavaScript / CSSファイルのJavaScriptファイルの「URL指定で追加」で、以下のURLを追加
        * https://js.cybozu.com/jquery/3.7.1/jquery.min.js
        * https://js.cybozu.com/sweetalert2/v7.3.5/sweetalert2.min.js
    * PC用のJavaScript / CSSファイルのJavaScriptファイルの「アップロードして追加」で、以下のファイルを追加
        * 「駅すぱあと API HTML5インターフェース」の「expGuiCourse.js」、「expGuiStation.js」、「expGuiCondition.js」
        * 「本リポジトリ」の「ekispert-api-kintone-sample.js」
    * PC用のJavaScript / CSSファイルのCSSファイルの「URL指定で追加」で、以下のURLを追加
        * https://js.cybozu.com/sweetalert2/v7.3.5/sweetalert2.min.css
    * PC用のJavaScript / CSSファイルのCSSファイルの「アップロードして追加」で、以下のファイルを追加
        * 「駅すぱあと API HTML5インターフェース」の「expGuiCourse.css」、「expGuiStation.css」、「expGuiCondition.css」
        * 「本リポジトリ」の「ekispert-api-kintone-sample.css」
3. アプリの更新を実行
4. レコードを新規作成し、「交通手段」から「駅すぱあと」を選択し、駅入力画面が表示されることを確認