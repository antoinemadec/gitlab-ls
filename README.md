# Gitlab-ls

## Setup
Example with Neovim:

`.config/nvim/lsp/gitlab-ls.lua`:
```lua
return {
  cmd = { '/home/antoine/src/gitlab-ls/gitlab-ls.sh' },
  filetypes = { 'txt', 'indentcolor' },
  init_options = {
    url = os.getenv("GITLAB_URL"),
    private_token = os.getenv("GITLAB_API_TOKEN"),
    projects = { os.getenv("GITLAB_PROJECTS") },
  },
}

`init.lua`:
```lua
vim.lsp.enable('gitlab-ls')
```

## Credit
Forked from [jrmsgr's gitlab-ls](https://github.com/jrmsgr/gitlab-ls)
