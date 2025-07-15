# Narou-Maker2 ワークフロー図

## 4段階ストーリー生成プロセス

```mermaid
graph TD
    A[単語 + world-prompt] --> B[Phase 1: 世界観生成]
    B --> C[世界観 final.md]
    
    C --> D[Phase 2: キャラクター生成]
    E[character-prompt] --> D
    D --> F[キャラクター final.md]
    
    C --> G[Phase 3: プロット生成]
    F --> G
    H[plot-prompt] --> G
    G --> I[プロット final.md]
    
    C --> J[Phase 4: 本文生成]
    F --> J
    I --> J
    K[context-prompt] --> J
    J --> L[全章完成]
    
    subgraph "Phase 1: 世界観生成"
        B1[input.md] --> B2[AI処理<br/>_prompt_used.md]
        B2 --> B3[output_raw.md]
        B3 --> B4{人間レビュー}
        B4 -->|承認| B5[final.md]
        B4 -->|訂正要求| B6[修正指示]
        B6 --> B2
        B4 -->|前段階に戻る| B7[Phase 0に戻る]
    end
    
    subgraph "Phase 2: キャラクター生成"
        D1[世界観 + input.md] --> D2[AI処理<br/>_prompt_used.md]
        D2 --> D3[output_raw.md]
        D3 --> D4{人間レビュー}
        D4 -->|承認| D5[final.md]
        D4 -->|訂正要求| D6[修正指示]
        D6 --> D2
        D4 -->|前段階に戻る| D7[Phase 1に戻る]
        D7 --> B4
    end
    
    subgraph "Phase 3: プロット生成"
        G1[世界観 + キャラクター + input.md] --> G2[AI処理<br/>_prompt_used.md]
        G2 --> G3[output_raw.md]
        G3 --> G4{人間レビュー}
        G4 -->|承認| G5[final.md]
        G4 -->|訂正要求| G6[修正指示]
        G6 --> G2
        G4 -->|前段階に戻る| G7[Phase 2に戻る]
        G7 --> D4
    end
    
    subgraph "Phase 4: 本文生成"
        J1[世界観 + キャラクター + プロット + input.md] --> J2[章1開始]
        
        J2 --> J3[話1-3生成<br/>AI処理 2-3話分]
        J3 --> J4[output_raw.md]
        J4 --> J5{人間レビュー}
        J5 -->|承認| J6[話1-3 final.md]
        J5 -->|訂正要求| J7[修正指示]
        J7 --> J3
        J5 -->|前段階に戻る| J8[Phase 3に戻る]
        J8 --> G4
        
        J6 --> J9{章1完成？}
        J9 -->|未完成| J10[話4-6生成<br/>AI処理 2-3話分]
        J10 --> J11[output_raw.md]
        J11 --> J12{人間レビュー}
        J12 -->|承認| J13[話4-6 final.md]
        J12 -->|訂正要求| J14[修正指示]
        J14 --> J10
        J12 -->|前段階に戻る| J15[前の話群に戻る]
        J15 --> J5
        
        J13 --> J9
        J9 -->|完成| J16[章1完成]
        
        J16 --> J17{全章完成？}
        J17 -->|未完成| J18[章2開始]
        J18 --> J19[話1-3生成<br/>AI処理 2-3話分]
        J19 --> J20[output_raw.md]
        J20 --> J21{人間レビュー}
        J21 -->|承認| J22[話1-3 final.md]
        J21 -->|訂正要求| J23[修正指示]
        J23 --> J19
        J21 -->|前段階に戻る| J24[前章に戻る]
        J24 --> J12
        
        J22 --> J25{章2完成？}
        J25 -->|未完成| J26[話4-6生成...]
        J25 -->|完成| J27[章2完成]
        J27 --> J17
        
        J17 -->|完成| J28[全章完成]
    end
    
    style B fill:#e1f5fe
    style D fill:#f3e5f5
    style G fill:#e8f5e8
    style J fill:#fff3e0
    style B4 fill:#ffebee
    style D4 fill:#ffebee
    style G4 fill:#ffebee
    style J5 fill:#ffebee
    style J12 fill:#ffebee
    style J21 fill:#ffebee
    style J3 fill:#e8f5e8
    style J10 fill:#e8f5e8
    style J19 fill:#e8f5e8
```

## ワークフロー概要

### Phase 1: 世界観生成
- **入力**: 単語 + world-prompt
- **処理**: Layered World Building Method による世界設定構築
- **出力**: 世界観 final.md

### Phase 2: キャラクター生成
- **入力**: 世界観 + character-prompt  
- **処理**: Omnibus Adaptability アプローチによるキャラクター作成
- **出力**: キャラクター final.md（主人公中心）

### Phase 3: プロット生成
- **入力**: 世界観 + キャラクター + plot-prompt
- **処理**: Instant Entertainment Logic Model によるストーリー構造構築
- **出力**: プロット final.md

### Phase 4: 本文生成
- **入力**: 世界観 + キャラクター + プロット + context-prompt
- **処理**: Cinematic Description System による実際の物語執筆
- **出力**: 章・話単位での本文 final.md

## 品質管理システム

### 人間レビュープロセス
各段階で以下の選択肢が提供されます：
- ✅ **承認**: 次段階に進む
- 🔄 **訂正要求**: 同じ段階内で修正
- ↩️ **前段階に戻る**: 前の段階のレビューに戻る

### AI文字制限対応
Phase 4では以下のような分割処理を行います：
- **章単位**: 大きな区切りでの管理
- **話単位**: 2-3話ずつの実際の生成
- **段階的生成**: AIの処理能力に合わせた分割処理

## ファイル構造

各段階で以下のファイルが生成されます：
- `input.md`: 人間による入力・要求
- `_prompt_used.md`: 使用されたプロンプトテンプレート
- `output_raw.md`: AIによる生成結果
- `final.md`: 人間レビュー後の最終版

## 技術的特徴

- **反復改善**: 各段階での品質向上サイクル
- **柔軟な出戻り**: 前段階への遡及修正
- **段階的構築**: 基盤から応用への順次構築
- **制約対応**: AI処理能力制限への対応