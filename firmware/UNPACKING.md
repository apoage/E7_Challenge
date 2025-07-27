# Nokia E7 Firmware Unpacking Instructions

## Download and Extract Firmware Files

The Nokia E7 firmware files are distributed as compressed split archives to accommodate GitHub's file size limitations.

### Option 1: Download from GitHub Releases (Recommended)

1. **Download Split Archive Files:**
   Go to the [Releases page](../../releases/latest) and download all parts:
   ```
   RM-626-firmware.7z.001
   RM-626-firmware.7z.002
   RM-626-firmware.7z.003
   (etc... download all numbered parts)
   ```

2. **Extract Split Archive:**
   ```bash
   # Place all .7z.001, .7z.002, etc. files in the same directory
   # Extract using the first part (7zip will automatically find others)
   7z x RM-626-firmware.7z.001
   
   # Alternative using p7zip on Linux/macOS
   7za x RM-626-firmware.7z.001
   ```

3. **Verify Extraction:**
   ```bash
   # Check that all firmware files are present
   ls -la RM-626/
   
   # Expected files:
   # RM-626_111.040.1511_79u_prd.core.fpsx
   # RM-626_111.040.1511_01.01_Euro1_QW_79u_prd.rofs2.fpsx
   # RM-626_111.040.1511_C00.01_79u_prd.rofs3.fpsx
   # RM-626_111.040.1511_U01.01_79u.uda.fpsx
   # RM626_APE_ONLY_ENO_11w36_v0.037.fpsx
   # RM626_0591821_111.040.1511_015.dcp
   # RM626_0591821_111.040.1511_015.vpl
   # RM626_0591821_111.040.1511_015_signature.bin
   ```

### Option 2: Download Complete Archive (External Link)

If you prefer to download the complete firmware package in one file:

1. **Download from External Storage:**
   [Download Complete Firmware (152MB)](https://example.com/RM-626-complete.7z)
   *(Link will be provided in releases)*

2. **Extract Complete Archive:**
   ```bash
   7z x RM-626-complete.7z
   ```

## File Verification

### Check File Integrity
```bash
# Verify archive integrity before extraction
7z t RM-626-firmware.7z.001

# Expected output: "Everything is Ok"
```

### Verify File Checksums
```bash
# Compare with provided checksums
sha256sum RM-626/*.fpsx RM-626/*.dcp RM-626/*.vpl RM-626/*.bin

# Expected checksums (will be provided in releases)
```

## Prerequisites for Extraction

### Install 7zip
```bash
# Ubuntu/Debian
sudo apt install p7zip-full

# macOS (using Homebrew)
brew install p7zip

# Windows
# Download from: https://www.7-zip.org/download.html
```

### Required Disk Space
- **Compressed files:** ~152MB (split into ~6-7 parts of 25MB each)
- **Extracted files:** ~248MB
- **Total space needed:** ~400MB (during extraction process)

## Troubleshooting

### Missing Split Archive Parts
**Error:** "Can not open the file as archive"
**Solution:** Ensure all numbered parts (.001, .002, .003, etc.) are in the same directory

### Insufficient Disk Space
**Error:** "Not enough space on disk"
**Solution:** Free up at least 400MB of disk space before extraction

### Corrupted Download
**Error:** "Data error" or "CRC failed"
**Solution:** 
1. Re-download the corrupted part(s)
2. Verify checksums match expected values
3. Try extracting again

### Permission Issues (Linux/macOS)
**Error:** "Permission denied"
**Solution:**
```bash
# Make sure you have write permissions
chmod 755 .
# Or extract to a directory you own
mkdir ~/e7-firmware && cd ~/e7-firmware
```

## Alternative Extraction Methods

### Using GUI Tools
- **Windows:** Right-click → "Extract Here" (with 7zip installed)
- **macOS:** Use The Unarchiver or Keka
- **Linux:** Use your file manager's built-in archive support

### Using Python (if 7zip unavailable)
```python
import py7zr
with py7zr.SevenZipFile('RM-626-firmware.7z.001', mode='r') as archive:
    archive.extractall(path='.')
```

## After Extraction

1. **Move files to correct location:**
   ```bash
   # If extracted to RM-626/ subdirectory
   mv RM-626/* firmware/
   rmdir RM-626
   ```

2. **Verify challenge setup:**
   ```bash
   # Check repository structure
   ls -la firmware/
   ls -la documentation/
   cat challenge_prompt.md
   ```

3. **Clean up archives (optional):**
   ```bash
   # Remove downloaded archive parts to save space
   rm RM-626-firmware.7z.*
   ```

## File Descriptions

| File | Description | Size |
|------|-------------|------|
| `core.fpsx` | Main firmware (bootloader, kernel, drivers) | ~85MB |
| `rofs2.fpsx` | System applications and libraries | ~45MB |
| `rofs3.fpsx` | Regional content and localization | ~35MB |
| `uda.fpsx` | User data area structure | ~25MB |
| `APE_ONLY_ENO_11w36_v0.037.fpsx` | Cellular modem firmware | ~40MB |
| `*.dcp` | Device configuration package | ~8MB |
| `*.vpl` | Variant product line configuration | ~5MB |
| `*_signature.bin` | Cryptographic signatures | ~1MB |

## Security Notice

- **Verify checksums** before using firmware files
- **Scan extracted files** with antivirus if concerned
- **Only use files** from official E7 Challenge releases
- **Report suspicious files** via GitHub issues

## Ready to Start the Challenge!

Once firmware extraction is complete, you can begin the E7 AI Demoscene Challenge:

```bash
# Verify everything is ready
ls firmware/        # Should show 8 firmware files
ls documentation/   # Should show service manuals and schematics
cat challenge_prompt.md  # Review the challenge instructions

# Start with your preferred AI platform
gemini run challenge_prompt.md --context . --mode=agentic
```

For questions about firmware extraction, please check the [FAQ](../FAQ.md) or open an issue on GitHub.
