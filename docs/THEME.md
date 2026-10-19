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
- 今は「スタンプの絵（キャラ）」から一式を作る作り。キャラのいないデザイン（ネオン・カーボン等）は未対応

## 出したもの
- Aotira Theme（あおティラの着せかえ、申請済み）
