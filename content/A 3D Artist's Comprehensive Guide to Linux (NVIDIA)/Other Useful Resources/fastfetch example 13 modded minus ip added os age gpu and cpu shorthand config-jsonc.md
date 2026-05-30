```config.jsonc
// Inspired by Catnap
{
    "$schema": "https://github.com/fastfetch-cli/fastfetch/raw/dev/doc/json_schema.json",
    "logo": {
        "type": "small",
        "padding": {
            "top": 1
        }
    },
    "display": {
        "separator": " "
    },
    "modules": [
        {
            "key": "╭───────────╮",
            "type": "custom"
        },
        {
            "key": "│ {#31} user    {#keys}│",
            "type": "title",
            "format": "{user-name}"
        },
        {
            "key": "│ {#32}󰇅 hname   {#keys}│",
            "type": "title",
            "format": "{host-name}"
        },
        {
            "key": "│ {#33}󰅐 uptime  {#keys}│",
            "type": "uptime"
        },
        {
            "key": "│ {#34}{icon} distro  {#keys}│",
            "type": "os"
        },
        {
            "key": "│ {#35} kernel  {#keys}│",
            "type": "kernel"
        },
        {
            "key": "│ {#36}󰇄 desktop {#keys}│",
            "type": "de"
        },
        {
            "key": "│ {#31} term    {#keys}│",
            "type": "terminal"
        },
        {
            "key": "│ {#32} shell   {#keys}│",
            "type": "shell"
        },
//        {
//            "key": "│ {#33}󰍛 cpu     {#keys}│",
//            "type": "cpu",
//            "showPeCoreCount": true
//        },
        {
            "type": "command",
            "key": "│ {#34}󰉉 cpu     {#keys}│",
            "text": "name=$(grep -m1 'model name' /proc/cpuinfo | sed 's/.*: //;s/11th Gen Intel(R) Core(TM) //;s/ @ .*//'); cores=$(nproc); freq=$(lscpu | grep 'CPU max MHz' | awk '{printf \"%.1f\", $NF/1000}'); echo \"$name ($cores) @ ${freq}GHz\""
        },
        {
            "type": "gpu",
            "key": "│ {#35} gpu     {#keys}│",
            "keyColor": "green"
        },
        {
            "key": "│ {#36}󰉉 disk    {#keys}│",
            "type": "disk",
            "folders": "/"
        },
        {
            "key": "│ {#37} memory  {#keys}│",
            "type": "memory"
        },
        {
            "type": "command",
            "key": "│ {#38} os age  {#keys}│",
            "keyColor": "magenta",
            "text": "birth_install=$(stat -c %W /); current=$(date +%s); time_progression=$((current - birth_install)); days_difference=$((time_progression / 86400)); echo $days_difference days"
        },
        {
            "key": "├───────────┤",
            "type": "custom"
        },
        {
            "key": "│ {#39} colors  {#keys}│",
            "type": "colors",
            "symbol": "circle"
        },
        {
            "key": "╰───────────╯",
            "type": "custom"
        }
    ]
}

```
