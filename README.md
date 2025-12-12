# Sky1 Linux APT Repository

Debian packages for CIX Sky1 SoC (Radxa Orion O6).

## Usage

```bash
# Add repository key (fingerprint: 7D7EE7FC36759E50D5C23CB348A0ABF100336ADB)
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

### main
- `linux-image-6.18-sky1` - Linux kernel for Sky1
- `linux-headers-6.18-sky1` - Kernel headers
- `linux-dtbs-6.18-sky1` - Device tree blobs

### non-free-firmware
- `sky1-firmware` - GPU, DSP, and VPU firmware

## Links

- [linux-sky1](https://github.com/sky1-linux/linux-sky1) - Kernel source
- [sky1-firmware](https://github.com/sky1-linux/sky1-firmware) - Firmware source
