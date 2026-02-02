# Sky1 Linux APT Repository

Debian packages for CIX Sky1 SoC (Radxa Orion O6/O6N).

## Usage

```bash
# Add repository key
wget -qO- https://sky1-linux.github.io/apt/key.gpg | sudo tee /usr/share/keyrings/sky1-linux.asc > /dev/null

# Add repository (LTS kernel — default)
echo "deb [signed-by=/usr/share/keyrings/sky1-linux.asc] https://sky1-linux.github.io/apt sid main non-free-firmware" | sudo tee /etc/apt/sources.list.d/sky1-linux.list

# Install
sudo apt update
sudo apt install linux-image-sky1 sky1-firmware
```

## Kernel Tracks

The repository has multiple components for different kernel tracks. Users opt-in by adding components to their sources.list. The `main` component is always required (firmware and multimedia live there).

| Track | Component | Meta Package | Description |
|-------|-----------|--------------|-------------|
| LTS | `main` | `linux-image-sky1` | Production kernel (6.18.x) |
| RC | `rc` | `linux-image-sky1-rc` | Release candidates (6.19-rcN) |
| Latest | `latest` | `linux-image-sky1-latest` | Latest stable (when 6.19 releases) |
| Next | `next` | `linux-image-sky1-next` | Bleeding-edge (Linus master) |

```bash
# LTS only (default)
deb .../apt sid main non-free-firmware

# LTS + RC testing
deb .../apt sid main rc non-free-firmware

# LTS + Latest stable
deb .../apt sid main latest non-free-firmware
```

To switch tracks, install the track's meta package:

```bash
# Switch to RC kernel
sudo apt install linux-image-sky1-rc linux-headers-sky1-rc

# Switch back to LTS
sudo apt install linux-image-sky1 linux-headers-sky1
sudo apt autoremove  # removes old track's kernel
```

## GPG Key

- **Key ID**: `48A0ABF100336ADB`
- **Fingerprint**: `7D7E E7FC 3675 9E50 D5C2 3CB3 48A0 ABF1 0033 6ADB`
- **Download**: [key.gpg](https://sky1-linux.github.io/apt/key.gpg)

## Available Packages

### Kernel — main (LTS)

| Package | Version | Description |
|---------|---------|-------------|
| linux-image-sky1 | 6.18.8 | Meta: latest LTS kernel image |
| linux-headers-sky1 | 6.18.8 | Meta: latest LTS kernel headers |
| linux-sky1 | 6.18.8 | Meta: image + headers |
| linux-image-6.18.8-sky1 | 1 | Linux 6.18.8 for Sky1 |
| linux-headers-6.18.8-sky1 | 1 | Kernel headers for module building |

### Kernel — rc

| Package | Version | Description |
|---------|---------|-------------|
| linux-image-sky1-rc | 6.19.0-rc8 | Meta: latest RC kernel image |
| linux-headers-sky1-rc | 6.19.0-rc8 | Meta: latest RC kernel headers |
| linux-sky1-rc | 6.19.0-rc8 | Meta: image + headers |
| linux-image-6.19.0-rc8-sky1-rc | 1 | Linux 6.19-rc8 for Sky1 |
| linux-headers-6.19.0-rc8-sky1-rc | 1 | Kernel headers for module building |

### Firmware (non-free-firmware)

| Package | Version | Description |
|---------|---------|-------------|
| sky1-firmware | 1.2.0 | GPU, DSP, VPU, WiFi firmware, HDMI audio UCM2 config |

### Multimedia

| Package | Version | Description |
|---------|---------|-------------|
| firefox | 146.0-1+v4l2m2m.2 | Firefox with V4L2-M2M hardware video decode |
| ffmpeg | 8.0.1-2+av1v4l2.1 | FFmpeg with AV1/VP9 V4L2-M2M support |
| chromium-sky1-config | 1.0.0-1 | Chromium V4L2-M2M hardware decode config |
| gstreamer1.0-plugins-good | 1.26.9-1+av1v4l2 | GStreamer with v4l2av1dec element |

> **Note:** Hardware video decoding uses V4L2-M2M directly. Chromium uses unmodified Debian packages with a config overlay. The libva-v4l2-stateful VA-API wrapper is deprecated.

### DKMS Drivers (deprecated — in-tree since 6.18.7-2)

| Package | Description |
|---------|-------------|
| r8126-dkms | Realtek RTL8126 5GbE (now built-in) |
| sky1-vpu-dkms | ARM Linlon MVE v8 VPU (now built-in) |
| sky1-npu-dkms | ARM Zhouyi V3 NPU (now built-in) |

These DKMS packages remain in the repo for older kernels but are no longer needed on 6.18.7+.

### Installer & First-Boot

| Package | Version | Description |
|---------|---------|-------------|
| calamares-settings-sky1 | 1.0.3-1 | Calamares installer branding and config |
| plasma-setup | 6.5.4-1sky1 | KDE Plasma first-boot user creation wizard |

## Source Repositories

| Repository | Description |
|------------|-------------|
| [linux](https://github.com/Sky1-Linux/linux) | Kernel source with Sky1 patches |
| [linux-sky1](https://github.com/Sky1-Linux/linux-sky1) | Patch series and configs for distribution |
| [sky1-linux-build](https://github.com/Sky1-Linux/sky1-linux-build) | Kernel package build scripts |
| [sky1-firmware](https://github.com/Sky1-Linux/sky1-firmware) | Firmware packaging |
| [chromium-sky1-config](https://github.com/Sky1-Linux/chromium-sky1-config) | Chromium V4L2-M2M config |
| [firefox-sky1](https://github.com/Sky1-Linux/firefox-sky1) | Firefox V4L2-M2M patches |
| [ffmpeg-sky1](https://github.com/Sky1-Linux/ffmpeg-sky1) | FFmpeg with V4L2 patches |
| [gstreamer-sky1](https://github.com/Sky1-Linux/gstreamer-sky1) | GStreamer with v4l2av1dec |
| [plasma-setup](https://github.com/Sky1-Linux/plasma-setup) | KDE Plasma first-boot wizard |
| [calamares-settings-sky1](https://github.com/Sky1-Linux/calamares-settings-sky1) | Calamares installer config |
