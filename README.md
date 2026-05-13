# Google Drive Video Transcriber

[![Open In Colab](https://colab.research.google.com/drive/1OlqmNquOI81OhFptrFSY0CD8pJUkT1hM?usp=sharing)

Transcribe any public Google Drive video to text using **faster-whisper large-v3 or tyny-whisper** running on a free Colab T4 GPU.

## Features

- Transcribes directly from a Google Drive share link — no manual downloading
- Uses the `large-v3` or `tiny-v3` Whisper model for high accuracy
- GPU-accelerated via CUDA (float16) on Colab's free T4
- Extracts audio with ffmpeg before transcription (handles any video format)
- Saves the transcript as a `.txt` file in `/content/`
- Two-cell design: load the model once, transcribe as many videos as you want

## Usage

1. Open the notebook in Google Colab using the badge above.
2. Make sure the runtime is set to **T4 GPU**: `Runtime → Change runtime type → T4 GPU`.
3. **Run Cell 1 once** — installs dependencies and loads the model (~3 GB, takes a few minutes on first run).
4. **Run Cell 2 for each video** — paste a public Google Drive share link and set an output filename. The model stays in memory between runs.

## Requirements

Everything runs inside Colab — no local setup needed. Dependencies installed automatically:

- [`faster-whisper`](https://github.com/SYSTRAN/faster-whisper)
- [`gdown`](https://github.com/wkentaro/gdown)
- `ffmpeg` (pre-installed on Colab)
- `torch` / CUDA (provided by the Colab T4 runtime)

## Supported Link Formats

The notebook parses all standard Google Drive share URL formats:

```
https://drive.google.com/file/d/FILE_ID/view?usp=sharing
https://drive.google.com/open?id=FILE_ID
FILE_ID (raw ID string)
```

> The video must be publicly accessible (anyone with the link can view).

## Output

The transcript is saved to `/content/<output_name>.txt` and also printed in the cell output. Download it from the Colab file browser on the left sidebar.

## License

MIT
