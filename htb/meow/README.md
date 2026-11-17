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



## Setup
- Target: HTB Starting Point, Meow (Tier 0, Linux). Attack machine: Kali VM in VirtualBox.
- Started the machine from the Meow page to get the target IP.
- Downloaded the Starting Point VPN file inside Kali and connected with `sudo openvpn starting.ovpn`.
  "Initialization Sequence Completed" means connected and the terminal must stay open, because
  closing it drops the VPN, so everything else ran in a second tab.
- Checked my address on HTB's network: `ip a show tun0`.
- Checked the target was reachable: `ping -c 3 <target IP>`. Replies came back with `ttl=63`.
  Linux usually starts at 64 and one router took 1 off, so the target is likely Linux.

## Mistakes and lessons
- Downloaded the VPN file in Windows first. Kali is a separate machine so it  couldn't see it;
  downloading it from Firefox inside Kali fixed it.
- `ping -c <target IP>` resulted in  "invalid argument". `-c` needs a number straight after it, so
  ping read the IP as the count. `ping -c 3 <target IP>` worked.
- Typed a backtick instead of `~` and the shell waited for a closing backtick (the `bquote>`
  prompt); Ctrl+C got me out.

## Recon
- Scanned the target for open ports and service versions: `nmap -sV <target IP>`
- Result: `23/tcp open telnet Linux telnetd`
- `-sV` makes Nmap connect to the service and identify it, instead of guessing from the
  port number. "Linux" here matches the ttl=63 clue from Setup.

## Access
- Port 23 runs telnet which is an old service for logging into another host over the network.
- Connected to it: `telnet <target IP>`
- At the `Meow login:`prompt, I tried `root`, the system's most powerful account.
  It did not ask for a password, so I pressed Enter and was logged straight in.
- The prompt became `root@Meow:~#`. The `#` means I am root; a normal user gets `$`.
- `ls` showed `flag.txt` in root's home directory.

## Why it worked, and the fix
Three separate misconfigurations had to line up. Fixing any one would have stopped me.
1. while telnet is running, it sends everything passwords included, in plain text. SSH (what I use
   for Bandit) encrypts the session; telnet should have been off and SSH used instead.
2. root could log in over the network. That account should not be reachable remotely at all;
   you log in as a normal user and raise privileges only when needed.
3. root had no password. Every account, root above all, needs a strong one.

## Summary
Meow is a Linux box running telnet on port 23. Its root account had no password, so a telnet
login as `root` with a blank password gave access to the full root shell. The single most important fix is
turning telnet off and using SSH, which would have closed the plain-text path in one step.
