## Setup dependencies
Install wireshark

```
sudo apt install wireshark tcpdump

```
Make a FIFO pipe file
```
mkfifo /tmp/filename

```
## Packet Capturing Proccess
Wireshark command for start capturing
```
wireshark -k -i /tmp/filename

```
On other terminal ssh command
```
ssh <user>@<remote ip address> "sudo tcpdump -s 0 -U -n -w - -i <interface name> not port 22" > /tmp/filename
```
