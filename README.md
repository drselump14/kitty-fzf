# kitty-fzf

Fuzzy-find and jump to any [kitty](https://sw.kovidgoyal.net/kitty/) window (pane) or tab with [fzf](https://github.com/junegunn/fzf) — like [tmux-fzf](https://github.com/sainnhe/tmux-fzf), for kitty.

- Lists every pane across all OS windows and tabs as `tab › title`
- Live preview of the pane's screen; preview label shows its cwd and running command
- Opens as a centered floating panel (or an overlay / plain command)

## Requirements

kitty ≥ 0.42 with remote control, `fzf`, `jq`.

```conf
# kitty.conf
allow_remote_control yes
listen_on unix:/tmp/mykitty
```

## Install

```sh
git clone https://github.com/drselump14/kitty-fzf.git
ln -s "$PWD/kitty-fzf/kitty-fzf" ~/.local/bin/kitty-fzf
```

Add key mappings to `kitty.conf` (example uses a tmux-style `ctrl+space` prefix):

```conf
# floating centered panel
map ctrl+space>w launch --type=os-panel --os-panel edge=center-sized --os-panel lines=30 --os-panel columns=140 --os-panel focus-policy=exclusive --os-panel hide-on-focus-loss=yes --os-panel layer=overlay --allow-remote-control ~/.local/bin/kitty-fzf
map ctrl+space>t launch --type=os-panel --os-panel edge=center-sized --os-panel lines=30 --os-panel columns=140 --os-panel focus-policy=exclusive --os-panel hide-on-focus-loss=yes --os-panel layer=overlay --allow-remote-control ~/.local/bin/kitty-fzf tab

# or: overlay on top of the current pane
# map ctrl+space>w launch --type=overlay --allow-remote-control ~/.local/bin/kitty-fzf
```

## Usage

```sh
kitty-fzf        # pick a pane
kitty-fzf tab    # pick a tab
```

| Key | Action |
|---|---|
| `enter` | focus selection |
| `ctrl-x` | close selection |
| `ctrl-r` | reload list |
| `ctrl-/` | toggle preview |

## License

MIT
