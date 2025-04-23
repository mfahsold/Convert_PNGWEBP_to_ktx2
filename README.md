# PNG / WEBP → KTX2 Encoder (PowerShell)

> Tiny, dependency-light helper that batch-converts **PNG** or **WEBP** textures  
> into Khronos **KTX2** containers (UASTC 4, Zstd 18, 4 mip-levels, sRGB).

---

## ✨ Why?

* **KTX2 + UASTC** offers near-lossless GPU-friendly compression with proper mip-chains.
* Works on **Windows, macOS, Linux** – anywhere PowerShell 7 or newer runs.
* Path-agnostic. Point it at any folder; it writes compressed copies to an output dir.
* **Optional auto-padding** (4 × 4 multiples) so every texture is GPU-safe.
* Reads **WEBP** and handles padding via ImageMagick *if* you happen to have it.
* Pure script – no NuGet/NPM/python/rust cargo chain to install.

---

## 📦 Requirements

| Component | Tested with | Purpose |
|-----------|------------|---------|
| **PowerShell** | ≥ 7.0 (Core) &nbsp;| cross-platform scripting host |
| **TokTX** (Khronos *KTX-Software*) | ≥ v4.0 | encodes raw images into KTX2 (must be in `PATH`) |
| **ImageMagick** *(optional)* | ≥ 7.0 | auto-pad to 4×4 **and** decode WEBP → PNG for TokTX |

> **Tip**  
> `winget install KhronosGroup.KTX-Software` (Windows) or  
> `brew install ktx-tools imagemagick` (macOS) gets you there fast.

---

## 🚀 Usage

```powershell
# 1. encode every PNG / WEBP in the current directory → .\ktx2\
.\convert_to_ktx2_generic.ps1

# 2. encode a custom folder → another folder
.\convert_to_ktx2_generic.ps1 -SourceDir .\textures -OutputDir .\build\ktx-out

# 3. same as (2) but **disable** GPU-safe 4×4 padding
.\convert_to_ktx2_generic.ps1 -SourceDir .\textures -OutputDir .\build\ktx-out -NoPad
