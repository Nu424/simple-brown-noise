# Simple Brown Noise 🎧

静かに、集中を。ワンクリックで心地よいブラウンノイズを再生する、超シンプルなウェブツールです。🌊✨

---

## 🚀 使い方
- 🖥️ `index.html` をブラウザで開く
- ▶️ 再生を押す → 音量を調整（初期 20%、次回から自動復元）
- ⌨️ Space で再生/停止、↑/↓ で音量 ±5%

💡 `file://` で動かない場合はローカルサーバーで:
```bash
python -m http.server 8000
# http://localhost:8000/ にアクセス
```

## ✨ 特長
- 🎯 最小 UI（再生/停止 + 音量）で迷わない
- 🌓 ライト/ダーク自動対応の落ち着いたデザイン
- 🎚️ フェードで滑らかな音量変化、クリックノイズを抑制
- ♿ キーボード操作とアクセシビリティ配慮（`aria-pressed`, `aria-live`）
- 📄 外部依存なし・単一 HTML

## 🛠️ 技術メモ
- Web Audio API の AudioWorklet を使用して、ブラウンノイズ（Brownian noise, 積分ノイズ）を生成しています。
  - 近似実装: `lastOut = (lastOut + 0.02 * white) / 1.02` によりリークを持たせドリフトを抑制
  - ステレオ出力: 生成したチャンネルを複製
- 音量は `GainNode` を `linearRampToValueAtTime` で遷移させ、クリックノイズを抑制
- ユーザー操作後に `AudioContext` を初期化（モバイルブラウザ対策）

## ☁️ デプロイ
静的ホスティングに `index.html` を置くだけ（GitHub Pages / Netlify / Vercel など）。

## ⚠️ 注意
長時間・大音量は聴覚に負担となります。小音量で安全にご利用ください。

