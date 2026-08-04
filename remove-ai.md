# Removing AI from 

## VS Code

*control + shift + p* search and select "Preferences: open user settings (JSON)"

add:

```
  "workbench.settings.showAISearchToggle": false,
    "chat.agent.enabled": false,
    "chat.commandCenter.enabled": false,
    "inlineChat.accessibleDiffView": "off",
    "terminal.integrated.initialHint": false,
    "github.copilot.enable": false,
    "chat.disableAIFeatures": true
```

save.
