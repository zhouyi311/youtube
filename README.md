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

脚本 2： zimu.py
我来帮你总结这段代码的功能和安装步骤。

**代码功能概述：**
这是一个音频转字幕的程序，它可以将音频文件转换为标准的 SRT 格式字幕文件。主要功能包括：
1. 将音频时间点转换为 SRT 时间戳格式（如：00:00:03,456）
2. 加载 Whisper 语音识别模型
3. 处理和转换音频文件（转单声道、16kHz采样率）
4. 执行语音识别，获取带时间戳的文本片段
5. 生成标准 SRT 格式字幕文件（包含序号、时间轴、文本内容）
6. 提供详细的处理进度和时间统计

**安装步骤：**

1. 确保安装了 Python（推荐 3.8 或更高版本）

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

# 安装 ffmpeg（处理音频文件必需）
# Windows: 
# 1. 下载 ffmpeg: https://www.gyan.dev/ffmpeg/builds/
# 2. 解压并添加到系统环境变量

# Linux:
sudo apt-get install ffmpeg

# Mac:
brew install ffmpeg
```

**使用示例：**
```python
# 导入函数
from your_script import transcribe_audio_to_srt

# 调用函数生成字幕
result = transcribe_audio_to_srt(
    audio_file_path="你的音频.mp3",
    output_srt_path="输出字幕.srt",
    language="zh"  # 支持的语言代码，如 zh=中文, en=英文
)
```

**生成的 SRT 格式示例：**
```
1
00:00:00,000 --> 00:00:02,500
第一段文字

2
00:00:02,500 --> 00:00:05,000
第二段文字
```

**注意事项：**
1. 代码使用 CPU 进行计算，可通过修改 `device="cuda"` 启用 GPU 加速
2. 使用了 `large-v2` 模型，需要较大内存，可以根据需要选择较小的模型
3. 使用了 `int8` 量化以减少内存占用
4. 输出的 SRT 文件采用 UTF-8 编码，兼容大多数播放器
5. 程序会显示详细的处理进度，方便监控长音频的转录进度

