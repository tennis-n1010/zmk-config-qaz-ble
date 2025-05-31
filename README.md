# QAZ BLE

QAZ BLE は、30〜40%サイズ・QAZ配列・BLE/USB 両対応の自作キーボードです。ZMK ファームウェアを搭載し、スプリット・各種スペースバーサイズ対応の多レイアウト設計を実現しています。

![QAZ BLE キーボードイメージ](docs/img/qaz_ble_top.jpg) <!-- ※後で画像を差し替え -->

---

## 🔧 主な仕様

| 項目          | 内容                                                                 |
|---------------|----------------------------------------------------------------------|
| MCU           | Seeeduino XIAO nRF52840（充電 IC 付き）                               |
| ファームウェア | [ZMK Firmware](https://zmk.dev/)（Zephyr 3.5 / `west` build）         |
| 接続方式      | Bluetooth LE / USB（両対応）                                          |
| キーマトリクス | 5 × 8 col-to-row（最大 40 key）＋ 側面タクタイル 3 key              |
| レイアウト対応| WK / HHKB / WKL × (SPLIT, 4.25u, 6.25u Space) ― 計 9 パターン       |
| ビルド方法    | GitHub Actions による自動ビルド／UF2 出力                             |

---

## 🧱 リポジトリ構成

qaz_ble/
├── app.overlay             # ZMK用の本体設定
├── boards/                 # Seeeduino XIAO 用 board 定義
├── config/                 # センサー、電源まわりの設定
├── keymap/                 # 各レイアウトのキー定義
│   └── layouts/            # 9種レイアウトの定義を一括管理
├── .github/workflows/     # GitHub Actions 定義
├── README.md               # ← 本ファイル
└── …

---

## 📦 ファームウェアのビルド方法

1. 必要な環境のインストール（`west`, Python, Zephyr SDKなど）
2. リポジトリをクローンして初期化：

```bash
git clone https://github.com/yourname/qaz_ble.git
cd qaz_ble
west init -l .
west update
```
3.	ビルド：
```
west build -s zmk/app -d build/qaz_ble -- -DSHIELD=qaz_ble
```

4.	出力された .uf2 をXIAOへドラッグ＆ドロップで書き込み

⸻

🛠 組立・ペアリング方法

→ docs/build_guide.md を参照（作成中）
	•	ハンダ付け例
	•	ケース組立の注意点
	•	初回書き込み手順
	•	BLE ペアリング手順

⸻

📲 ZMK Studio 対応状況
	•	release/qaz_ble ブランチにて .keymap 出力対応
	•	すべての9レイアウトがZMK Studio上で選択・書込み可能

⸻

📥 リリースとダウンロード
	•	タグ v1.0.0 以降のリリースに .uf2 を自動添付予定
	•	Releases をチェック

⸻

🧪 今後の予定
	•	ケース設計の確定 → ガーバー公開
	•	組立ガイドに写真追加
	•	CI で keymap サイズチェック追加

⸻

📸 ギャラリー

<!-- 実機写真をあとでここに並べる -->



⸻

ライセンス

MIT License

⸻


---

この構成なら、あとから「docs/build_guide.md」や画像ファイルを足すだけで完成度高く見えるようにしてあるよ。  
必要に応じて、「ZMK Studio 用 .keymap ダウンロード」や「PCBデータ」へのリンクも入れようか？

修正・追加したいところがあれば教えて！
