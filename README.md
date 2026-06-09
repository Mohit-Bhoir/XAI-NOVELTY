# 🤖 Explainability-Driven Decision Gating for Risk-Controlled Algorithmic Trading

> **Making AI-powered trading systems transparent, trustworthy, and profitable**

A research project that uses **Explainable AI (XAI)** to validate and filter trading decisions made by deep neural networks, reducing unnecessary trades while maintaining profitability.

---

## 📖 What is This Project About? (Simple Explanation)

Imagine you have an AI system that predicts whether currency prices will go up or down. The problem? **AI systems are often "black boxes"** — they make predictions but you don't know *why* they made those predictions. This creates risk when real money is at stake.

This project solves that problem by:
1. **Training an AI model** to predict currency price movements
2. **Using explainability technology** to understand *which features* influenced each prediction
3. **Creating a decision gate** that only executes trades when the AI's reasoning is sound
4. **Reducing risky trades** while maintaining profitability

**Real-world impact:** The system reduces trading activity by ~60% while either maintaining or **improving** overall performance, resulting in lower transaction costs and more stable returns.

---

## 🎯 The Problem

Traditional AI-based trading systems face a critical challenge:

- ❌ **Black-box predictions:** AI models make predictions without explanations
- ❌ **Over-trading:** Systems execute too many trades, increasing transaction costs
- ❌ **Unreliable signals:** Many predictions lack strong evidence, leading to losses
- ❌ **Lack of trust:** Regulators and traders can't understand why trades are executed

This becomes especially problematic in high-frequency trading where every unnecessary trade costs money.

---

## ✨ The Solution

This project integrates **Explainable AI (XAI)** directly into the trading execution layer:

```
Traditional Approach:
Model Prediction → Execute Trade → (Later) Explain why trade was made

Our Approach:
Model Prediction → Explain WHY → Decision Gate → Execute Trade (only if explainable)
```

### How It Works:

1. **Feature Importance Analysis** — Uses SHAP (a mathematical method) to identify which factors influenced each prediction
2. **Confidence Filtering** — Only executes trades where supporting evidence is strong (>60th percentile)
3. **Risk Control** — Eliminates low-confidence signals before they become costly trades
4. **Performance Optimization** — Focuses on high-quality trading opportunities

---

## 📊 Key Results

Our research found impressive improvements:

| Metric | Result |
|--------|--------|
| **Trade Reduction** | ~60% fewer trades executed |
| **Cost Savings** | 47% - 70% reduction in transaction costs |
| **Performance** | Maintained or **improved** portfolio returns |
| **Equity Stability** | More consistent, stable returns over time |

### Visual Example:

```
Without Explainability-Based Gating:
500 trades executed → High transaction costs → Frequent losses from bad trades

With Explainability-Based Gating:
200 trades executed → Low transaction costs → Better quality trades → Better returns
```

---

## 🔑 Key Concepts Explained

### 1. **Algorithmic Trading**
Automated buying/selling of currency pairs (like EUR/USD) based on predictive models rather than human decisions.

### 2. **Deep Neural Networks (DNN)**
AI models inspired by how the brain works. They learn patterns from historical data to make predictions. Accurate but hard to interpret.

### 3. **SHAP (SHapley Additive exPlanations)**
A mathematical framework that explains which input features contributed to each prediction. Answers: "Why did the model predict this?"

### 4. **Explainable AI (XAI)**
The field of making AI decisions understandable to humans. Instead of just trusting the prediction, we understand *how* it was made.

### 5. **Decision Gating**
A filter mechanism that validates predictions before execution. Only allows trades that meet a confidence threshold based on explanation strength.

### 6. **Walk-Forward Validation**
A realistic testing method that simulates how the system would perform in live trading by training on past data and testing on future data.

---

## 📁 Project Structure

```
XAI NOVELTY/
│
├── README.md                          # This file
├── requirements.txt                   # Python dependencies
├── DNNModel.py                        # DNN model implementation
├── DNNStrategy.ipynb                  # Trading strategy notebook
│
├── Data Files:
│   ├── EURUSD_M15_2019-2025.csv      # Historical EUR/USD prices (15-minute intervals)
│   ├── wf_comparison_metrics.csv      # Performance metrics across walk-forward splits
│   ├── DNN_model.keras                # Trained neural network model
│   └── oanda.cfg                      # API configuration
│
├── Research Notebooks:
│   ├── NB_03_Deep_Learning.ipynb              # Deep learning fundamentals
│   ├── DNN_XAI.ipynb                          # XAI analysis of DNN predictions
│   ├── DNN_XAI_Iter.ipynb                     # Iterative XAI experiments
│   ├── DNN_OOS_2025_EURUSD_M15.ipynb          # Out-of-sample testing
│   ├── Results.ipynb                          # Final results and analysis
│   ├── WF_Comparison.ipynb                    # Walk-forward comparison
│   │
│   └── Workflow Notebooks (WF1-WF5):
│       ├── WF1.ipynb                         # Walk-forward split 1
│       ├── WF2.ipynb                         # Walk-forward split 2
│       ├── WF3.ipynb                         # Walk-forward split 3
│       ├── WF4.ipynb                         # Walk-forward split 4
│       └── WF5.ipynb                         # Walk-forward split 5
│
└── .gitignore                         # Git configuration
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Jupyter Notebook
- pip (Python package manager)

### Installation

1. **Clone or download the project**
   ```bash
   cd "XAI NOVELTY"
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Verify installation**
   ```bash
   python -c "import tensorflow, shap, keras; print('All dependencies installed!')"
   ```

### Running the Project

#### Option 1: Jupyter Notebooks (Recommended for exploration)
```bash
jupyter notebook
```
Then open any `.ipynb` file to explore the analysis step-by-step.

#### Option 2: Run the main strategy
```bash
python DNNModel.py
```

---

## 📈 Understanding the Results

### The Trade-Off Chart
The project demonstrates an optimal trade-off between:
- **Y-axis:** Performance gains (%)
- **X-axis:** Cost reduction (%)

All data points fall in the ideal zone: **lower costs + same/better performance**

### Equity Curves Over Time
The gated strategy shows:
- ✅ Smoother equity curves (less volatility)
- ✅ Fewer drawdowns (losses)
- ✅ More stable long-term returns
- ✅ Better resistance to market stress

---

## 🧠 How the Explainability Gate Works

### Step-by-Step Example:

1. **Model Predicts:** "Buy EUR/USD" (probability: 65%)

2. **Feature Analysis:** SHAP calculates which factors supported this prediction:
   - Simple Moving Average (Lag 2): +8% support
   - Directional Movement Indicator (Lag 1): +6% support
   - Momentum: +3% support
   - Other factors: Various contributions

3. **Confidence Score:** Total supporting evidence = 17%

4. **Decision Gate Check:** Is 17% > 60th percentile threshold?
   - If **YES** → Execute the trade (high confidence)
   - If **NO** → Skip the trade (low confidence)

5. **Result:** Only high-quality, well-supported trades are executed

### Visualization
The project includes SHAP waterfall plots showing exactly which features pushed the model to make each decision.

---

## 📊 Data Details

### Dataset
- **Asset:** EUR/USD (Euro to US Dollar exchange rate)
- **Time Period:** 2019-2025
- **Interval:** 15-minute bars (M15)
- **Data Source:** OANDA API
- **Features:** 35 technical indicators including:
  - Moving Averages
  - Bollinger Bands
  - Directional Movement Indicators
  - Momentum Indicators
  - Volatility Measures

### Training Approach
- **Walk-Forward Validation:** 5 separate training/testing periods
- Train: 2019-2020 → Test: 2021
- Train: 2019-2021 → Test: 2022
- Train: 2019-2022 → Test: 2023
- (And so on...)

This simulates real-world deployment where the model continuously learns from recent data.

---

## 🔬 Technical Architecture

### Model Components

```
┌─────────────────────────────────────────────┐
│  Input: Market Data & Technical Indicators  │
│         (35 features)                       │
└──────────────────┬──────────────────────────┘
                   │
┌──────────────────▼──────────────────────────┐
│  Deep Neural Network (DNN)                  │
│  - 5 hidden layers, 50 neurons each         │
│  - ReLU activation functions                │
│  - Dropout regularization                   │
│  - Output: Probability (0-1)                │
└──────────────────┬──────────────────────────┘
                   │
┌──────────────────▼──────────────────────────┐
│  SHAP Explainability Analysis              │
│  - Calculate feature importance            │
│  - Generate explanations                   │
│  - Assess confidence                       │
└──────────────────┬──────────────────────────┘
                   │
┌──────────────────▼──────────────────────────┐
│  Decision Gate                              │
│  - Compare against 60th percentile         │
│  - Accept/Reject trade                     │
└──────────────────┬──────────────────────────┘
                   │
┌──────────────────▼──────────────────────────┐
│  Trade Execution (only if confidence high)  │
│  - Execute during 12:00-16:00 UTC          │
│  - Include transaction costs                │
└─────────────────────────────────────────────┘
```

---

## 📚 Research Methodology

### Walk-Forward Testing
Unlike traditional backtesting, walk-forward validation:
- ✅ Avoids look-ahead bias (knowing future prices)
- ✅ Tests on completely unseen data
- ✅ Simulates realistic trading conditions
- ✅ Accounts for transaction costs
- ✅ Tests across different market regimes

### Comparison Strategy
Each walk-forward period compares:
1. **Baseline Strategy:** DNN without explainability gating
2. **Gated Strategy:** DNN with SHAP-based decision gating

This isolates the impact of explainability filtering.

---

## 💡 Key Insights & Learnings

1. **Quality Over Quantity**
   - Fewer, better trades outperform many mediocre trades
   - Transaction costs matter more than most traders realize

2. **Explainability ≠ Just Interpretation**
   - XAI can be an active control mechanism, not just a post-hoc analysis tool
   - Filtering by explanations improves actual trading performance

3. **Market Regime Independence**
   - The gating strategy performed consistently across different market conditions
   - Works in both favorable and challenging trading environments

4. **Stability Matters**
   - Smoother equity curves indicate lower risk
   - More consistent returns attract real investors

---

## 🔗 Using the OANDA API

The project uses live market data from OANDA. To set up:

1. Create an account at [OANDA](https://www.oanda.com/)
2. Generate an API token
3. Update `oanda.cfg` with your credentials
4. The system will fetch real EUR/USD data

---

## 📖 How to Read the Notebooks

**For Beginners:**
1. Start with `NB_03_Deep_Learning.ipynb` (conceptual foundation)
2. Then `DNN_XAI.ipynb` (see how explainability works)
3. Finally `Results.ipynb` (see the impact)

**For Technical Details:**
1. `DNNStrategy.ipynb` (full strategy implementation)
2. `WF_Comparison.ipynb` (detailed performance analysis)
3. Individual WF notebooks (dive into specific walk-forward periods)

---

## 🎓 Key References & Citations

This project builds on decades of research in:
- **Deep Learning for Finance:** Using neural networks for market predictions
- **Explainable AI:** SHAP values and feature attribution methods
- **Quantitative Trading:** Walk-forward validation and realistic backtesting

Primary references include:
- Lundberg & Lee (2017): "A Unified Approach to Interpreting Model Predictions" (SHAP)
- Conventional walk-forward backtesting methodology for algorithmic trading

---

## 🤝 Contributing & Future Work

### Potential Improvements
- [ ] Multi-asset trading (beyond EUR/USD)
- [ ] Adaptive threshold methods (instead of fixed 60th percentile)
- [ ] Computational efficiency optimizations
- [ ] Real-time trading deployment
- [ ] Additional asset classes (stocks, commodities)

### Known Limitations
- Single time resolution (15-minute intervals)
- Single currency pair tested
- Fixed threshold approach
- Currently SHAP-only for explanations (could expand to LIME, etc.)

---

## ⚠️ Disclaimer

**This is a research project, not investment advice.**

- Past performance does not guarantee future results
- Trading involves risk of loss
- Use this research for educational purposes
- Consult financial professionals before trading real money
- Market conditions change; strategies must adapt

---

## 📞 Support & Questions

For questions about:
- **Deep Learning:** See the DNN model in `DNNModel.py`
- **SHAP Explainability:** Check `DNN_XAI.ipynb`
- **Trading Logic:** Review `DNNStrategy.ipynb`
- **Results:** Explore `Results.ipynb` and `WF_Comparison.ipynb`

---

## 📄 License & Citation

If you use this research, please cite it as:

```
Bhoir, M. N., Rosner, A., Ichtev, A., Golcarenarenji, G., & Gegov, A. (2026).
Explainability-Driven Decision Gating for Risk-Controlled Algorithmic Trading.
IEEE International Conference Proceedings.
```

---

## 🎯 Summary

This project demonstrates that **Explainable AI can be more than just an interpretation tool** — it can actively improve trading performance by filtering out low-confidence predictions. By reducing unnecessary trades and focusing on high-quality opportunities, the system achieves:

- **60% reduction** in trading activity
- **47-70% reduction** in transaction costs  
- **Maintained or improved** portfolio performance
- **More stable** and predictable returns

This opens new possibilities for responsible, trustworthy AI in finance.

---

**Last Updated:** June 2026  
**Status:** Research Complete ✅
