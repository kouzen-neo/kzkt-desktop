# Changelog

All notable changes to KZKT Desktop are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-09-20

### Added

- **KZKT Desktop Initial Release**:
  - Full-featured, native desktop application built with Kotlin Multiplatform and JetBrains Compose Desktop for Windows, Linux, and macOS.
  - Studio workspace layout with three-pane architecture: left explorer/history panel, center canvas, and right inspector panel.
- **AI & Computer Vision Pipeline**:
  - Offline bubble detection using bundled YOLOv8 model (`kzkt.dat`).
  - Offline text recognition via Tesseract OCR engine (`tess4j`).
  - Smart OpenCV text inpainting (`Photo.INPAINT_TELEA`) with transparent ARGB canvas overlay.
  - Interactive touch-up brush tool (`Brush`, `Eraser`, `Eyedropper`) with non-destructive `AlphaComposite.Clear` erasing.
  - Click-and-drag custom bounding box creation with real-time preview.
  - Multi-LLM provider integration supporting Google Gemini, OpenAI, Anthropic Claude, OpenRouter, and Custom HTTP endpoints (Ollama/LocalAI).
- **Pro Licensing & Feature Gating**:
  - Offline RSA cryptographic digital license verification.
  - Free Tier limits: 8 pages per batch with Pro-gating on On-Device Local OCR, Free-text translation, SFX translation, and unlimited glossary.
- **Workflow & Productivity**:
  - Real-time 60 FPS live drag re-rendering for smooth bounding box movement and resizing.
  - Full desktop keyboard shortcuts: `Ctrl+Z` (Undo), `Ctrl+Y` / `Ctrl+Shift+Z` (Redo), `Ctrl+S` (Save), `Delete`/`Backspace` (Delete selected bubble), `Escape` (Deselect / Exit tool).
  - Universal mouse navigation: Right-click drag and middle-click drag for instant free canvas panning anywhere.
  - Collapsible terminal-style Translation Logs drawer with high-contrast syntax highlighting.
  - System Logs viewer in Advanced Settings with font resizing (`A-`/`A+`) and error filtering.
  - Direct output file export to `~/Downloads/KZKT/` with clean image files only (no `.kzkt.json` clutter).
- **Native Window Management & Snapping (Windows, macOS, Linux)**:
  - Enabled native Win32/macOS window decorations by default on floating desktop environments.
  - Fixed maximize button covering taskbar on Windows by respecting OS work areas.
  - Enabled native Windows Snap Assist (Aero Snap / Dragging window to edges/corners to split screen / `Win + Arrows`) and Windows 11 Snap Layouts.
  - Enabled native window resize borders and resize cursors.
  - Added automatic desktop environment detection: keeps borderless undecorated window mode for Linux tiling window managers (Niri, Hyprland, Sway, i3, etc.).
  - Added `--decorated` and `--undecorated` CLI flags for user override.
  - Set default floating centered window size (`1280x820`) for floating desktop environments while preserving maximized start for tiling window managers.
- **Application Icon & Desktop Integration**:
  - Synchronized application icons directly with KZKT Mobile (`#17171F` container with white `Kzt` monogram).
  - Generated multi-resolution Windows `.ico`, macOS `.icns`, and full-size Linux icon themes (`16x16` to `512x512` + SVG).
  - Configured Windows installers (`.msi`, `.exe`) to automatically create Start Menu and Desktop shortcuts.
- **Cross-Platform Installers**:
  - Portable Linux Distribution (`kzkt-1.0.0-linux-x64.tar.gz`) for Arch Linux, openSUSE, and any Linux distribution without package manager dependencies.
  - Debian/Ubuntu `.deb` package (`kzkt_1.0.0-1_amd64.deb`).
  - Fedora/RHEL `.rpm` package (`kzkt-1.0.0-1.x86_64.rpm`).
  - Windows `.msi` and `.exe` installers.
  - macOS `.dmg` disk image.
