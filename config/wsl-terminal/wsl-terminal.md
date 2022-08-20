# WSL Terminal Configuration

1.  Add the color scheme `One Dark` to your colorschemes in Windows Terminal's `settings.json`

    ```json
    {
    "background": "#1E2127",
    "black": "#000000",
    "blue": "#61AFEF",
    "brightBlack": "#5C6370",
    "brightBlue": "#61AFEF",
    "brightCyan": "#56B6C2",
    "brightGreen": "#98C379",
    "brightPurple": "#C678DD",
    "brightRed": "#E06C75",
    "brightWhite": "#FFFFFF",
    "brightYellow": "#D19A66",
    "cursorColor": "#FFFFFF",
    "cyan": "#56B6C2",
    "foreground": "#A0A0A0",
    "green": "#98C379",
    "name": "One Dark",
    "purple": "#C678DD",
    "red": "#E06C75",
    "selectionBackground": "#FFFFFF",
    "white": "#DBDBDB",
    "yellow": "#D19A66"
    },
    ```

2.  Add the variable `colorScheme` for **each distro**:

    ```json
    "list": 
    [
        {
            "colorScheme": "One Dark",
            "commandline": "%SystemRoot%\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
            "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
            "hidden": false,
            "name": "Windows PowerShell"
        },
    ```