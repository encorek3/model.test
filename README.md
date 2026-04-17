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

## 🛠️ 環境需求

請確保你的 Python 環境已安裝以下套件：

```bash
pip install pandas scikit-learn shap matplotlib
