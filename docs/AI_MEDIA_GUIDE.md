# AI photo and video cleanup on Windows

This folder is the local checkout of `watermarks-remover`. It supports two different tasks:

- **Photos:** inspect and remove supported file metadata (including C2PA, EXIF, and XMP). Optional CtrlRegen and MarkDiffusion backends can regenerate image pixels. These are best-effort image transformations: they may change visible details and cannot guarantee removal of every vendor watermark.
- **Videos:** inspect and remove supported container metadata from MP4/MOV/M4V files. The optional CtrlRegen and MarkDiffusion pixel-removal backends operate on still images, not video frames. Video pixel watermark removal is not implemented here.

## Install the optional CtrlRegen photo backend

CtrlRegen is the recommended first image backend because it conditions regeneration on the input image. It downloads several gigabytes of models and uses a separate Python environment. The backend project has no published license; review its terms before use.

From PowerShell in this folder:

```powershell
$python312 = py -3.12 -c "import sys; print(sys.executable)"
& .\service\scripts\setup_ctrlregen.ps1 -Dir "$PWD\noai-watermark-py312" -Python $python312
```

The setup script detects NVIDIA CUDA support and verifies PyTorch can see the GPU. Python 3.12 is used here because the pinned tokenizer dependency does not build cleanly with Python 3.14 on Windows.

## Clean an image

Keep the original and write a separate output file:

```powershell
$env:NOAI_WATERMARK_DIR = "$PWD\noai-watermark-py312"
py .\service\scripts\clean_image.py .\photo.png -o .\photo.cleaned.png --remove-pixel ctrlregen
```

Use only on images you own or are authorized to modify. Compare the output visually with the original; regeneration can alter fine details, text, faces, or texture. Start with the conservative default intensity. A clean metadata report does not prove a pixel watermark is gone.

## Clean video metadata

For supported MP4/MOV/M4V files, strip container metadata with the normal file cleaner:

```powershell
py .\service\scripts\clean_file.py .\clip.mp4 -o .\clip.cleaned.mp4
```

This operation does not remove a watermark embedded in video pixels or across frames. Applying the still-image backend frame by frame is not provided because it can cause flicker and temporal inconsistency.

## Scope

There is no “perfect” or universal remover. Detection may be unavailable or only a proxy score, regenerated content may change, and vendor verification may disagree with local tools. Keep originals and verify results with the relevant provider when that matters.
