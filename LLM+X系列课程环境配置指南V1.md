## 《LLM+X》环境配置指南

### 一、环境配置总览

根据课程进度，我们将分阶段配置环境：
- **第1-3周**：Python基础环境 + LLM开发环境
- **第4-5周**：产品设计工具
- **第6-10周**：全栈开发环境
- **第11-12周**：部署与商业化工具

### 二、基础环境配置清单（必装）

#### 1. 操作系统准备
**Windows用户**：
- ✅ 安装WSL2（Windows Subsystem for Linux）
- 推荐：Ubuntu 22.04 LTS
- 原因：后续Docker、部署等在Linux环境下更稳定

**Mac用户**：
- 安装Homebrew包管理器

#### 2. Python环境（第1周必装）
```
Python 3.10.x（推荐3.10.12）
├── 安装方式：Anaconda或Miniconda
├── 虚拟环境：conda create -n llm-saas python=3.10
└── 激活环境：conda activate llm-saas
```

#### 3. 深度学习框架（第2周必装）
```
PyTorch 2.0+（不需要TensorFlow）
├── CPU版本：适合无独立显卡同学
├── GPU版本：根据显卡选择CUDA版本
│   ├── NVIDIA显卡：安装对应CUDA
│   └── 查询命令：nvidia-smi
└── 安装命令：参考PyTorch官网选择器
```

#### 4. 代码编辑器（第1周必装）
- **VSCode**（推荐）+ 必装插件：
  - Python
  - Jupyter
  - GitLens
  - Docker
  - Remote-SSH（WSL用户必装）

### 三、LLM开发环境（第1-3周）

```bash
# 基础库安装
pip install transformers==4.36.0
pip install datasets
pip install accelerate
pip install sentencepiece
pip install protobuf

# API调用库
pip install openai
pip install anthropic
pip install langchain

# 数据处理
pip install pandas numpy
pip install matplotlib seaborn
pip install jupyter notebook
```

### 四、全栈开发环境（第4-10周）

#### 前端环境
```bash
# Node.js环境
Node.js 18.x LTS
npm 9.x
├── 安装Vue CLI：npm install -g @vue/cli
└── 安装Vite：npm install -g vite
```

#### 后端环境
```bash
# Java环境
JDK 17 LTS
├── 推荐：Amazon Corretto或OpenJDK
├── Maven 3.8+
└── 开发工具：IntelliJ IDEA Community（免费版够用）
```

#### 数据库环境
```bash
# 关系型数据库（二选一）
MySQL 8.0 或 PostgreSQL 15
├── 可视化工具：DBeaver
└── 本地开发推荐Docker安装

# 缓存数据库
Redis 7.0
└── 可视化工具：Redis Insight

# 图数据库（第10周）
Neo4j Community Edition 5.x
└── 包含Neo4j Browser
```

### 五、PDF处理与向量数据库（第6-9周）

```bash
# PDF处理
pip install pymupdf
pip install pdfplumber
pip install camelot-py[cv]

# 向量数据库（本地开发）
pip install chromadb
# 或使用Docker部署Milvus/Weaviate
```

### 六、部署环境（第11周）

```bash
# 容器化
Docker Desktop
├── Windows/Mac：官网下载安装
└── 自动包含Docker Compose

```

### 七、其他必备工具

```bash
# 版本控制
Git 2.x
├── 配置：git config --global user.name/email
└── GUI工具：GitHub Desktop（可选）

# API测试
Postman 或 Insomnia

# 项目管理
Notion/飞书（团队协作）
```

### 八、环境配置顺序建议

1. **第一步**：操作系统准备（WSL/Homebrew）
2. **第二步**：Python + Anaconda
3. **第三步**：VSCode + 插件
4. **第四步**：Git配置
5. **第五步**：PyTorch（根据GPU情况）
6. **第六步**：pip install基础包
7. **第七步**：Node.js（第4周前）
8. **第八步**：Java环境（第5周前）
9. **第九步**：数据库（可用Docker）
10. **第十步**：Docker（第11周前）

### 九、常见问题解决

**Q1：PyTorch GPU版本冲突**
```bash
# 1. 先查看CUDA版本
nvidia-smi

# 2. 选择匹配的PyTorch版本
# 访问 https://pytorch.org/get-started/locally/

# 3. 使用conda安装避免冲突
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```

**Q2：Windows的WSL配置**
```bash
# 1. 开启WSL功能
wsl --install

# 2. 安装Ubuntu
wsl --install -d Ubuntu-22.04

# 3. VSCode连接WSL
# 安装Remote-WSL插件后，命令面板输入：WSL: New Window
```

**Q3：pip安装速度慢**
```bash
# 使用国内镜像
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

### 十、环境验证脚本

创建 `check_env.py`：
```python
import sys
print(f"Python: {sys.version}")

try:
    import torch
    print(f"PyTorch: {torch.__version__}")
    print(f"CUDA available: {torch.cuda.is_available()}")
except:
    print("PyTorch not installed")

try:
    import transformers
    print(f"Transformers: {transformers.__version__}")
except:
    print("Transformers not installed")

```

### 建议

1. **使用虚拟环境**：避免依赖冲突
2. **优先Docker**：数据库等服务优先使用Docker，避免污染本地环境
3. **保存配置**：将所有配置命令保存到个人笔记中
4. **遇到问题**：先Google错误信息，大部分问题都有现成解决方案，遵循[提问的智慧](./提问的智慧.md); 再去群里提问找解决方案。

