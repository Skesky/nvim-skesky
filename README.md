# nvim-skesky

## Multiple configuration

To have multiple configuration of neovim one option is to add the code below to the shell configuration file (e.g. .zshrc)

```bash
vv() {
        # Assume all configs exist in directories names ~/.config/nvim-*
        local config=$(fd --max-depth 1 --glob 'nvim-*' ~/.config | fzf --prompt="Neovim Configs > " --height=30% --layout=reverse --border --exit-0)

        # If I exit fzf without selecting a config, don't open Neovim
        [[ -z $config ]] && echo "No config selected" && return

        # Open Neovim with the selected config
        NVIM_APPNAME=$(basename $config) nvim $@
}
```

