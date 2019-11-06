# OpenVPN

[OpenVPN](https://openvpn.net/index.php/access-server/docs/quick-start-guide/495-connecting-to-openvpn-access-server-using-the-connect-client-on-mac.html) is used for connecting to secure environments. I need to download the client and configuration file from our VPN server, and then use it to connect to our secure environments.

## Install

First download the Mac Beta client from <https://openvpn.net/vpn-server-resources/connecting-to-access-server-with-macos/#future-replacement-for-openvpn-connect-client>. After switching to it, it appears to give a more consistent connection than the current standard version.
Then go to <https://openvpn-ops.aws.defra.cloud>, enter username and password and make sure to choose `login` rather than `connect`. I should then come to a screen with a link to download my profile.

Install the beta client and when complete open it up. The initial splash screen should give you the option to import a profile. Select it and choose the downloaded profile. It will be called `client.ovpn`.

Be sure to save the password, and from then on you'll just need the Google authenticator code to login.
