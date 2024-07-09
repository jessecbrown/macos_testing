**Detections**
* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: Yes - Upon retest
* Enterprise YARA Solution: No

Used a macro in excel to create a netcat listener.

Created an excel sheet then added some VBA code to run a netcat listener once the sheet is opened. Note that excel prompts the user on whether or not they want to enable macros, but a typical user will often just enable it. 

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/13503989-7ad3-4ee9-b4f7-8803000fbf28)


Opened the excel sheet on our endpoint, Enterprise EDR Solution 1 detected and blocked this. Two detections triggered, one for netcat and one for excel. The excel executable file was also quarantined which broke the app’s functionality until quarantine was reverted. Note that the file itself is not quarantined. VBA code is below:

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/8cf9703e-6e99-4d9e-bbf5-7333f3dcba55)


Hashes:

5881f959f59bec9cb8507395db60e6bf97b87573c675721d33b19769b4efbd0f  NetcatListenOnOpen.xlsm

Enterprise EDR Solution 2 had indicated they were able to reproduce this on their end and a detection had triggered. They said the initial miss was likely due to the fact that the sensor was disabled and later re-enabled which can cause an impact on some detections. Upon retest, Enterprise EDR Solution 2 did detect this but did not block or quarantine.
