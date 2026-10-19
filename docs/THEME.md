# LINE着せかえ メモ（作業用）

## LINE着せかえの画像一式（62枚・管理画面とガイドラインPDFで確認済み）
- メイン画像（すべて不透明）
  - ios_thumbnail.png 200×284
  - android_thumbnail.png 136×202
  - store_thumbnail.png 198×278
- メニューボタン（iOSのみ。Androidは同じ画像を使うのでa_のメニューは不要）128×150、OFF/ON
  - i_03/04 トーク、i_07/08 通話、i_25/26 ニュース、i_27/28 ウォレット、i_29/30 ホーム、
    i_31/32 TODAY、i_33/34 VOOM、i_35/36 ショッピング、i_37/38 アプリ（奇数=OFF、偶数=ON）
  - iOS26用 80×56：同じ番号に _g（例 i_29_g.png）
  - バッジは上から49px・右から21pxに出るので、そこに大事な絵を置かない
  - 公式見本ではONは別ポーズ（光る・色が付く）
- メニュー背景 i_11.png 1472×150
- パスコード i_12〜19 120×120 / a_12〜19 116×116（OFFとONが交互。公式見本はOFF=シルエット）
- プロフィール i_20/21 240×240 / a_20/21 247×247
- トーク背景 i_22 1482×1334 / a_22 1300×1300（各1MB以下）
- 「画像の数が一致しません」と出たら、余計なファイル（a_のメニューなど）が入っていないか確認

## ツールの実装（index.html、便利ツールの「🎨 着せかえ」タブ #x-theme）
- 関数：thChars, thChar, thThumb, thMenuBtn, thPass（OFFはsilhouette()）, thProfile, thMenuBg, thTalkBg,
  buildThemeFiles, drawThemePreview, ACT.downloadTheme
- TH_MENU_DEF = [['ホーム',29],['トーク',3],['VOOM',33],['TODAY',31],['ウォレット',27],['通話',7],['ニュース',25],['ショッピング',35],['アプリ',37]]
- 入力：#thMain/#thBg/#thAccent（色）, #thPattern, #thHero, #thSub, #thMenus, #thMenusOn, #thPass, #thIos26
- モード切替 #thModeSeg（thMode = 'chara' / 'custom'）。chara＝スタンプの絵から、custom＝自分の画像から

## 自分の画像で作る（custom、2026-10追加）
- 入れる所 thc：main / prof / prof2 / menuBg / talk（各1枚）、mOff・mOn（9）、pOff・pOn（4）。保存はIndexedDBのキー 'theme'
- まとめ画像の分割：ACT.thcSplit（横×縦、ふちを削る%、入れる先を選ぶ。左上から TH_MENUS の順）
- 背景の抜き方 thcCut：black＝黒を透明（光る絵向け、明るさ→透明度）／corner＝四すみの色を外側から消す／none
- OFF・ON thcAuto：auto＝OFF1枚から消灯(thcDim)と点灯(thcGlowImg)／onlyOn＝ONだけ自動／none。自分のON画像があればそれを優先
- パスコードは1つ目だけ入れれば4つ全部に使う
- メイン・プロフィール・メニュー背景・トーク背景は「すき間を埋める色」の上に中央で切り抜き（不透明になる）

## 書き出し前チェック（両モード共通 ACT.checkTheme → thCheck）
- 62枚（iOS26なしは44枚）、ファイル名、サイズ、空っぽの画像
- 不透明：メイン画像（透過不可）、メニュー背景の上0〜100px（透過不可）＝NG。プロフィール・トーク背景の透けは注意
- 容量：トーク背景1MB以下。超えたら pngIndexed で 256→128→64色のPNGにして軽くする（thLighten）
- 色：文字・吹き出しの色は自由に選べない。画像登録後に管理画面の「カラースキン」から選ぶ（黒系は白黒系スキン）。トーク背景色も指定できる

## 出したもの
- Aotira Theme（あおティラの着せかえ、申請済み）
