# SD-Eval: A Benchmark Dataset for Spoken Dialogue Understanding Beyond Words

## 論文の位置付け

- パラ言語情報を用いた応答生成タスクにおける代表的なベンチマーク
- 提案法の有効性を示すための有力候補

## 研究背景

- 音声対応LLMやSpeech/Audio-LLMの進展により，音声入力の対話システムが発展
- 従来評価は発話内容の語彙的意味中心で，感情・アクセント・年齢・環境音など「言葉以外」の情報に基づく応答の適切さを測る枠組みが不足
- 音声にはパラ言語情報や周辺環境情報が含まれ，発話意図理解や自然な応答に重要であるため，それらを対象にしたベンチマークが必要

## 提案手法

- SD-Eval という音声対話理解ベンチマークデータセットを提案
- 4つの観点（感情，アクセント，年齢，環境音）ごとのテストサブセットで構成
- 複数の既存音声データセットを統合・加工して構築
    - 一部はTTS音声合成や環境音付加を利用
- 各発話に対する応答データを作成 (LLMによる複数パターン作成を含む)
- ベースラインとして以下の3系統を比較する
    - カスケード型：ASR（例：Whisper）で文字起こししてテキストLLMで応答生成
    - エンドツーエンド型（VS-LLM）：音声エンコーダ表現を直接LLMに入力して応答生成
    - 上限モデル：正解文字起こしやラベル情報を与える設定
- 評価はBLEU/ROUGE/BERTScore等の自動指標に加え，LLM評価および人手評価も用いて妥当性を検証

## 長所と短所

### 長所

- 言葉以外の要因に基づく応答生成能力を体系的に評価可能
- 音声を直接扱うエンドツーエンド型モデルが有利になり得ることを示した
- LLMによる自動評価が人手評価と高相関になり得る点を示した

### 短所

- 単発のspeech-to-text応答に限定され，speech-to-speechやマルチターン対話は対象外
- 観点が4種類に限定され，他の話者属性・社会的要因などは未カバー
- 応答生成や一部構築にLLMを用いるため，LLM由来のバイアスが入る可能性

## .bibtex

```bibtex
@article{ao2024sd,
  title   = "Sd-eval: A benchmark dataset for spoken dialogue understanding beyond words",
  author  = "Ao, Junyi and Wang, Yuancheng and Tian, Xiaohai and Chen, Dekun and Zhang, Jun and Lu, Lu and Wang, Yuxuan and Li, Haizhou and Wu, Zhizheng",
  journal = "Advances in Neural Information Processing Systems",
  volume  = "37",
  number  = "",
  pages   = "56898--56918",
  year    = 2024
}
```
