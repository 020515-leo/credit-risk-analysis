# 信贷风险数据分析项目
> 基于Lending Club的金融风控探索 | [完整代码](credit-risk-analysis.ipynb)

## 业务价值
为消费信贷机构识别高风险客户特征，降低坏账损失

## 📌 核心发现
### 1. 收入风险阈值效应
![收入分层分析](images/income_default.png)
- **关键转折点**：$40,000年收入  
- **高危群体**：<$30k人群违约率24.1%（均值16.5%）

### 2. DTI债务比风险分层
| DTI区间 | 违约率 | 风险等级 |
|---------|--------|----------|
| <30%    | 12.1%  | 🟢 低     |
| 30%-40% | 18.7%  | 🟡 中     |
| >40%    | 28.3%  | 🔴 高     |

**建议**：对DTI>35%客户提高利率浮动基准+15%

## 🛠 技术实现
```python
# 典型代码片段：风险特征计算
high_risk_flag = (df['annual_inc'] < 30000) & (df['dti'] > 40)
print(f"高危客户占比: {high_risk_flag.mean():.1%}")
```

| 技术环节       | 工具库                  | 应用案例                  |
|----------------|-------------------------|---------------------------|
| 数据清洗       | Pandas, NumPy          | 处理15%缺失值             |
| 可视化分析     | Matplotlib, Seaborn    | 生成6类风险图表           |
| 分析框架       | Jupyter Notebook       | 可复现分析流程            |

## 📂 项目结构
```
credit-risk-analysis/
├── notebooks/       # 完整分析代码
├── images/          # 分析图表
└── data/            # 样本数据(1000条)
```

## 快速开始
1. 安装依赖：`pip install -r requirements.txt`
2. 运行分析：`jupyter notebook notebooks/credit_risk_analysis.ipynb`
