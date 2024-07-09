**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: Yes (Blocked)
* Enterprise YARA Solution: Yes


Ran unmodified [apfell](https://github.com/MythicAgents/apfell) in endpoint, blocked by Enterprise EDR Solution 2.


`osascript index.js`

Hashes:
89a06666173b1acac37c00e99e7e287bfb029622c1f22206ecef3d8571097fb1 index.js

***

**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: Yes (It detected the copying of the osascript binary and blocked)
* Enterprise YARA Solution: Yes

Moved osascript binary (and removed signature because of  AMFI), reran the same apfell script. 

`cp /usr/bin/osascript /var/tmp/launchd
codesign --remove-signature /var/tmp/launchd
/var/tmp/launchd index.js`

Hashes:
89a06666173b1acac37c00e99e7e287bfb029622c1f22206ecef3d8571097fb1 index.js

***

**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: Yes

Removed all the comments from the apfell script, reran with an osascript binary downloaded from Slack (an attacker could have sent a zip with apfell and the osascript binary).

`sed -i '' -e 's/^\/\/.*$//g' index.js`


`./osa index_nocom.js`

Hashes:
b4c8c8cad1916c3f999dfd042c2893f7851e5a713022a5e2f52b28f3ce59248d  index_nocom.js
37f1efdc985e99cffaee4546ced87a5c0bf6560d41799119f27432dbce6139ac  osa