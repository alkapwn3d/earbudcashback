# Monitor Errors

## Rule
Proactively check logs and error outputs for issues related to current work.

## When
- After installing/configuring software
- When user mentions "something's wrong" or "error"
- After system changes (services, configs, packages)
- During troubleshooting

## Where to Check
- Application logs: `journalctl -u service-name -n 50`
- User logs: `journalctl --user -n 50`
- App-specific: `~/.local/state/app/`, `~/.cache/app/`
- System: `/var/log/`
- Recent errors: `journalctl -p err -n 20`

## How
1. Check relevant logs first
2. Filter for errors/warnings: `grep -i "error\|warn"`
3. Fix root cause, not just symptoms
4. Verify fix worked

## Examples
- Working on nvim → Check `~/.local/state/nvim/lsp.log`
- Service issues → `journalctl -u service-name`
- Boot problems → `journalctl -b -p err`
- Package errors → Check pacman/paru output

## Don't
- Ignore error messages in command output
- Assume "no visible error" = "no error"
- Fix symptoms without checking logs
