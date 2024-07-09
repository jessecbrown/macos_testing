The following section outlines the defined EDR policy settings for this testing.

Firstly, when we are testing on an endpoint with various EDR’s, having them all actively block can cause issues. Our current EDR, which we are deprecating, is put into passive mode, whereby all policy enforcement is disabled. Enterprise EDR Solution 1 and Enterprise EDR Solution 2 are both blocking, but various exclusions are added to ensure no issues occur with both EDRs blocking. I recommend speaking with your EDR provider to ensure the proper exclusions are in place such that one EDR does not block the other. Throughout testing, you may also want to add more exclusions if the EDR/YARA solution starts identifying false positives or if performance issues manifest. Just be mindful that the more exclusions you have, the higher chance a piece of malware hides under that path. So try to limit broad file path exclusions wherever possible.

Secondly, in onboarding an endpoint to an EDR, there are often configurations one can make to have the EDR more or less stringent. We looked to use settings recommended by the vendor for Mac OS such that false positives would not be very high. We will also be recording the number of false positives and factoring that into our evaluation because, realistically, if we were to implement one of these solutions, we would use a setting which does not generate many false positives. Your tolerance for false positive rates may vary, these configurations are detailed below.

## **Enterprise EDR Solution 1**

For Enterprise EDR Solution 1, we enable any setting centered around detection and enable protection for malicious threats which have a high confidence of malicious activity. This should log everything we are looking for. This EDR also has an option to upload files related from incidents but Mac OS is not supported, so this is disabled. In the detections below, note that “suspicious” is a lower confidence than “malicious” and we can opt not to block them.

## **Enterprise EDR Solution 2**

For Enterprise EDR Solution 2, we use the MacOS recommended settings for Prevention and Detection policies. These policies will generally detect anything low confidence or higher of malicious activity, but prevent medium confidence or higher. We have enabled a setting which uploads unknown executables because it should reduce false positives and increase true positives. When unknown executable uploads are enabled, the sensor uploads files that match these criteria:
They are unique in the Enterprise EDR Solution 2 cloud (based on the file’s hash) and thus have not been uploaded previously 
Are 32MB or smaller in size to conserve bandwidth
They do not belong to an exclusion that’s been applied to the host

## **Enterprise YARA Solution**

In terms of policy, the only things to really consider here are exclusions, filetypes being uploaded, and what YARA rules we will be using. On exclusions, we enter in some paths which may cause performance issues if the file shipper were to upload all files. These paths were identified during testing, primarily by measuring build time on dev machines when they have the agent vs when they do not have the agent. We saw a significant performance impact and had to add a file path exclusion. For filetypes, we are using the default filetypes in the tool but, in section 2.7, we will test uploading of different filetypes. These default filetypes are listed [here](https://github.com/lawrence737/EDR-YARA-Testing/blob/main/YARA_Solution_filetypes_for_analysis). Lastly for YARA rules, this solution provides a large volume of rules of varying noise. Some of these are detection-grade, some are not very useful, and some are useful particularly in threat hunting situations. Here, we enable detection grade rules. We also create a few rules focused on Sliver and upload some rules from some OSINT which we deem would not cause much noise. This is also mentioned in section 2.8. One could easily find plenty of reputable YARA sources online such as Crowdstrike, Florian Roth, Reversing Labs, etc. Regardless of what source is chosen, some tuning will be required as we adjust the YARA rules to fit our environment (i.e. reduce false positives and benign alerts).

Note that, in addition to the YARA rules, this solution has an ML model which it uses to analyze files and determine whether files are malicious. This ML model is trained off many known good and bad files. This will be used as an additional detection layer on top of the YARA rules we have enabled.

