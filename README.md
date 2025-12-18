# VideoEdit

> Bash utilities for converting videos to WebM format optimized for Telegram with automatic quality and size management.

## Tools

### `vidcut` — Process single video

Converts a video file to WebM format with automatic quality adjustment, time trimming, and cropping.

```bash
vidcut input_file output_file [start_time] [end_time] [crop_w] [crop_h] [crop_x] [crop_y]
```

**Parameters:**
- `input_file` — Input video file (required)
- `output_file` — Output WebM file (required)
- `start_time` — Start time in seconds (default: 0)
- `end_time` — End time in seconds (default: full video)
- `crop_w`, `crop_h` — Crop dimensions in pixels (default: 100%)
- `crop_x`, `crop_y` — Crop position offset (default: 0)

**Examples:**
```bash
vidcut input.mp4 output.webm
vidcut input.mp4 output.webm 1 6
vidcut input.mp4 output.webm 0 0 720 720 0 150
```

**Features:**
- Time-based trimming
- Crop and scale to 512px max
- Automatic quality adjustment (CRF) to maintain ≤ 256 KB file size
- Optimized for Telegram (30fps, yuva420p format)
- No audio track

---

### `vidbatch` — Batch process all videos

Automatically converts all video files in a directory using `vidcut`.

```bash
vidbatch input_directory output_directory
```

**Supported formats:** MP4, MOV, WebM, MKV, AVI, FLV

**Example:**
```bash
vidbatch ~/videos ~/videos_processed
```

---

## Installation

### Requirements

```bash
# Ubuntu/Debian
sudo apt install ffmpeg bc

# macOS
brew install ffmpeg bc
```

### Setup

```bash
# Make executable
chmod +x bin/vidcut bin/vidbatch

# Option 1: Add to PATH
export PATH="$PATH:$(pwd)/bin"

# Option 2: Install globally
sudo cp bin/vidcut bin/vidbatch /usr/local/bin/
```

---

## License

MIT

