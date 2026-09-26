This document is a collection of ideas/problems and commands I have come across that might be useful. 


# Useful Commands
## Check your laptop charging rate (Windows)
```bash
gwmi -Class batterystatus -Namespace root\wmi | Select-Object ChargeRate, Charging, DischargeRate, Discharging, PowerOnline, RemainingCapacity
```

# Useful ideas/platforms
## Self-hosted LaTeX:
Follow this [link](https://github.com/overleaf/toolkit/blob/master/doc/quick-start-guide.md). 
Probably need to install these packages in Docker:
```
docker exec -it sharelatex bash
```
and
```
tlmgr install float listings pdfpages titlesec subfigure collection-mathscience collection-latexrecommended
```
Or do:
```
tlmgr install \
        collection-latexrecommended \
        collection-latexextra \
        collection-fontsrecommended \
        collection-mathscience
```

## Cloudflare tunnel/proxy 
This is when you want to port forward your web server to the world without opening firewall ports.
See the [setup guide](https://developers.cloudflare.com/tunnel/get-started/). 


# Random tips and Tricks

## Feko Completion Message
Add
```lua
file:write(winln([[curl.exe -d "Sim is done: %date% %time%" https://ntfy.sh/ntfy_server_name]]))
```
To File ``C:\ProgramData\altair\feko\2026.0_xxx\installedapplicationmacrolibrary\Shared\ParameterSweep\utils\parameter_sweep_helper.lua`` around line 487. <br>
You can also add code in the Lua script, such as:
```lua
local message = "Sim started: ".. os.date("%Y-%m-%d %H:%M:%S")
    os.execute(string.format(
        'curl.exe -d "%s" https://ntfy.sh/ntfy_server',
        message
    ))
```
Or if it's a normal sim and you're just doing a large sweep of frequencies, the easiest is to use the Feko terminal and add your commands, like so:
```bash
runfeko project_XXX --run-from-gui && curl.exe -d "Sim is done: %date% %time%" https://ntfy.sh/ntf_server
```


## ESP to ESP Flashing:
```
WORKING ESP32 DEVKIT                 TARGET ESP32 DEVKIT
────────────────────                 ──────────────────
USB-UART TX  ──────────────────────> U0RXD / GPIO3
USB-UART RX  <────────────────────── U0TXD / GPIO1
GND          ──────────────────────> GND
EN / RESET <───> GND                 NA 
```




