use matte black omarchy theme

useful apps
```
LACT, handbrake, losslesscut, sourcegit
use slack-desktop-wayland with tray-delay conf for system tray working correctly
```

vpn script (~/.scripts/vpn)
```
#!/bin/bash

if [[ $1 == "print" ]];then
  if pgrep openfortivpn > /dev/null; then
    echo "Connected 🌐";
  else 
    echo " ";
  fi
else
  if pgrep openfortivpn; then
    killall -9 openfortivpn
  else
    sudo -u krayon xdg-open "https://<VPN_PROVIDER_DOMAIN>/remote/saml/start?redirect=1" &
    openfortivpn <VPN_PROVIDER_DOMAIN> --saml-login &
  fi
fi
```
split-monitor-workspaces hypr plugin (https://github.com/Duckonaut/split-monitor-workspaces)
