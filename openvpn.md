# OpenVPN

[OpenVPN](https://openvpn.net/index.php/access-server/docs/quick-start-guide/495-connecting-to-openvpn-access-server-using-the-connect-client-on-mac.html) is used for connecting to secure environments. I need to download the client and and configuration file from our VPN server, and then use it to connect to our secure environments.

## Install

Go to <https://openvpn-ops.aws.defra.cloud>, enter username and password and make sure to choose `login` rather than `connect`. I should then come to a screen with a link to download the Mac version of the client, plus my profile.

Download both, and run the client install first just hitting next (there is nothing to configure).

Once installed select `Import -> From local file` and then browse to the profile you downloaded. It will be called `client.ovpn`.

That's it. It should now be ready to use. Connect entering the same username and password again.

