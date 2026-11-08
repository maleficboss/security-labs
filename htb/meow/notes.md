cd Downloads to change directory into the downloads folder
ls to llist folders in the directory
sudo openvpn starting.ovpn to start the openvpn 
mkdir -p ~/security-labs/htb/meow to create a dirsctory for notes
nano ~/security-labs/htb/meow/notes.md to create the notes.md file

Initialization Sequence Completed means connected, and that tab has to stay open.
tun0 = 10.10.15.94, your address on HTB’s network.
The ping got 0% loss with ttl=63, which suggests a Linux target.
Mistake: typing ` instead of ~ gave a bquote> prompt. Ctrl+C gets you out.
Mistake, if it’s what happened: the .ovpn was downloaded on Windows, so Kali couldn’t see it.

root should never be exposed over the network, and telnet should never be used at all. It sends everthing including passwords in plain text.
