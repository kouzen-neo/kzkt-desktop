<div align="center">
  <img src="docs/assets/app_icon.png" width="100" alt="KZKT Desktop Logo" />
  <h1>KZKT Desktop</h1>

  <p>
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-Proprietary-blue.svg?style=for-the-badge" alt="Lisensi: Proprietary"></a>
    <a href="https://github.com/kouzen-neo/kzkt-desktop/releases"><img src="https://img.shields.io/github/v/release/kouzen-neo/kzkt-desktop?style=for-the-badge&color=teal" alt="Rilis Terbaru"></a>
    <a href="https://www.jetbrains.com/lp/compose-multiplatform/"><img src="https://img.shields.io/badge/Compose_Desktop-Material_3-4285F4.svg?style=for-the-badge&logo=jetpackcompose&logoColor=white" alt="Compose Desktop"></a>
    <a href="https://opencv.org/"><img src="https://img.shields.io/badge/OpenCV-v4.9.0-5C3EE8.svg?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV"></a>
    <a href="https://onnxruntime.ai/"><img src="https://img.shields.io/badge/ONNX_Runtime-YOLOv8-00599C.svg?style=for-the-badge&logo=onnx&logoColor=white" alt="ONNX Runtime"></a>
    <a href="https://tesseract-ocr.github.io/"><img src="https://img.shields.io/badge/Tesseract_OCR-v5.16-yellowgreen.svg?style=for-the-badge&logo=tesseract&logoColor=white" alt="Tesseract OCR"></a>
  </p>

  <p>
    <a href="README.md"><img src="https://img.shields.io/badge/EN-6e7681.svg?style=for-the-badge" alt="English"></a>
    <a href="README.id.md"><img src="https://img.shields.io/badge/ID-0078D4.svg?style=for-the-badge" alt="Bahasa Indonesia"></a>
  </p>
</div>

KZKT Desktop adalah aplikasi desktop canggih untuk menerjemahkan manga, manhwa, manhua, dan komik secara otomatis di PC (Windows, Linux, dan macOS), dibangun dengan Kotlin Multiplatform dan JetBrains Compose Desktop. Balon kata dideteksi langsung di perangkat menggunakan model AI YOLOv8, teks diekstrak melalui Tesseract OCR lokal, dialog diterjemahkan via model LLM pilihan (atau model offline lokal), teks asli dihapus rapi menggunakan inpainting OpenCV, dan hasil terjemahan di-typeset langsung ke halaman komik.

---

## Fitur & Keunggulan

- **Format Input Lengkap**: Terjemahkan gambar tunggal (PNG, JPG, BMP), seleksi banyak gambar sekaligus, folder, arsip (ZIP / CBZ), hingga dokumen PDF dengan pemrosesan batch.
- **Deteksi Balon Kata YOLO On-Device**: Model kaskade YOLOv8 ONNX bawaan mendeteksi balon dialog dan teks bebas langsung di perangkat tanpa mengunggah halaman ke server luar.
- **Multi-Script Local OCR**: Mesin Tesseract OCR (Tess4J) akurat dengan teknologi pembersihan border untuk pengenalan teks Bahasa Jepang, Korea, Mandarin, dan Latin.
- **Tipografi Cerdas & Inpainting**: Inpainting OpenCV multi-core (`Photo.INPAINT_TELEA`), pembungkusan teks elips dinamis, perataan vertikal optik, styling outline komik, dan pemenggalan suku kata otomatis.
- **Dukungan Cloud & Local LLM Luas**: Integrasi langsung dengan Google Gemini, Anthropic Claude, OpenAI (GPT), OpenRouter, atau endpoint kustom/lokal (Ollama, LM Studio, LocalAI, vLLM).
- **Studio Workspace**: Layout desktop 3 panel yang dilengkapi file explorer, antrean batch terjemahan, kanvas interaktif dengan zoom/pan bebas, serta panel kontrol inspektor.
- **Visual Touch-up Editor**: Jendela editor interaktif khusus untuk menggeser/mengubah ukuran kotak balon kata, kuas inpainting manual (*Brush*, *Eraser*, *Eyedropper*) dengan penghapusan non-destruktif, dan riwayat Undo/Redo.
- **Reader Manga & Webtoon Terintegrasi**: Jendela pembaca hasil yang mendukung mode per halaman (Manga) maupun gulir vertikal (Webtoon), lengkap dengan komparasi langsung ke halaman asli sebelum diterjemahkan.
- **Glosarium & Memory Terjemahan**: Kamus istilah kustom untuk menjaga konsistensi nama karakter dan istilah berulang.
- **Integrasi Native Desktop**: Mendukung Windows 11 Snap Assist, dekorasi jendela native, ikon aplikasi beresolusi tinggi, serta paket distribusi portabel.

---

## Download & Panduan Instalasi

Unduh installer rilis terbaru langsung dari **[GitHub Releases](https://github.com/kouzen-neo/kzkt-desktop/releases/latest)**.

### Paket installer mana yang harus saya unduh?

| Sistem Operasi | Paket Installer | Keterangan & Perangkat yang Disarankan |
|---|---|---|
| **Windows** | **`kzkt-1.0.0.msi`** / **`kzkt-1.0.0.exe`** | Windows 10 / 11 (64-bit). Dilengkapi shortcut Start Menu & Desktop. |
| **Linux (Debian/Ubuntu)** | **`kzkt_1.0.0-1_amd64.deb`** | Ubuntu, Debian, Linux Mint, Pop!_OS, Zorin OS. |
| **Linux (Fedora/RHEL)** | **`kzkt-1.0.0-1.x86_64.rpm`** | Fedora, Red Hat Enterprise Linux, openSUSE. |
| **Linux (Portabel)** | **`kzkt-1.0.0-linux-x64.tar.gz`** | Seluruh distribusi Linux (Arch Linux, Manjaro, Gentoo, Void, dll.) — arsip portabel tanpa instalasi; ekstrak dan jalankan. |
| **macOS** | **`kzkt-1.0.0.dmg`** | macOS Monterey atau yang lebih baru (Universal: Apple Silicon & Intel). |

---

## Alur Translasi

```text
[ Gambar / Halaman Manga / PDF / ZIP / CBZ ]
                      │
                      ▼
[ 1. Deteksi Balon Kata YOLO (ONNX) ]    ──> Menemukan posisi balon kata & teks di perangkat
                      │
                      ▼
[ 2. OCR Multi-Bahasa (Tesseract) ]     ──> Ekstraksi teks asli (Jepang, Korea, Mandarin, Latin)
                      │
                      ▼
[ 3. Translasi LLM (Multimodal / Teks) ] ──> Gemini / Claude / GPT / OpenRouter / Ollama
                      │
                      ▼
[ 4. OpenCV Inpainting & Masking ]       ──> Menghapus teks asli secara bersih dari panel
                      │
                      ▼
[ 5. Dynamic Diamond Text Render ]       ──> Merender teks terjemahan berbalut rapi ke balon kata
                      │
                      ▼
[ Output di /Downloads/KZKT/ ]           ──> Tersimpan dengan metadata edit untuk touch-up
```

---

## Privasi & Keamanan

- **Privasi Total**: Saat menggunakan deteksi YOLOv8 dan Tesseract OCR lokal, seluruh pemrosesan berlangsung sepenuhnya di komputer Anda tanpa komunikasi jaringan.
- **Kredensial Aman**: API Key dan konfigurasi pengguna tersimpan aman di direktori konfigurasi lokal komputer Anda.

---

## Pengakuan Open Source

KZKT Desktop dibangun berkat teknologi open-source dan komunitas pengembang:

- [JetBrains Compose Multiplatform](https://www.jetbrains.com/lp/compose-multiplatform/) untuk antarmuka grafis desktop native.
- [OpenCV](https://opencv.org/) untuk Computer Vision dan inpainting gambar.
- [Microsoft ONNX Runtime](https://onnxruntime.ai/) untuk inferensi neural network YOLOv8.
- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) & [Tess4J](https://github.com/nguyenq/tess4j) untuk Optical Character Recognition.
- [Apache PDFBox](https://pdfbox.apache.org/) untuk pemrosesan berkas PDF.

---

## Lisensi

Hak Cipta © KZKT. Private and Proprietary.
