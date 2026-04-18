# AI-Dialogue-System 
# AI语音伴侣

> 一个基于本地大模型和Coqui TTS的AI语音伴侣，支持文字对话、语音合成、聊天记录导出。

## 功能

- 🎭 **角色扮演**：内置【角色名】人设，强制（动作）台词格式输出
- 🔊 **语音合成**：集成Coqui TTS，让AI“开口说话”，支持系统语音降级
- 💾 **本地存储**：聊天记录自动保存，刷新页面不丢失
- 📤 **导出训练数据**：一键导出JSON格式聊天记录，可用于模型微调
- 🎵 **背景音乐**：沉浸式聊天体验
- 🖼️ **欢迎页面**：完整的用户引导

## 如何运行

### 1. 启动本地大模型服务

```bash
# 使用llama.cpp的server模式
./llama-server -m your-model.gguf --host 127.0.0.1 --port 8080
```

### 2. 启动Coqui TTS服务（可选，用于语音合成）

```bash
# 在Anaconda环境中启动TTS服务
python TTS/server/server.py --model_name tts_models/zh-CN/... --port 5002
```

如果不启动TTS服务，系统会自动降级到浏览器语音合成。

### 3. 准备资源文件

- **背景图片**：修改CSS中的`background-image`路径
- **背景音乐**：替换`6aa6aa97c3be134ce7f8e89d86dfe14c.mp3`为你的音乐文件

### 4. 打开应用

双击`index.html`，点击“进入聊天”即可开始。

## 项目结构

```
index.html          # 主程序（单文件）
background.jpg      # 背景图片（需自行准备）
bg-music.mp3        # 背景音乐（需自行准备）
```

## 技术栈

- HTML/CSS/JavaScript（原生）
- llama.cpp server（本地大模型）
- Coqui TTS（语音合成）
- Web Speech API（降级语音）

## 亮点说明

- **语音降级**：Coqui TTS未启动时，自动切换到浏览器语音合成
- **格式强制**：通过提示词工程，强制模型输出（动作）台词格式
- **训练数据导出**：聊天记录可导出为JSON，用于LoRA微调
- **本地存储**：使用localStorage持久化聊天记录

## 注意事项

- 需要先启动llama.cpp的server模式
- 语音功能需要Coqui TTS服务（可选，不启动也能用）
- 背景音乐需要用户手动点击播放（浏览器策略）
