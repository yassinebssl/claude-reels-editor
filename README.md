# Claude reels editor

A Claude Code skill: six data-driven Remotion overlay effects for talking-head reels (over-the-shoulder cards, glass chart, freeze-frame sticker, tier list, text behind, colour-grade wipe). Every number is read from a file, never invented.

## Install

```bash
git clone https://github.com/yassinebssl/claude-reels-editor.git ~/.claude/skills/claude-reels-editor
```

Claude Code picks it up on the next session. Works best with the Remotion plugin (`claude plugin marketplace add remotion-dev/claude-code-plugin`, then `claude plugin install remotion@remotion`).

## Needs

Node.js, a Remotion project, a vertical talking-head clip (1080x1920 ideal), and for cut-outs a person segmentation tool (MediaPipe or rembg on Linux/Windows, Apple Vision on macOS).

## Credits

Effects adapted from the "6 Claude prompts that edit my reels" pack by @brodyautomates. The specs in this skill are rewritten summaries, not the original prompts.
