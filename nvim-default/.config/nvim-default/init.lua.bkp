vim.g.mapleader = " "

-- require("options")
-- require("keymaps")
-- require("plugins")

-- Clipboard compartilhado com o sistema operacional
vim.opt.clipboard = "unnamedplus"

local function is_wsl()
  local file = io.open("/proc/sys/kernel/osrelease", "r")
  if not file then
    return false
  end

  local release = file:read("*a")
  file:close()

  return release:lower():find("microsoft", 1, true) ~= nil
end

if is_wsl() then
  -- WSL: integração com o clipboard do Windows
  vim.g.clipboard = {
    name = "WSLClipboard",
    copy = {
      ["+"] = "clip.exe",
      ["*"] = "clip.exe",
    },
    paste = {
      ["+"] = "powershell.exe -NoProfile -Command Get-Clipboard",
      ["*"] = "powershell.exe -NoProfile -Command Get-Clipboard",
    },
    cache_enabled = 0,
  }
end

