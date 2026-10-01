# Codex Browser File Upload

`browser-file-upload` is a Codex skill for reliable, filename-aware uploads from a local computer to a website using Codex browser or computer-use tools.

It covers:

- exact local-file and destination verification;
- visible and custom upload controls;
- browser file-chooser handling;
- Chrome extension permission recovery;
- the required full Chrome quit/reopen after permission changes; and
- upload, form-save, reload, and persistence verification.

This is a community Codex skill, not an official OpenAI product or a general Chrome extension.

## Install in Codex

macOS or Linux:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/dilan95x/codex-browser-file-upload.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/browser-file-upload"
```

Windows PowerShell:

```powershell
$codexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME ".codex" }
New-Item -ItemType Directory -Force -Path (Join-Path $codexRoot "skills") | Out-Null
git clone https://github.com/dilan95x/codex-browser-file-upload.git `
  (Join-Path $codexRoot "skills\browser-file-upload")
```

Start a new Codex turn after installation. The skill should activate when Codex is asked to upload a file to a website.

## Chrome permission recovery

If the upload chooser is blocked and the browser extension permission is implicated:

1. Open `chrome://extensions`.
2. Open the browser extension's **Details** page.
3. Enable **Allow access to file URLs**.
4. Fully quit Chrome and reopen it—not just the tab.
5. Retry the upload and verify the saved result.

Never upload a file unless the user has authorized the exact file and destination. Never claim success from file selection alone; the skill verifies the website's receipt and the enclosing form's saved state.

## Files

- `SKILL.md` — workflow instructions and safety rules.
- `agents/openai.yaml` — Codex display metadata and implicit activation.

## License

MIT. See [LICENSE](./LICENSE).
