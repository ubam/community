# VPN PIA

Use the openvpn settings files provided by PIA. *(I haven't tested the others like the advanced openvpn-IP configuration but had a problem using the openvpn-strong set. The settings below is what I tested and this works, some tweaks may be required for improved security)*


- download file: https://www.privateinternetaccess.com/openvpn/openvpn.zip
- create a folder `.privateinernetaccess` in `~` (`/home/phablet`) extract the file there

All the settings can be found in the ovpn file if you open it with a text editor

- In VPN settings: `Add Manual Configuration`
- `server`: *enter the server you will be using, e.g.* `uk-london.privateinternetaccess.com`
- *Use a custom gateway port:* `1198`
- *Tick* Use this VPN for `All network connections`
- Protocol: `UDP`
- Authentication type: `Password`
- Username: *Your PIA username* `Pxxxx`
- Password: *(Your password)*
- CA Certificate: *Select the file* `ca.rsa.2048.crt`
- Cipher: `AES-128-CBC` *and select* `Compress data`

The settings above worked fine for me. This can be setup with the default VPN settings if you installed the click package `VPN Editor`

The only other setting to change is under `Security` section Choose `SHA-1` as the `HMAC` authentication.

This is not needed to work but it is a defined in the ovpn profile provided by PIA.


I did try a number of different settigns but they seemd to fail and the above worked. I tested that IP address of my phone with a *what is my ip* search on duckduck go. I did not test the actual encryption of traffic etc. This may require someone with more skill than me.


# Authors/Contributors

- ? *(original author)*
