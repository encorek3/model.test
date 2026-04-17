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

## 🖼️ 視覺化展示（Visualization）

### 🔸 SHAP 全域特徵重要度

![SHAP Summary](images/shap_summary.png)

👉 顯示哪些特徵最影響設備異常

---

### 🔸 單筆預測解釋

![SHAP Waterfall](images/shap_waterfall.png)

👉 解釋為什麼這筆資料被判定為「異常」

---

## 🧭 Demo

```python
predict_equipment_status_ml(110, 160, 18)
