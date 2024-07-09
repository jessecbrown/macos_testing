**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: Yes (Blocked)
* Enterprise YARA Solution: Yes

From the prior test, "Microsoft Word Shell via Macro", we just take the Launcher-2ef41c.py file that was generated and run it.

On the VM, we start the listener.

`python start.py --cli --port 1234`

Then the Launcher-2ef41c.py file, generated in the prior test, is run on our endpoint.

`cd /Users/red/EvilOSX/data/builds/`

`python Launcher-2ef41c.py`

The process is killed by Enterprise EDR Solution 2.

Hashes:

4ff7656819f82e08dc49782b3ed3315d25c3dd86752768f0ff4c64e9f5fb8397  Launcher-2ef41c.py
 
