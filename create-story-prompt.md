#### **ステップ0：プロジェクトの開始**

1.  `projects`フォルダ内に、新しい物語のためのフォルダを作成します（例：`Project_C_Ocean_Symphony`）。
2.  `_templates`フォルダから4つの`prompt_*.md`ファイルを、新しいプロジェクトフォルダ内の対応する階層（`01_World/`など）にコピーし、名前を`_prompt_used.md`に変更します。これにより、その生成に使ったプロンプトのバージョンを記録できます。

#### **ステップ1：World（世界観の構築）**

1.  **入力:** `01_World/input.md`に、世界観の核となる3つのキーワードを記述します。
2.  **実行:** `01_World/_prompt_used.md`に、`01_World/input.md`の内容を組み込んでAIに与えます。
3.  **中間出力:** AIからの生成結果を`01_World/output_raw.md`として保存します。
4.  **★レビュー＆最終化:** `output_raw.md`を人間が確認し、必要に応じて修正・加筆します。完成した世界観パッケージを`01_World/final.md`として保存します。

#### **ステップ2：Character（キャラクターの創造）**

1.  **入力:** `02_Character/input.md`に、キャラクターのキーワードを記述します。
2.  **実行:** `02_Character/_prompt_used.md`に、**`01_World/final.md`**（前の工程の最終版）と`02_Character/input.md`の内容を組み込んでAIに与えます。
3.  **中間出力:** AIからの生成結果を`02_Character/output_raw.md`として保存します。
4.  **★レビュー＆最終化:** `output_raw.md`をレビューし、完成したキャラクターシートを`02_Character/final.md`として保存します。

#### **ステップ3：Plot（プロットの構築）**

1.  **入力:** `03_Plot/input.md`に、プロットのキーワードを記述します。
2.  **実行:** `03_Plot/_prompt_used.md`に、**`01_World/final.md`**、**`02_Character/final.md`**、そして`03_Plot/input.md`の内容を組み込んでAIに与えます。
3.  **中間出力:** AIからの生成結果を`03_Plot/output_raw.md`として保存します。
4.  **★レビュー＆最終化:** `output_raw.md`をレビューし、完成したプロット概要を`03_Plot/final.md`として保存します。

#### **ステップ4：Context（本文の執筆）**

1.  **入力:** `04_Context/input.md`に、執筆したいシーンなどを指定します。
2.  **実行:** `04_Context/_prompt_used.md`に、これまでの**すべての`final.md`ファイル**と`04_Context/input.md`の内容を組み込んでAIに与えます。
3.  **中間出力:** AIからの生成結果を`04_Context/output_raw.md`として保存します。
4.  **★レビュー＆最終化:** `output_raw.md`を推敲し、物語の完成稿を`04_Context/final.md`として保存します。

この改善された構造により、各工程の成果物が明確にバージョン管理され、上書きの心配なく複数のプロジェクトやアイデアを試すことが可能になります。