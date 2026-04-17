# 🚀 設備異常預測系統（Equipment Failure Prediction System）
### Machine Learning × Explainable AI × Predictive Maintenance

---

## 🧠 專案故事（Project Story）

在製造業或工業場景中，設備異常通常會帶來：

- ❌ 停機損失
- ❌ 維修成本上升
- ❌ 生產延誤

本專案目標是：

> 👉 **在設備故障發生前預測異常，並解釋原因**

因此不只做「預測」，還加入：

- Explainable AI（SHAP）
- 資料驗證（Production 思維）

---

## 🎯 專案亮點（Highlights）

- 🔍 三分類預測（正常 / 警告 / 異常）
- 🧠 RandomForest 機器學習模型
- 📊 SHAP 可解釋 AI（Explainable AI）
- 🛡️ 資料驗證層（避免錯誤輸入）
- ⚙️ 模組化設計（可擴展成系統）

---

# 🏭 設備狀態預測與 SHAP 模型解釋 (Equipment Status Prediction & XAI)

本專案使用**隨機森林分類器 (Random Forest Classifier)**，透過分析設備的感測器數據（溫度、壓力、振動），來自動預測機台設備的運行狀態（正常、警告、異常）。

同時，本專案導入了 **SHAP (SHapley Additive exPlanations)** 套件，為模型提供「可解釋性 AI (XAI)」的視覺化分析。這不僅能讓系統給出預測結果，還能清楚展示「為什麼」模型會做出這樣的判斷，協助工程師釐清各項感測器特徵對預測結果的具體影響。

---

## ✨ 核心功能

1. **資料防呆與驗證**：內建 `validate_sensor_data` 函式，自動檢查輸入資料的型態與合理區間（不可為負數），避免異常資料導致系統錯誤。
2. **機器學習預測**：使用 `scikit-learn` 訓練隨機森林模型，並透過測試集自動產出準確率 (Accuracy) 與分類報告。
3. **預測 API 封裝**：提供獨立的 `predict_equipment_status_ml` 預測函式，方便未來輕鬆串接後端 API 或即時感測器資料流。
4. **全域與局部模型解釋 (SHAP)**：
   * **Summary Plot (全域解釋)**：針對「正常」、「警告」、「異常」三個類別，分別繪製特徵重要度分佈圖。
   * **Waterfall Plot (局部解釋)**：針對單一筆測試資料，以瀑布圖解析該筆預測結果的加分/扣分因素。
---
### 2. SHAP 視覺化圖表

> **⚠️ 重要提示：**
> 為了在 README 中顯示圖表，你需要先上傳產生的圖片檔，並將下方的佔位符鏈接替換為你實際上傳的鏈接。

執行完畢後，程式會自動使用 Matplotlib 彈出以下分析圖表。這些圖表解釋了各個特徵（溫度、壓力、振動）對模型預測特定類別的影響。

#### 全域解釋：多類別 SHAP Summary Plot

對於多分類問題，SHAP 會對每個類別單獨繪製一張 Summary Plot。以下是本專案中針對三個類別產出的圖表：

**1. 類別: 正常 (Normal)**

(<img width="753" height="260" alt="output" src="https://github.com/user-attachments/assets/30a81610-0206-414d-9510-bd14473ffc17" />)

* **解讀：** 藍色點（低特徵值）聚集在正向 SHAP 值（大於 0），表示當溫度、壓力和振動數值較低時，模型更傾向於預測設備狀態為「正常」。

**2. 類別: 異常 (Anomaly)**

(<img width="753" height="260" alt="output1" src="https://github.com/user-attachments/assets/579fbcbf-8f47-458c-ba92-9e01cbdcea81" />)

* **解讀：** 紅色點（高特徵值）聚集在正向 SHAP 值，表示當溫度、壓力和振動數值較高時，模型更傾向於預測設備狀態為「異常」。

**3. 類別: 警告 (Warning)**

(<img width="753" height="260" alt="output2" src="https://github.com/user-attachments/assets/9f64c304-10d6-4025-a360-544da0931cfd" />)

* **解讀：** 特徵值的影響呈現分佈。特定區間的特徵值高低會將模型推向預測「警告」狀態。

---

#### 圖表閱讀通用說明：
* **X 軸 (SHAP 值)：** 表示該特徵對模型輸出機率的影響。大於 0 表示增加預測該類別的機率，小於 0 表示減少機率。
* **顏色的含義：** 顏色的深淺代表特徵值的數值大小（紅色表示高，藍色表示低）。

---

#### 局部解釋：單筆測試資料 SHAP Waterfall Plot

除了全域解釋，專案還提供對特定單一筆資料的解釋。以下是一個瀑布圖範例，用於解構模型對單一筆預測結果的判斷過程。

(<img width="753" height="260" alt="output3" src="https://github.com/user-attachments/assets/90d5e55c-d8b3-457c-b47b-259ff8b4d9d6" />)

* **解讀：** 此圖呈現了各個特徵如何從模型的基準預測機率 (`E[X]`) 開始，進行加分或扣分，最終推移至該筆資料的預測結果。這能幫助開發者理解模型對具體案例的決策邏輯。




---

## 🛠️ 環境需求

請確保你的 Python 環境已安裝以下套件：

```bash
pip install pandas scikit-learn shap matplotlib
