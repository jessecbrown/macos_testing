**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: No

Added the below entries to the etc/hosts file in an attempt to disrupt communication between the sensor and domain. One should be able to easily find this information after some googling but, if in doubt, you can also find these domains by reaching out to the vendor or observing domains the EDR processes are reaching out to.

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/11d09f7d-bab5-4044-81c8-15063db616e2)

From the picture above, the first two URLs are for Enterprise EDR Solution 1 and the next three are for Enterprise EDR Solution 2.

Following this, malicious activity was performed and telemetry was not sent for either EDR until the entries were removed.
