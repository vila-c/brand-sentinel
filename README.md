# 小红书笔记情绪分析 - PyTorch 实现  
# Xiaohongshu (XHS) Sentiment Analysis with PyTorch

一个学习型项目：爬取小红书笔记 → 存储到 SQL → 情绪分析（基线 vs 深度学习）→ 可视化结果。  
A learning project: Crawl Xiaohongshu posts → Store in SQL → Sentiment analysis (baseline vs deep learning) → Visualization.

---

## 📌 项目简介 | Project Overview
本项目以小红书笔记为数据源，展示完整的 NLP 情绪分析流程：  
- 数据采集与 SQL 存储  
- 基线模型（SnowNLP / VADER）  
- 进阶模型（中文 BERT 微调，PyTorch + HuggingFace）  
- Plotly/Streamlit 可视化  

This project demonstrates a full NLP sentiment pipeline using Xiaohongshu posts:  
- Data collection & SQL storage  
- Baseline models (SnowNLP / VADER)  
- Advanced model (fine-tuned Chinese BERT with PyTorch + HuggingFace)  
- Interactive visualization with Plotly/Streamlit  

---

## 🛠 技术栈 | Tech Stack
- Python 3.9+, pandas, numpy  
- SQLAlchemy + SQLite/PostgreSQL  
- HuggingFace Transformers, PyTorch  
- SnowNLP, VADER  
- Plotly, Streamlit  
- 爬虫参考：[Spider_XHS](https://github.com/cv-cat/Spider_XHS)  

---

## 📂 项目结构 | Project Structure
brand-sentinel/
├── README.md               # 项目说明文档
├── data/                  # 原始数据 & SQL schema
├── notebooks/             # Jupyter demo 笔记本
├── src/                   # 核心代码
│   ├── data_ingest.py     # 数据采集与入库
│   ├── model_train.py     # 模型训练与评估
│   ├── visualization.py    # 可视化逻辑
├── requirements.txt        # 依赖库清单
└── future_work.md         # 未来扩展计划

---

## 🔄 子项目拆分 | Sub-projects
- **A. 数据采集与 SQL 存储**  
- **B. 数据处理与情绪建模**  
- **C. 分析与可视化**  
- **D. 部署与扩展**  

---

## 💻 Demo 区域 | Demo Code
```python
# 基线 - SnowNLP
from snownlp import SnowNLP
text = "这款面膜真的很好用！毛孔都变小了～"
s = SnowNLP(text)
print(f"情感得分: {s.sentiments:.3f}")  # >0.5 偏正面

# 进阶 - BERT
from transformers import pipeline
sentiment_pipeline = pipeline("sentiment-analysis", model="uer/roberta-base-finetuned-dianping-chinese")
result = sentiment_pipeline("这款面膜真的很好用！毛孔都变小了～")
print(result)  # [{'label': 'POSITIVE', 'score': 0.998}]

📈 结果展示 | Result Showcase
Sentiment distribution (占位图)

Time trend (占位图)

🚀 未来改进方向 | Future Work
多语言支持（中文 + 英文）

Docker/Kubernetes 部署

增加更多数据源

📑 数据来源声明 | Data Source
本项目仅用于学习与技术展示，不涉及商业用途。实际运行请遵守小红书平台的数据使用政策。
This project is for learning and technical demonstration only, not for commercial use. Please follow Xiaohongshu’s data usage policies.
