# Cursor Pocket

**Android remote for Cursor on your Mac.** Type a prompt on the phone. Cursor desktop on the MacBook gets it (paste + Send). The phone shows the reply and what files were fixed, then notifies you when it finishes.

Cursor has no Android app. The official iOS app is cloud / Remote Control, not this. Pocket is **Cursor-only**.

**Mac + Android walkthrough:** [MACBOOK_ANDROID.md](MACBOOK_ANDROID.md)

```text
  Android phone                          MacBook (awake, unlocked)
  ┌─────────────────┐                    ┌──────────────────────────┐
  │ Type a prompt   │  Wi-Fi / internet  │ Cursor desktop open      │
  │                 │ ─────────────────► │ python3 -m cursor_pocket │
  │ Reply + files   │ ◄───────────────── │ paste prompt, click Send │
  │ Finished ping   │                    │ Accessibility required   │
  └─────────────────┘                    └──────────────────────────┘
```

```bash
git clone https://github.com/seethinajayadileep/Cursor-Pocket.git
cd Cursor-Pocket
python3 -m cursor_pocket --workspace ~/Projects/my-app
```

Leave Cursor open. Grant **System Settings → Privacy & Security → Accessibility** to Terminal (or Python). The Mac must stay **awake and unlocked**.

On the phone: open the URL from the terminal, enter the PIN, tap **Install Android app (APK)** if an APK is built, or Chrome → Add to Home screen.

| Flag | Use |
|---|---|
| `--online` | Phone on another network (Cloudflare or ngrok) |
| `--demo --pin 123456` | Try the phone UI without Cursor |
| `--cli` | Cursor CLI instead of clicking Send in the desktop app |

More architecture notes: [CURSOR_POCKET.md](CURSOR_POCKET.md)

## Tests

```bash
python3 -m unittest discover -s tests -v
```

Linux CI cannot launch Cursor.app. Desktop Send is mocked there. Real Send-click needs a Mac + Android.

## License

MIT. See [LICENSE](LICENSE).
