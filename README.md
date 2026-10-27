# Ghost in the Machine

Haunted terminal + revived fortune teller. Built for Hacktober Week 4: "Ghost in the Machine" - bringing abandoned open-source tech back from the dead with open-weight AI at its core.

## Story

In the quiet corners of UNIX history, `fortune-mod` sat forgotten. A simple oracle that once amused generations of hackers with its dry wit and groan-worthy puns, it had been left behind as computing moved on. 

For Día de los Muertos and Halloween, we remember not just the people who came before us, but the programs too. Like candles on an ofrenda, these forgotten tools deserve to be brought back to life. 

Rather than rebuilding it from scratch, *ghost-fortune* possesses the old oracle - whispering eerie follow-ups through a local open-weight model, or channeling entirely new cursed fortunes from beyond. All while keeping the original archive alive as a fallback. The spirits of old UNIX live on, now haunted by modern AI running entirely on your machine.

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
Revives the forgotten `fortune` oracle. Possesses it with a local open-weight model, or generates cursed fortunes from scratch. Now also tells haunted tales from forgotten terminals.

```bash
# Interactive haunted UI
./ghost-fortune

# Quick modes
./ghost-fortune --classic   # Untouched original fortune
./ghost-fortune --haunt     # Possess a classic fortune with AI whisper
./ghost-fortune --possess   # Generate a brand new cursed fortune
./ghost-fortune --tale      # Tell a haunted tale from the machine's memory
./ghost-fortune --tale-ai   # Channel a brand new tale from beyond
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
