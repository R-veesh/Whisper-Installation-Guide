# Whisper Installation Guide

This README provides instructions for installing OpenAI's Whisper speech recognition tool on Windows, both via **manual setup** and using the **automated script**. Upload this file to your Git repository to guide users.

---

## 📋 Prerequisites

* **Windows 10/11** (64-bit)
* **Administrator** privileges for installing system packages (Chocolatey, FFmpeg)
* A **compatible NVIDIA GPU** (optional, for GPU acceleration via CUDA)
* **PowerShell** (with execution policy allowing scripts)

---

## 🔧 Manual Installation

Follow these steps if you prefer to control each component manually:

1. **Install Python 3.11**

   * Download the installer from the [official Python website](https://www.python.org/downloads/release/python-3119/).
   * Run the installer, check **"Add Python to PATH"**, and complete installation.

2. **Create a Virtual Environment**

   ```powershell
   # Use Python 3.11
   py -3.11 -m venv whisper-env
   # Activate the environment
   .\whisper-env\Scripts\activate
   ```

3. **Bootstrap Packaging Tools**

   ```powershell
   python -m ensurepip --upgrade
   python -m pip install --upgrade pip setuptools wheel
   ```

4. **Install FFmpeg**

   * Using Chocolatey (recommended):

     ```powershell
     choco install ffmpeg -y
     ```
   * Or download from the [FFmpeg website](https://ffmpeg.org/) and add to your PATH.

5. **Install PyTorch**

   * **CPU-only**:

     ```powershell
     python -m pip install torch torchvision torchaudio
     ```
   * **CUDA GPU** (e.g., CUDA 12.1):

     ```powershell
     python -m pip install --index-url https://download.pytorch.org/whl/cu121 \
         torch torchvision torchaudio
     ```

6. **Install Whisper**

   ```powershell
   python -m pip install openai-whisper ffmpeg-python
   ```

7. **Verify Installation**

   ```powershell
   python -c "import whisper; print('✅ Whisper is ready!')"
   ```

8. **Run Your Script**

   ```powershell
   python path\to\your\voice.py
   ```

---

## 🤖 Automated Script Installation

Use the TroubleChute installer script to automatically set up all dependencies:

1. Open an elevated PowerShell window (Run as Administrator).
2. Execute the one-liner:

   ```powershell
   iex (irm https://whisper.tc.ht)
   ```
3. Follow on-screen prompts; the script will:

   * Install Chocolatey
   * Install Python 3.10.11 (or use Conda)
   * Install FFmpeg
   * Install CUDA & cuDNN (if NVIDIA GPU detected)
   * Install PyTorch (GPU or CPU build)
   * Install OpenAI Whisper
4. Verify by running:

   ```powershell
   whisper --help
   ```

---

## 🛠️ Troubleshooting

* **`ModuleNotFoundError: No module named 'whisper'`**:

  * Ensure you’ve activated the virtual environment where `openai-whisper` is installed.
  * Run `python -m pip list` to confirm installation.

* **`ImportError` or build errors**:

  * Recreate the virtual environment using Python 3.11:

    ```powershell
    py -3.11 -m venv whisper-env
    ```
  * Upgrade `pip`, `setuptools`, and `wheel` before installing.

* **CUDA/PyTorch mismatches**:

  * Verify your NVIDIA driver and CUDA Toolkit versions.
  * Use the matching PyTorch wheel from the official [PyTorch site](https://pytorch.org/get-started/locally/).

---

## 📄 License

This guide is provided under the **MIT License**. See `LICENSE` for details.
