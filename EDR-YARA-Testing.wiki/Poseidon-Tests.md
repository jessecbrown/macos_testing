**Detections**
* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: Yes (Low confidence detection)
* Enterprise YARA Solution: Yes

Run off the shelf [Poseidon](https://github.com/MythicAgents/poseidon). 

`./pos`

Hashes:

203cbf572454c9b2eca0bea39d3960461602771a8d1e778aa05e1c2e88d6ede4 pos

***

**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: Yes (Blocked)
* Enterprise YARA Solution: No

Recreated Poseidon using an option to obfuscate payload

Enterprise EDR Solution 2 quarantined the file and blocked this activity.

`./pos_mod`

Hashes:

5b5e9ca8f44c7345382495c40a3e9fee7d1810dd2c0c341ef742e0f81d5443b1 pos_mod

***

**Detections**
* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: No

Compressed poseidon with [UPX](https://upx.github.io/). Enterprise EDR Solution 1 detects it now, but not Enterprise EDR Solution 2.

`./pos_mod_upx`

Hashes:

be49560aaaaa74333357c7abb05f89cdcaeb4f661d7467b991353bf4d7cd373e  pos_mod_upx