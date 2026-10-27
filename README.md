# Ghost in the Machine

Haunted terminal + revived fortune teller. Built for Hacktober Week 4: "Ghost in the Machine" - bringing abandoned open-source tech back from the dead with open-weight AI at its core.

## Tools

### `ghost` - Haunted terminal
Asks a local open-weight model for a one-line spooky comment on your last shell command.

```bash
# Run with last command
./ghost

# Or pass command explicitly
./ghost "rm -rf /tmp/test"
```

### `ghost-fortune` - Possessed fortune teller
Revives the forgotten `fortune` oracle. Possesses it with a local open-weight model, or generates cursed fortunes from scratch.

```bash
# Interactive haunted UI
./ghost-fortune

# Quick modes
./ghost-fortune --classic  # Untouched original fortune
./ghost-fortune --haunt    # Possess a classic fortune with AI whisper
./ghost-fortune --possess  # Generate a brand new cursed fortune
```

## Why open?
- **Open core**: Uses open `fortune` archives (when present) + runs on open-weight models via any OpenAI-compatible local server (Ollama, OpenWebUI, LMDeploy, etc.). Swappable with `GHOST_MODEL`.
- **Revival, not replacement**: Falls back to embedded public-domain fortunes if `fortune-mod` isn't installed. The archive lives on.
- **Local first**: Everything stays on your machine. Fortunes and prompts never leave your laptop.
- **Offline capable**: Works air-gapped with a cached local model. If no model is reachable, it gracefully degrades to classic fortunes.
- **$0 to run**: After pulling a model, free.
- **Flexible**: Swap models/personas with env vars, no code changes needed.
- **Privacy**: No telemetry, no API keys, no third-party servers.

## Config
```bash
export GHOST_HOST="http://localhost:11434"  # OpenAI-compatible or Ollama
export GHOST_MODEL="llama-3.2:3b"           # any local open-weight model
```

## Notes
- `ghost-fortune` has a proper TUI (colors, boxes, menu). Falls back gracefully.
- No shell auto-hooks (intentionally). Avoids footguns.
- `shortcut: no fortune binary installed by default; ceiling: uses tiny embedded corpus as fallback; upgrade: bundle fortune-mod + full open fortune dbs.`
- `shortcut: depends on local server for AI modes; ceiling: no offline fallback model bundled; upgrade: embed llama.cpp + gguf.`
- `shortcut: naive parsing; ceiling: quotes/newlines may break; upgrade: use stdlib json.`
