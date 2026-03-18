# Gitlab-ls

## Setup
Example with Neovim:

`.config/nvim/lsp/gitlab-ls.lua`:
```lua
local url = os.getenv("GITLAB_URL")
local private_token = os.getenv("GITLAB_API_TOKEN")
local projects = {}
local projects_str = os.getenv("GITLAB_PROJECTS")
if projects_str then
  for proj in string.gmatch(projects_str, "[^ ]*") do
    table.insert(projects, proj)
  end
end

if not url or not private_token or #projects == 0 then
  return {}
end

return {
  cmd = { vim.fn.stdpath("data") .. '/lazy/gitlab-ls/gitlab-ls.sh' },
  filetypes = { 'txt', 'indentcolor' },
  init_options = {
    url = url,
    private_token = private_token,
    projects = projects,
  },
}
```

`init.lua`:
```lua
vim.lsp.enable('gitlab-ls')
```

## Credit
Forked from [jrmsgr's gitlab-ls](https://github.com/jrmsgr/gitlab-ls)
