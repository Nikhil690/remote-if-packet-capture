## Setup dependencies
Install wireshark

```
sudo apt install wireshark tcpdump

```
Make a FIFO pipe file without any extension (don't make file like filename.pcap or something)
```
mkfifo /tmp/<filename>

```
## Packet Capturing Proccess
Start Wireshark capturing with the following command:
```
wireshark -k -i /tmp/<filename>

```
In another terminal, execute the SSH command:
```
ssh <user>@<remote ip address> "sudo tcpdump -s 0 -U -n -w - -i <interface name> not port <port no.>" > /tmp/filename
```
and for multiple ports:
```
ssh <user>@<remote ip address> "sudo tcpdump -s 0 -U -n -w - -i <interface name> not port <port no.> and not port <port no.>" > /tmp/filename
```

and if the remote host require sudo password:
```
ssh <user>@<remote ip address> "echo <password> | sudo -S tcpdump -s 0 -U -n -w - -i <interface name> not port <port no.> and not port <port no.>" > /tmp/filename

