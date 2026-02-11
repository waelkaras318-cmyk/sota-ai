# sota-ai
# sota-ai

Generate a long AI video (around 20 minutes) from a single topic.

## What this does

`long_video_generator.py` builds an end-to-end pipeline:

1. Generates a multi-section narration script with OpenAI.
2. Converts each section to speech (MP3) with OpenAI TTS.
3. Builds one simple visual clip per section with `ffmpeg`.
4. Concatenates clips into one final MP4.

The result is a ready-to-upload long-form video with narration and title cards.

## Requirements

- Python 3.10+
- `ffmpeg` and `ffprobe` on your PATH
- OpenAI API key
- Python dependency:

```bash
pip install openai
```

## Usage

```bash
export OPENAI_API_KEY="your_key_here"
python long_video_generator.py "The future of AI in healthcare" \
  --target-minutes 20 \
  --section-count 8 \
  --voice alloy \
  --output ai_healthcare_20min.mp4
```

## Tips for quality

- Increase `--section-count` to 10-12 for smoother pacing.
- Use a topic with clear subtopics (history, trends, risks, future).
- After generation, optionally add B-roll, music, and subtitles in an editor.

## Output files

- Intermediate assets are saved in `build_video/` by default.
- Final video is written to `video_20min.mp4` (or `--output`).
