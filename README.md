# 基于 Python 的药物数据分析与可视化

> 课程作业项目：Linux 与 Python 编程基础

## 1. 项目目的

本项目面向 Python 初学者，使用 **Pandas** 整理药物数据，使用 **Matplotlib** 绘制图表，并在 Jupyter Notebook 中展示完整分析过程。

项目将回答以下简单问题：

- 数据中有哪些治疗领域和药物类别？
- 不同治疗领域的药品盒装价格是否存在差异？
- 药品规格（毫克数）与盒装价格之间是否有直观关系？
- 数据中是否有缺失值或重复记录，应该怎样处理？

## 2. 数据来源与说明

`data.csv` 是为本课程**人工生成的教学模拟数据**，不是临床用药建议、真实市场价格或药品说明书资料。药物名称、治疗领域和数值仅用于练习数据处理及可视化。

数据包含以下字段：

| 字段 | 含义 |
| --- | --- |
| `drug_id` | 模拟药物记录编号 |
| `drug_name` | 药物通用名或教学示例名称 |
| `therapeutic_area` | 治疗领域 |
| `dosage_mg` | 单次规格（mg） |
| `unit_price_cny` | 模拟盒装价格（元） |
| `prescription_type` | 处方药或非处方药 |
| `storage_condition` | 建议储存条件（教学示例） |
| `manufacturer_type` | 模拟生产企业类型 |

数据故意包含少量缺失值和一条近似重复的药物记录，以便练习数据清洗。

## 3. 文件结构

```text
drug-data-analysis/
├── analysis.ipynb      # 主分析 Notebook
├── data.csv            # 教学模拟数据
├── requirements.txt    # Python 依赖
├── .gitignore          # Git 忽略规则
└── README.md           # 项目说明（本文件）
```

## 4. 环境配置

建议先安装 Python 3.10 或更高版本。以下命令可在 Linux 终端、Windows PowerShell 或 VS Code 终端中执行。

```bash
# 创建虚拟环境（建议执行）
python -m venv .venv

# Linux / macOS 激活虚拟环境
source .venv/bin/activate

# Windows PowerShell 激活虚拟环境
.venv\Scripts\Activate.ps1

# 安装所需软件包
pip install -r requirements.txt
```

## 5. 运行方法

在本项目目录运行：

```bash
jupyter notebook
```

浏览器打开后，点击 `analysis.ipynb`。在 Notebook 菜单选择 **Run All Cells（全部运行）**，即可从数据读取到图表输出完整运行。

也可以在 VS Code 中安装 Python 与 Jupyter 扩展后，直接打开 `analysis.ipynb` 并选择 Python 内核。

## 6. 分析内容

Notebook 按以下顺序开展分析：

1. 导入 Pandas 和 Matplotlib，读取 CSV 文件；
2. 查看前几行、数据类型、缺失值和重复记录；
3. 将数值列转换为数字类型，用中位数补全缺失的规格和价格；
4. 去除同一药物的重复规格记录；
5. 计算总体描述性统计量，以及治疗领域分组统计；
6. 绘制治疗领域平均价格柱状图、规格与价格散点图、价格分布直方图；
7. 用简单文字总结观察到的结果与局限性。

## 7. 主要结果（基于模拟数据）

运行 Notebook 后可看到：

- 不同治疗领域的平均模拟盒装价格有一定差别；
- 较大规格的药物不一定更贵，说明价格还可能受剂型、企业类型和市场因素影响；
- 少数缺失值经中位数补全后可以继续开展基础教学分析；
- 这些图表仅说明本模拟样本的特点，不能用于药品定价、采购或临床决策。

## 8. Git 版本管理

本项目已初始化 Git 仓库。提交作业前，可使用以下命令查看和保存自己的修改：

```bash
git status
git add .
git commit -m "更新药物数据分析"
git log --oneline
```

如果需要提交项目链接，可以在 GitHub 新建空仓库后执行（将链接替换成自己的仓库地址）：

```bash
git remote add origin https://github.com/你的用户名/drug-data-analysis.git
git branch -M main
git push -u origin main
```

## 9. 可复现性说明

- 数据文件随项目一同保存，不依赖外部下载；
- `requirements.txt` 固定了依赖包版本；
- Notebook 中固定了绘图风格，并以相对路径读取同目录数据；
- 从干净环境安装依赖后，按“全部运行”即可复现分析流程。
