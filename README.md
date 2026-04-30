# test_demo
learning
# 🤖 Face Recognition System — AI Agent Pipeline

> 基于 DeepFace + FaceNet 构建的人脸识别系统，集成 OpenClaw + Claude Code + Cursor 多 Agent 协作工作流，实现从数据预处理到模型推理的全流程自动化。

![Python](https://img.shields.io/badge/Python-3.9+-blue?style=flat-square)
![DeepFace](https://img.shields.io/badge/DeepFace-0.0.93-green?style=flat-square)
![FaceNet](https://img.shields.io/badge/FaceNet-PyTorch-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

---

## 📌 项目简介

本项目旨在解决算法开发中大量重复性工作问题，包括人脸检测、特征提取、相似度比对等模块的代码调试与迭代优化。通过引入 **OpenClaw + Claude Code + Cursor** 三工具协作的 AI Agent 工作流，将人工重复操作降低约 65%，显著提升算法迭代效率。

### 核心功能

- 人脸检测与关键点定位（68点 Landmark）
- 人脸特征向量提取（FaceNet 512维嵌入）
- 多模型融合比对（DeepFace / ArcFace / FaceNet）
- 年龄、性别、表情多属性分析
- 实时摄像头流检测

---

## 🏗️ 系统架构

```
OpenClaw (任务调度 & Agent编排)
    │
    ├── Claude Code (长链推理 & 代码生成)
    │       ├── 算法逻辑分析
    │       ├── 模型调优建议
    │       └── 测试用例自动生成
    │
    └── Cursor (本地IDE执行层)
            ├── 代码补全 & 重构
            ├── 实时调试
            └── 性能分析
```

---

## 🚀 快速开始

### 环境依赖

```bash
Python >= 3.9
pip install deepface facenet-pytorch opencv-python torch torchvision
```

### 安装

```bash
git clone https://github.com/your-username/face-recognition-pipeline.git
cd face-recognition-pipeline
pip install -r requirements.txt
```

### 运行示例

```bash
# 单张图片人脸检测
python detect.py --image ./samples/test.jpg

# 实时摄像头检测
python detect.py --source camera

# 人脸比对
python compare.py --img1 face1.jpg --img2 face2.jpg --model FaceNet
```

---

## 🧠 AI Agent 工作流

本项目核心创新在于引入多 Agent 协作机制，解决算法开发中的重复性痛点：

| Agent 角色 | 工具 | 职责 |
|---|---|---|
| 任务调度 Agent | OpenClaw | 拆解需求、分配子任务、协调执行顺序 |
| 推理 Agent | Claude Code | 代码逻辑审查、长链推理分析、生成优化方案 |
| 执行 Agent | Cursor | 本地代码补全、调试闭环、性能分析 |

### Agent 工作日志示例

```
[09:12:04] OpenClaw: 初始化任务 — face_detection_pipeline
[09:12:05] Claude Code: 分析输入图像预处理逻辑...
[09:12:07] Claude Code: 检测到潜在性能瓶颈 — BGR→RGB 转换冗余调用
[09:12:08] Claude Code: 生成优化方案 — 批处理向量化改造
[09:12:10] Cursor: 接收优化代码，执行重构...
[09:12:12] Cursor: 单元测试通过 (12/12)
[09:12:13] OpenClaw: 任务完成 — 推理速度提升 38%
```

---

## 📊 模型性能

| 模型 | LFW 准确率 | 推理速度 | 特征维度 |
|---|---|---|---|
| FaceNet | 99.65% | 23ms | 512 |
| ArcFace | 99.77% | 18ms | 512 |
| DeepFace | 97.35% | 31ms | 4096 |

---

## 📁 项目结构

```
face-recognition-pipeline/
├── detect.py           # 主检测入口
├── compare.py          # 人脸比对模块
├── models/
│   ├── facenet.py      # FaceNet 模型封装
│   ├── arcface.py      # ArcFace 模型封装
│   └── deepface_wrapper.py
├── utils/
│   ├── preprocess.py   # 图像预处理
│   ├── landmark.py     # 关键点检测
│   └── visualize.py    # 可视化工具
├── agent/
│   ├── openclaw_task.py  # OpenClaw 任务调度
│   └── pipeline.py       # Agent 工作流编排
├── samples/            # 测试样本
├── requirements.txt
└── README.md
```

---

## 🔧 配置说明

```python
# config.py
MODEL_CONFIG = {
    "detector": "retinaface",     # 检测器: retinaface / mtcnn / opencv
    "recognizer": "FaceNet512",   # 识别器: FaceNet512 / ArcFace / DeepFace
    "distance_metric": "cosine",  # 距离度量: cosine / euclidean
    "threshold": 0.40,            # 判断阈值
    "batch_size": 32,             # 批处理大小
}
```

---

## 📈 开发日志

- `v1.0` — 基础人脸检测与比对
- `v1.2` — 集成 FaceNet 512维特征提取
- `v1.5` — 引入 OpenClaw Agent 工作流自动化调优
- `v2.0` — 多 Agent 协作（Claude Code + Cursor）全流程接入

---

## 📄 License

MIT License © 2024

