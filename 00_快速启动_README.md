## 00_快速启动（Windows / PowerShell）

> 目标：在 **fitness-trainer-pose-estimation** 目录里，用独立虚拟环境正确安装 `mediapipe`，并启动应用。

### 1. 进入项目目录

```powershell
cd d:\code4\51_computer\maven\ai_fitness\fitness-trainer-pose-estimation
```

### 2. 创建并激活虚拟环境

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

如果激活时报执行策略错误，可先执行（只需一次）：

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

然后再执行一次激活命令：

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. 安装依赖（特别是正确的 mediapipe）

```powershell
python -m pip install -U pip
python -m pip uninstall -y mediapipe
python -m pip install "mediapipe==0.10.9"
python -m pip install -r requirements.txt
```

### 4. 验证 mediapipe 是否正常（必须看到 has_solutions True）

```powershell
python -c "import mediapipe as mp; print('version', getattr(mp,'__version__',None)); print('has_solutions', hasattr(mp,'solutions'))"
```

输出示例（类似下面即可）：

```text
version 0.10.9
has_solutions True
```

### 5. 启动应用

```powershell
python app.py
```

浏览器打开：

- `http://127.0.0.1:5000/video_analysis` 进行视频上传分析
- 或首页 `http://127.0.0.1:5000` 做实时相机检测

