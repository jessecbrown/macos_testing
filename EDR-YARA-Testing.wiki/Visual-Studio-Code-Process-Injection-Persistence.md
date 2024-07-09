**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: No

We can add a level persistence into the prior exercise "Visual Studio Code Process Injection".

A new file is created to replace “inject.py” named “persistentinject.py”, given [here](https://github.com/lawrence737/EDR-YARA-Testing/blob/main/persistentinject.py), which simply checks whenever the Visual Studio Code app is running. If it is, then kill it, and launch our own with the inspect flag and put it in the background. We run this and it is not detected.

`python persistentinject.py`

Hashes:

bb8e608b0a70084d4373db617496e836ac37bef08938ef7ec9aec5bcbdff4eaf  persistentinject.py

