# 建立自己的 benchmark

By 油成

## 作業說明
```plain
作業說明：

建立自己的benchmarks

建立一組你自己的基準測試（ prompts ）（可延伸詢問）
主題是你有興趣、有點懂的（才能分辨好壞）

測試 prompts 範例如下：

「請用 Python 寫一個程式，輸入圖的 adjacency matrix，判斷該圖是否連通。」

至少使用兩種以上的 LLM 來測試  （不要考你的 LLM  例如「IVE的成員是誰?」）
寫下你對這些模型回答的看法，你比較喜歡哪一個、為什麼
請以截圖的方式或以pdf繳交。

也可以自行增加內容。

-------------------------------------------------------------------------------------------------

繳交期限：10/06 23:59 （遲交期限：10月07日 下午 11:59）

繳交標題格式：學校 學號 系級 姓名 主題 (主題可打可不打) (學校、系級打簡稱即可)

繳交內容必須包含：

重點截圖or附上pdf檔。
寫對此份作業的重點說明，以及這些模型回答的看法。
-------------------------------------------------------------------------------------------------

評分標準：

0分：作答區中無附檔，且無截圖。

2分：繳交作業與本週主題無關(若貼成別週作業也列在此)

4分：只有比較一個LLM。

5 ~6分：(基本繳交分)沒有寫下對模型的看法或問題不合適。

8~10分：達成以上作業說明。
```

## Benchmark 測試

題目要求我出一個題目來詢問兩個以上的 LLM，正好我手邊剛好有 ChatGPT 5、Claude Sonnet 4.5、Gemini 2.5 Flash，我就來以「大學老師設計互動式示範程式」為題，來詢問這三個 LLM。

我使用的測試 prompt 如下：

```plain
請你扮演一個大學老師，設計一個關於「深度學習中的 Softmax 函數」的互動式示範程式，
並且使用 Python 的 Jupyter Notebook 來實作。
目的是為了讓學生能夠理解 Softmax 函數的特性，著重在它在多分類問題中的應用，以及「贏者通吃」效應。

這個程式應該包含以下功能：
1. 互動式的介面，讓使用者可以調整 Softmax 函數的輸入值。
2. 動態顯示 Softmax 函數的輸出結果。
3. 視覺化 Softmax 函數的特性，例如「贏者通吃」效應。
4. 提供詳細的程式碼說明，讓使用者可以理解每一部分的功能。
請你生成完整的 Jupyter Notebook 程式碼，並且在程式碼中加入詳細的註解說明。
```

## LLM 回應比較

以下是各個 LLM 的回應截圖：

| 評比項目 | ChatGPT 5 | Claude Sonnet 4.5 | Gemini 2.5 Flash |
|---|---|---|---|
| 回應速度 | 13 秒 | 約 1 分鐘 | 約 30 秒 |
| 回應完整度 | 完整 <br /> [🔗 Colab](https://drive.google.com/file/d/1C3LjESv3u4xZQqY5DYgqZ8ai5zHuZEBD/view?usp=sharing) | 非常完整 <br /> 🔗 [Colab](https://colab.research.google.com/drive/1aqWHdtOTtDoEw2V2Omn5rJ45vK-1N5X0?usp=sharing) | 較完整 <br />[🔗 Colab](https://colab.research.google.com/drive/11Btct_q4GXZtxBbm6CEwV0erSBROIpDt?usp=sharing) |
| 截圖 | ![ChatGPT 5 回應截圖](./softmax/chatgpt-5.png) | ![Claude Sonnet 4.5 回應截圖](./softmax/claude-sonnet-4.5.png) | ![Gemini 2.5 Flash 回應截圖](./softmax/gemini-2.5-flash.png) |
| 程式碼正確性 | 部分錯誤 | 正確、程式碼結構繁重 | 正確、模組化設計，好使用 |
| 提供檔案下載 | ✅  | ❌ | ❌ |
| 給予程式碼 | downloaded file | block code | block code |
| 程式碼說明 | 詳細，會繼續確認名詞解釋 | 詳細，問一次就夠了 | 一般，但容易引誘我繼續問下去 |
| 執行狀況 | 圖表拖曳後無法正確顯示圖表 <br /> ![](./chatgpt-ipywidgets/slider1.png) <br /> ![](./chatgpt-ipywidgets/slider2.png) | 操作滑桿後，圖表會正確地更新 <br /> Adjust 1 <br /> ![](./claude-graph/SCR-20251006-ngfk.png) <br /> ![](./claude-graph/SCR-20251006-nggg.png) <br /> Adjust 2 <br /> ![](./claude-graph/SCR-20251006-nght.png) <br /> ![](./claude-graph/SCR-20251006-ngin.png) <br /> Adjust 3 <br /> ![](./claude-graph/SCR-20251006-ngjq.png) <br /> ![](./claude-graph/SCR-20251006-ngkh.png) <br /> Adjust 4 <br /> ![](./claude-graph/SCR-20251006-nglh.png) <br /> ![](./claude-graph/SCR-20251006-ngmk.png) | 比較多中國用語，例如「運行」、「滑塊」、「創建」等詞彙。<br /> 請看以下「五組 Logits 調整對 Softmax 輸出的影響分析」段落。 |
| 我對模型回答的看法 | 一如往常的「完整」，使用者會接收到一大坨的 code 與冗長的文字敘述，無論與使用者的需求是否有關。我在檢視 notebook 時，像是在閱讀天書一般，理解在做什麼的過程中有些負擔。 | 比較簡潔一點，該有的結果和 code 都有，沒什麼感覺。倒是使用過程中，遇到圖表為了顯示中文字但缺字型的提示訊息，我增加了 ignore command，warning message 還是沒能消掉，好怪。| Gemini 的結果我最滿意，回應和引導相較人性化許多，在操作的過程中我發現了 font warning message、調參數的問題，在這三個 LLM 裡，我最願意進一步請教 LLM 該怎麼調整、這些數值代表的意涵。 |

總結：我最喜歡 Gemini 2.5 Flash 設計的示範程式，雖然它在我周遭使用者的生態中不算太普及，正確率也不是最高，但它所設計的互動性和人性化設計，讓我願意花時間去操作和理解這個程式，有種「他知道使用者需要什麼，並且等待著使用者繼續探索與他互動」的感覺。


## 五組 Logits 調整對 Softmax 輸出的影響分析

| 圖片順序 | Logits (A, B, C) | Logits 差異 (最大 - 次大) | Softmax 輸出 (A, B, C) | 最高機率 Class | **Softmax 效應觀察** |
| :---: | :---: | :---: | :---: | :---: | :--- |
| **1. nypo (初始設定)** <br /> ![](./gemini-demo/SCR-20251006-nypo.png) | $[1.00, 2.00, 3.00]$ | $3.00 - 2.00 = 1.00$ | $[9.00\%, 24.47\%, 66.52\%]$ | **C** | Logits 差值為 1，Softmax 明顯將 C 類別機率推高到 $\approx 66.52\%$。 |
| **2. nzec (拉開差異)** <br /> ![](./gemini-demo/SCR-20251006-nzec.png) | $[0.20, 2.00, 3.00]$ | $3.00 - 2.00 = 1.00$ | $[4.26\%, 25.75\%, 69.99\%]$ | **C** | **Logit A 大幅降低** (從 1.00 $\rightarrow$ 0.20)，其機率從 9.00% **被壓縮**到 4.26%。Logit C 和 B 的比重因此輕微增加。 |
| **3. nzhp (改變贏家)** <br /> ![](./gemini-demo/SCR-20251006-nzhp.png) | $[0.20, 2.00, 1.20]$ | $2.00 - 1.20 = 0.80$ | $[10.24\%, 61.93\%, 27.83\%]$ | **B** | **贏家轉移**：Logit B (2.00) 成為最大值。即使 B 和 C 的差值只有 0.80，**B 的機率仍達到近 62\%**，展示了 Softmax 快速將「信心」轉移到新贏家。 |
| **4. nzpi (全面負值)** <br /> ![](./gemini-demo/SCR-20251006-nzpi.png) | $[-2.40, -3.90, -1.90]$ | $-1.90 - (-2.40) = 0.50$ | $[34.82\%, 7.77\%, 57.41\%]$ | **C** | **Logits 絕對值不重要**：儘管所有 Logits 都是負數，Softmax 仍將它們轉化為有效的機率。最大 Logit $\mathbf{C (-1.90)}$ 仍被推高到 $\approx 57.41\%$。 |
| **5. oaan (極端負值)** <br /> ![](./gemini-demo/SCR-20251006-oaan.png) | $[-0.60, -3.90, -1.90]$ | $-0.60 - (-1.90) = 1.30$ | $[76.37\%, 2.82\%, 20.81\%]$ | **A** | **最強烈的「贏者通吃」**：Logit A (-0.60) 遠大於 Logit B (-3.90) 和 Logit C (-1.90)。 Softmax 將 Logit A 的機率推到 **76.37\%**，證明了**相對較大的 Logit (哪怕是負值)**，都會被 Softmax 極端強化。 |

### 結論

透過這五組實驗，我們可以得出以下關於 Softmax 函數的幾個重要結論：

#### 1. **Softmax 關注 Logits 的相對大小，而非絕對值**

* 無論 Logits 是正數 (如圖 1, 2, 3) 還是負數 (如圖 4, 5)，Softmax 都能將它們轉換成 0 到 1 之間的機率。
* 例如，圖 1 的 $[1, 2, 3]$ 和圖 5 的 $[-0.6, -3.9, -1.9]$，儘管數值差異巨大，但 Softmax 總是將**相對最高的** Logit 轉換為最高的機率。

#### 2. **「贏者通吃」效應極為顯著**

* Softmax 的指數運算 $e^z$ 會**放大** Logits 之間的微小差異。
* 在圖 3 中，Logit B (2.00) 僅比 Logit C (1.20) 大了 0.80，但 B 的機率 (61.93%) 遠高於 C 的機率 (27.83%)，這就是模型判斷的信心被強化的表現。

#### 3. **相對領先者將獲得不成比例的機率**

* 在圖 5 中，Logit A (-0.60) 相對於 B (-3.90) 和 C (-1.90) 取得了 $1.30$ 以上的領先優勢，其結果是 A 獲得了超過 $\mathbf{76\%}$ 的機率。
* 這表明，在多分類任務中，Softmax 使得模型在面對略微優勢的輸入時，可以**非常自信**地做出最終分類預測。

這裡展示了 Softmax 如何將模型的原始信心分數（Logits）轉化為清晰且可解釋的最終決策（機率分佈）。

### 名詞解釋

> Logits 是神經網路倒數第二層（或最後一層的線性輸出）的結果。簡單來說，它就是模型為每個類別計算出的一個原始分數。代表模型對每個類別的傾向性或信心強度。數值越大，代表模型越傾向於該類別。

> Softmax 函數 是 Logits 和最終預測機率之間的橋樑。它是一個活化函數，用於將一組 Logits 轉換成一個有效的機率分佈。
    > 1. 轉換為機率：讓模型輸出可以被解釋為**「屬於每個類別的機率」。
    > 2. 「贏者通吃」效應：指數運算會放大** Logits 之間的相對差異，使得最高的 Logit 轉換為接近 1 的機率，而其他機率值被壓縮（如同我們在示範程式中看到的）。

> Class N 是一個通用的術語，指的是一個多分類問題中的第 N 個類別。
    > 定義：在一個包含 K 個可能結果的分類任務中，Class N 代表其中的一個特定標籤或類別。
    > 例如：如果我們有一個圖像識別任務，分類 K=3 種動物： - Class 1: 貓 - Class 2: 狗 - Class 3: 鳥
    > 與 Logits/Softmax 的關係：神經網路的輸出層通常有 K 個節點，每個節點都對應一個 Class N。這些節點輸出的就是Logits，經過 Softmax 轉換後，模型就會給出一個關於每個 Class N 的機率。

> 流程：$$\text{輸入數值} \rightarrow \text{多層網路運算} \rightarrow \underbrace{\text{輸出 } K \text{ 個原始分數}}_{\text{Logits}} \rightarrow \underbrace{\text{Softmax 函數}}_{\text{活化}} \rightarrow \underbrace{\text{輸出 } K \text{ 個機率}}_{\text{機率分佈}} \rightarrow \underbrace{\text{選擇最高機率的類別}}_{\text{預測 Class N}}$$