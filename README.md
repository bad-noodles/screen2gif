# screen2gif

A macOS command-line tool that records your screen and converts it to a high-quality GIF with a progress bar.

## Features

- 📹 Screen recording using macOS native `screencapture`
- 🎨 High-quality GIF conversion
- 📊 Real-time progress bar during conversion
- ⚡ Customizable frame rate and scale
- 🔄 Automatic cleanup of temporary files

## Requirements

- macOS (uses `screencapture`)
- FFmpeg (for video conversion)

## Installation

```bash
brew install bad-noodles/bad-noodles/screen2gif
```

## Usage

```bash
screen2gif [OPTIONS] <filename>
```

### Arguments
- `filename` - Output filename (without .gif extension)

### Options
- `-f, --fps FPS` - Frames per second (default: 10)
- `-s, --scale SIZE` - Scale width in pixels (default: 1920)
- `-r, --replace` - Replace existing output file if it exists
- `-h, --help` - Show help message

### Examples

```bash
# Basic usage - creates demo.gif at 10fps, 1920px wide
screen2gif demo

# Higher frame rate
screen2gif -f 15 demo

# Custom scale and frame rate
screen2gif -f 15 -s 1080 demo

# Replace existing file
screen2gif -r demo

# Full options
screen2gif --fps 20 --scale 720 my-recording
```

## How it Works

1. **Screen Recording**: Uses macOS `screencapture` to record your screen
2. **File Detection**: Automatically finds the newest .mov file created during recording
3. **Conversion**: Converts video to GIF using FFmpeg with optimized settings:
   - Generates custom palette for better quality
   - Uses Lanczos scaling for smooth resizing
4. **Progress Tracking**: Shows real-time progress bar during conversion
5. **Cleanup**: Removes temporary recording files

## Technical Details

- Uses FFmpeg's `palettegen` and `paletteuse` filters for optimal GIF quality
- Progress tracking via FFmpeg's progress output
- Lanczos scaling algorithm for high-quality resizing
- Automatic video duration detection for accurate progress calculation
