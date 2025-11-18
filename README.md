Have to include this line in `sudo visudo` for VPN to work
```
krayon ALL=(root) NOPASSWD: /home/krayon/.scripts/openfortivpn
```


openfortivpn script (~/.scripts/openfortivpn)
```
if [[ $1 == "print" ]];then
  if [[ -z $(pgrep openfortivpn) ]];then
    echo "Disconnected";
    exit 0
  fi

  echo "Connected";
  exit 0
fi

if pgrep openfortivpn; then
  sudo killall -9 openfortivpn
else
  sudo openfortivpn <VPN_PROVIDER_DOMAIN_HERE> --saml-login & xdg-open "https://<VPN_PROVIDER_DOMAIN_HERE>/remote/saml/start?redirect=1"
fi

exit 0
```
