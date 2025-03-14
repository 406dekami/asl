# ✋ ASL手势识别系统

基于MediaPipe和机器学习技术的手语识别解决方案，支持静态手势识别和动态手势轨迹分析

![系统界面截图](https://github.com/nujrarian/asl-detector-mediapipe/assets/55311409/eb0269de-b4bb-49c7-86c9-a5de0eea7dbd)

## 🌟 核心功能

| 功能类别        | 特性描述                                                                |
|----------------|-------------------------------------------------------------------------|
| **识别模式**    | 支持静态/动态双模式识别 |
| **实时处理**    | 60FPS实时视频流处理，延迟<100ms                                          |
| **可视化**      | 手部21关键点渲染 + 智能边界框显示                                        |
| **智能交互**    | 5秒无手势自动重置 + 运动轨迹稳定性分析                                   |
| **扩展能力**    | 手势数据收集系统 + 模型再训练接口                                        |

## 🛠️ 环境配置

### 硬件要求
- USB摄像头（推荐Logitech C920以上）
- CPU：Intel i5 8代+/AMD Ryzen 5 3500U+
- RAM：8GB+

### 软件依赖
```bash
# 基础环境
Python 3.8+ | CUDA 11.2 (可选)

# 核心依赖
mediapipe==0.9.0        # 手部关键点检测
opencv-python==4.5.5.64 # 视频处理
numpy==1.21.5           # 数值计算
Pillow==9.0.1           # 图像处理
scikit-learn==1.0.2     # 机器学习模型
```
## 🚀 快速入门
### 安装步骤
```bash
git clone https://github.com/406dekami/asl-detector-mediapipe.git
cd asl-detector-mediapipe
pip install -r requirements.txt
```
### 项目结构
```tree
asl-detector-mediapipe-main/
│
├── model/
│   ├── keypoint_classifier/
│   │   ├── keypoint_classifier.hdf5
│   │   ├── keypoint_classifier.tflite
│   │   ├── keypoint.csv
│   │   ├── keypoint_classifier_label.csv
│   │   ├── keypoint_classification.py
│   │   └── keypoint_classifier.py
│   │
│   └── keypoint_history_classifier/
│       ├── keypoint_history_classifier.hdf5
│       ├── keypoint_history_classifier.tflite
│       ├── keypoint_history.csv
│       ├── keypoint_history_classification.py
│       ├── keypoint_history_classifier.py
│       └── keypoint_classifier_label.csv
│
├── README.md
├── main.py
└── requirements.txt
```
# 📖 使用指南
## 操作流程
### 硬件连接
1. 确保摄像头驱动正常。
2. 调整摄像头角度，建议俯角30°。

### 模式选择
|模式|功能说明|适用场景|
|--|--|--|
|演示模式|实时识别显示|快速演示|
|静态手势|单手势录入/识别|字母手势识别|
|动态手势|连续动作轨迹记录|手语短语识别|

### 手势训练
示例：训练静态新手势"Hello"
1. 在输入框输入"Hello"。
2. 保持手势稳定2秒（需完成20次采样）。
3. 点击<确认>按钮。

# ❓ 常见问题
## Q1: 识别延迟较高
### 解决方案：
关闭其他占用摄像头的程序。

## Q2: 如何扩展新手势
### 操作步骤：
1. 在"静态/动态手势"模式下输入新手势名称。
2. 保持不同角度/位置的姿势完成采样。
3. 运行`python kepoint_classification.py/kepoint_history_classification.py`重新训练。 