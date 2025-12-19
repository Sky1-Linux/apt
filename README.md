# Sky1 Linux APT Repository

Debian packages for CIX Sky1 SoC (Radxa Orion O6).

## Usage

```bash
# Add repository key
wget -qO- https://sky1-linux.github.io/apt/key.gpg | sudo tee /usr/share/keyrings/sky1-linux.asc > /dev/null

# Add repository
echo "deb [signed-by=/usr/share/keyrings/sky1-linux.asc] https://sky1-linux.github.io/apt sid main non-free-firmware" | sudo tee /etc/apt/sources.list.d/sky1-linux.list

# Install packages
sudo apt update
sudo apt install linux-image-6.18-sky1 sky1-firmware
```

## GPG Key

- **Key ID**: `48A0ABF100336ADB`
- **Fingerprint**: `7D7E E7FC 3675 9E50 D5C2 3CB3 48A0 ABF1 0033 6ADB`
- **Download**: [key.gpg](https://sky1-linux.github.io/apt/key.gpg)

## Available Packages

### Metapackages

| Package | Description |
|---------|-------------|
| sky1-desktop | Full desktop: kernel, firmware, drivers, hardware video |
| sky1-minimal | Essential: kernel, firmware, 5GbE driver |
| sky1-ai | Adds NPU driver to sky1-minimal |

### Kernel

| Package | Version | Description |
|---------|---------|-------------|
| linux-image-6.18-sky1 | 6.18.1-sky1.5 | Linux 6.18.1 LTS for Sky1 |
| linux-headers-6.18-sky1 | 6.18.1-sky1.5 | Kernel headers for DKMS |
| linux-dtbs-6.18-sky1 | 6.18.1-sky1.5 | Device tree blobs |

### Firmware (non-free-firmware)

| Package | Version | Description |
|---------|---------|-------------|
| sky1-firmware | 1.1.0 | GPU, DSP, VPU, WiFi firmware |

### Multimedia

| Package | Version | Description |
|---------|---------|-------------|
| chromium-sky1-config | 1.0.0-1 | Chromium V4L2-M2M hardware video decode config |
| firefox | 146.0-1+v4l2m2m.2 | Firefox with V4L2-M2M hardware video decode |
| ffmpeg | 8.0.1-1+av1v4l2.6 | FFmpeg with AV1/VP9 V4L2M2M support |
| gstreamer1.0-plugins-good | 1.26.9-1+av1v4l2 | GStreamer with v4l2av1dec element |
| libva-v4l2-stateful | 0.1.0-1 | VA-API driver for V4L2 decoders (deprecated) |

> **Note:** The libva/VA-API path is deprecated in favor of direct V4L2-M2M, which is more efficient and maintainable. Firefox, FFmpeg, and Chromium now use V4L2-M2M directly. Chromium uses unmodified Debian packages with the `chromium-sky1-config` configuration package enabling hardware decode. We plan to patch other popular applications that default to VA-API, such as video players and screen recorders.

### DKMS Drivers

| Package | Version | Description |
|---------|---------|-------------|
| r8126-dkms | 10.016.00-1 | Realtek RTL8126 5GbE driver |
| sky1-vpu-dkms | 1.0.0-1 | ARM Linlon MVE v8 VPU driver |
| sky1-npu-dkms | 1.0.0-2 | ARM Zhouyi V3 NPU driver (30 TOPS) |

## Source Repositories

| Repository | Description |
|------------|-------------|
| [linux-sky1](https://github.com/Sky1-Linux/linux-sky1) | Kernel source with 57 patches |
| [sky1-firmware](https://github.com/Sky1-Linux/sky1-firmware) | Firmware packaging |
| [sky1-drivers-dkms](https://github.com/Sky1-Linux/sky1-drivers-dkms) | DKMS drivers (r8126, VPU, NPU) |
| [chromium-sky1-config](https://github.com/Sky1-Linux/chromium-sky1-config) | Chromium V4L2-M2M config |
| [firefox-sky1](https://github.com/Sky1-Linux/firefox-sky1) | Firefox V4L2-M2M patches |
| [ffmpeg-sky1](https://github.com/Sky1-Linux/ffmpeg-sky1) | FFmpeg with V4L2 patches |
| [gstreamer-sky1](https://github.com/Sky1-Linux/gstreamer-sky1) | GStreamer with v4l2av1dec |
| [libva-v4l2-stateful](https://github.com/Sky1-Linux/libva-v4l2-stateful) | VA-API wrapper |
