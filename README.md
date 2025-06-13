# Whisper Installation Guide

This README provides instructions for installing OpenAI's Whisper speech recognition tool on Windows, both via **manual setup** . Upload this file to your Git repository to guide users
A Python project using OpenAI's Whisper for automatic speech recognition and transcription.

## Prerequisites

- Python 3.10.11 or compatible version
- Windows environment (based on setup paths)

## Installation

### 1. Create Virtual Environment

```bash
# Create virtual environment
python -m venv whisper-env

# Navigate to Scripts directory and activate
C:\Users\Veesh\whisper-env\Scripts> activate
```

### 2. Verify Python Installation

```bash
# Check Python version
python --version
# Should output: Python 3.10.11
```

### 3. Install Dependencies

```bash
# Upgrade pip
python -m pip install --upgrade pip

# Install required packages
python -m pip install openai-whisper torch ffmpeg-python pyaudio pyserial
```

### 4. Verify Installation

```bash
# List installed packages
python -m pip list

# Test Whisper import
python -c "import whisper; print('Whisper is ready!')"
```

## Dependencies

- **openai-whisper**: OpenAI's automatic speech recognition system
- **torch**: PyTorch machine learning framework
- **ffmpeg-python**: Python bindings for FFmpeg audio/video processing
- **pyaudio**: Python audio I/O library
- **pyserial**: Serial communication library

## Quick Start

```python
import whisper

# Load a model
model = whisper.load_model("base")

# Transcribe audio
result = model.transcribe("audio_file.mp3")
print(result["text"])
```

## Project Structure

```
whisper-project/
├── whisper-env/          # Virtual environment
├── scripts/              # Your Python scripts
├── audio/               # Audio files for processing
├── output/              # Transcription outputs
└── README.md           # This file
```

## Usage Examples

### Basic Transcription

```python
import whisper

# Load model (options: tiny, base, small, medium, large)
model = whisper.load_model("base")

# Transcribe audio file
result = model.transcribe("path/to/audio.mp3")
print("Transcription:", result["text"])
```

### Real-time Audio Processing

```python
import pyaudio
import whisper

# Configure audio recording
model = whisper.load_model("base")

# Your real-time processing code here
```

## Troubleshooting

### Common Issues

1. **FFmpeg not found**: Ensure FFmpeg is installed and in your system PATH
2. **PyAudio installation issues**: May require Microsoft C++ Build Tools on Windows
3. **CUDA/GPU issues**: Install appropriate PyTorch version for your GPU

### Environment Activation

Always activate your virtual environment before running scripts:

```bash
C:\Users\Veesh\whisper-env\Scripts\activate
```

## Model Options

Whisper offers several model sizes with different trade-offs:

- `tiny`: Fastest, least accurate
- `base`: Good balance of speed and accuracy
- `small`: Better accuracy, slower
- `medium`: Higher accuracy, more resources
- `large`: Best accuracy, most resources

## License

This project uses OpenAI Whisper, which is released under the MIT License.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Support

For issues related to:
- **Whisper**: Check the [OpenAI Whisper GitHub repository](https://github.com/openai/whisper)
- **PyTorch**: Visit [PyTorch documentation](https://pytorch.org/docs/)
- **Audio processing**: Refer to FFmpeg and PyAudio documentation

---

**Note**: Remember to activate your virtual environment (`whisper-env`) before running any scripts in this project.
