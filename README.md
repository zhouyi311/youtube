# youtube
YouTube video processing scripts

脚本 1: CN_mp3_audio2text.py
这段代码的功能和安装步骤。

**代码功能概述：**
这是一个音频转文字的程序，主要功能是将 MP3 音频文件转换为文本。具体来说：
1. 加载 Whisper 大型语音识别模型
2. 读取并预处理 MP3 音频文件（转换为单声道、16kHz采样率）
3. 将音频数据转换为模型可处理的格式
4. 执行语音识别，生成文本
5. 将转录结果保存到文件
6. 提供详细的处理进度和时间统计

**安装步骤：**
1. 首先确保安装了 Python（推荐 3.8 或更高版本）

2. 创建并激活虚拟环境（推荐）：
```bash
# 创建虚拟环境
python -m venv venv

# 激活虚拟环境
# Windows:
venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate
```
3. 安装所需依赖：
```bash
# 安装基础依赖
pip install faster-whisper
pip install pydub
pip install numpy

# 如果处理 MP3 文件，还需要安装 ffmpeg
# Windows: 
# 下载 ffmpeg: https://www.gyan.dev/ffmpeg/builds/
# 添加到系统环境变量

# Linux:
sudo apt-get install ffmpeg

# Mac:
brew install ffmpeg
```
**使用示例：**
```python
# 导入函数
from your_script import transcribe_audio

# 调用函数进行转录
result = transcribe_audio(
    audio_file_path="你的音频文件.mp3",
    output_file_path="输出文本.txt",
    language="zh"  # 支持的语言代码，如 zh=中文, en=英文
)
```
**注意事项：**
1. 代码使用 CPU 进行计算（`device="cpu"`），如果有 GPU 可以修改为 `device="cuda"`
2. 使用了 `large-v2` 模型，需要较大内存，如果内存不足可以换用较小的模型
3. 使用了 `int8` 量化（`compute_type="int8"`）来减少内存占用
4. 程序会显示详细的处理进度，方便监控长音频的转录进度
