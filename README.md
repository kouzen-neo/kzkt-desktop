<div align="center">
  <img src="docs/assets/app_icon.png" width="100" alt="KZKT Desktop Logo" />
  <h1>KZKT Desktop</h1>

  <p>
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-Proprietary-blue.svg?style=for-the-badge" alt="License: Proprietary"></a>
    <a href="https://github.com/kouzen-neo/kzkt-desktop/releases"><img src="https://img.shields.io/github/v/release/kouzen-neo/kzkt-desktop?style=for-the-badge&color=teal" alt="Latest Release"></a>
    <a href="https://www.jetbrains.com/lp/compose-multiplatform/"><img src="https://img.shields.io/badge/Compose_Desktop-Material_3-4285F4.svg?style=for-the-badge&logo=jetpackcompose&logoColor=white" alt="Compose Desktop"></a>
    <a href="https://opencv.org/"><img src="https://img.shields.io/badge/OpenCV-v4.9.0-5C3EE8.svg?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV"></a>
    <a href="https://onnxruntime.ai/"><img src="https://img.shields.io/badge/ONNX_Runtime-YOLOv8-00599C.svg?style=for-the-badge&logo=onnx&logoColor=white" alt="ONNX Runtime"></a>
    <a href="https://tesseract-ocr.github.io/"><img src="https://img.shields.io/badge/Tesseract_OCR-v5.16-yellowgreen.svg?style=for-the-badge&logo=tesseract&logoColor=white" alt="Tesseract OCR"></a>
  </p>

  <p>
    <a href="README.md"><img src="https://img.shields.io/badge/EN-0078D4.svg?style=for-the-badge" alt="English"></a>
    <a href="README.id.md"><img src="https://img.shields.io/badge/ID-6e7681.svg?style=for-the-badge" alt="Bahasa Indonesia"></a>
  </p>
</div>

KZKT Desktop is an advanced, automated Manga and Webtoon Translator for PC (Windows, Linux, and macOS), built with Kotlin Multiplatform and JetBrains Compose Desktop. It detects speech bubbles on-page using an on-device YOLOv8 AI model, extracts text with local Tesseract OCR, translates dialogue using multi-provider LLMs (or local offline models), seamlessly erases original text using OpenCV inpainting, and typesets styled translations directly onto comic pages.

---

## Highlights & Features

- **Wide Input Formats**: Translate single images (PNG, JPG, BMP), multi-image selections, folders, archives (ZIP / CBZ), and PDF documents with batch page processing.
- **On-Device YOLO Speech Bubble Detection**: Bundled 3-stage YOLOv8 ONNX cascade identifies speech bubbles and text regions locally without sending entire pages to external servers.
- **Multi-Script Local OCR**: High-accuracy Tesseract OCR engine (Tess4J) with border-component stripping for Japanese, Korean, Chinese, and Latin text, plus free-text region detection.
- **Intelligent Typography & Inpainting**: Multi-core OpenCV inpainting (`Photo.INPAINT_TELEA`) with elliptical text wrapping, optical vertical centering, outline comic styling, and hyphenation.
- **Multi-Cloud & Local LLM Support**: Translate via Google Gemini, Anthropic Claude, OpenAI (GPT), OpenRouter, or local/custom HTTP endpoints (Ollama, LM Studio, LocalAI, vLLM).
- **Studio Workspace**: 3-pane desktop layout featuring a file explorer, batch translation queue, interactive zoom/pan canvas, and inspector controls.
- **Visual Touch-up Editor**: Dedicated interactive editor with draggable bounding-box controls, manual inpainting brushes (Brush, Eraser, Eyedropper) with non-destructive erasing, and snapshot undo/redo.
- **Built-in Manga & Webtoon Reader**: Dedicated reader window supporting horizontal manga pager or continuous vertical webtoon scrolling, with instant side-by-side comparison to original pages.
- **Glossary & Translation Memory**: Custom terminology dictionary to enforce consistent character names and recurring terms.
- **Native Desktop Integration**: Windows 11 Snap Assist and Aero Snap, native decorations, multi-resolution application icons, and portable distributions.

---

## Download & Installation

Grab the latest installer directly from **[GitHub Releases](https://github.com/kouzen-neo/kzkt-desktop/releases/latest)**.

### Which installer should I download?

| Operating System | Installer Package | Recommended For |
|---|---|---|
| **Windows** | **`kzkt-1.0.0.msi`** / **`kzkt-1.0.0.exe`** | Windows 10 / 11 (64-bit). Includes Start Menu and Desktop shortcuts. |
| **Linux (Debian/Ubuntu)** | **`kzkt_1.0.0-1_amd64.deb`** | Ubuntu, Debian, Linux Mint, Pop!_OS, Zorin OS. |
| **Linux (Fedora/RHEL)** | **`kzkt-1.0.0-1.x86_64.rpm`** | Fedora, Red Hat Enterprise Linux, openSUSE. |
| **Linux (Portable)** | **`kzkt-1.0.0-linux-x64.tar.gz`** | Any Linux distribution (Arch Linux, Manjaro, Gentoo, Void, etc.) — standalone portable archive; extract and run. |
| **macOS** | **`kzkt-1.0.0.dmg`** | macOS Monterey or newer (Universal: Apple Silicon & Intel). |

---

## Translation Pipeline

```text
[ Input image / manga page / PDF / ZIP / CBZ ]
                      │
                      ▼
[ 1. YOLOv8 Bubble Detection (ONNX) ]    ──> Locates dialogue bubbles & text regions on-device
                      │
                      ▼
[ 2. Multi-Script OCR (Tesseract) ]     ──> Extracts original text (Japanese, Korean, Chinese, Latin)
                      │
                      ▼
[ 3. Multimodal / Text LLM Translation ] ──> Gemini / Claude / GPT / OpenRouter / Ollama
                      │
                      ▼
[ 4. OpenCV Inpainting & Masking ]       ──> Erases original text strokes cleanly from background art
                      │
                      ▼
[ 5. Dynamic Diamond Text Render ]       ──> Renders styled, wrapped translation into speech bubbles
                      │
                      ▼
[ Output in /Downloads/KZKT/ ]           ──> Saved with edit metadata for interactive touch-up
```

---

## Privacy & Security

- **Local AI Privacy**: When using offline YOLOv8 detection and Tesseract OCR, processing occurs entirely on your device with zero network traffic.
- **Secure Credentials**: API keys and personal configuration are stored locally in user configuration directories.

---

## Open-Source Acknowledgments

KZKT Desktop is made possible by open-source technologies and community projects:

- [JetBrains Compose Multiplatform](https://www.jetbrains.com/lp/compose-multiplatform/) for native desktop GUI.
- [OpenCV](https://opencv.org/) for computer vision and inpainting.
- [Microsoft ONNX Runtime](https://onnxruntime.ai/) for YOLOv8 neural network inference.
- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) & [Tess4J](https://github.com/nguyenq/tess4j) for optical character recognition.
- [Apache PDFBox](https://pdfbox.apache.org/) for PDF processing.

---

## License

Copyright © KZKT. Private and Proprietary.
