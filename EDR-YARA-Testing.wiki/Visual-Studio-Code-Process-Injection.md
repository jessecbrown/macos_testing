**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: No

The goal here is to inject javascript shellcode into the Visual Studio Code app, which connects back to our Command and Control server, and allows us to run our Command and Control traffic within the Visual Studio Code trusted process.

We begin by installing Visual Studio Code, this can be found in our Managed Software Center. Then we create a command and control server on our host over port 80. This is done via “c2.py”. Then “inject.py” is used to inject a shell into the Visual Studio Code process. Whereby the shellcode variable contains the code which will initiate a shell within the process. The code for “[c2.py](https://github.com/lawrence737/EDR-YARA-Testing/blob/main/c2.py)” and “[inject.py](https://github.com/lawrence737/EDR-YARA-Testing/blob/main/inject.py)” are linked.

First, we start the Command and Control server by running “c2.py”.

`python c2.py`

Then, in another terminal window, we run visual Studio Code with the inspect element. 

`/Applications/Visual\ Studio\ Code.app/Contents/MacOS/Electron --inspect`


In Chrome, we navigate to the url: “chrome://inspect/#devices”. Then, we click the link for “Open dedicated DevTools for Node” to get the console below.

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/173853cb-4286-455a-a2ea-ff17e2b1760c)


Lastly, in yet another terminal window we run “inject.py”.

`python inject.py`

We will now see the following in the DevTools console.

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/68f3214b-2937-4554-8424-083650142669)

This shows the shell is active, and we can run commands from the Command and Control within the trusted process. As shown below.

![image](https://github.com/lawrence737/EDR-YARA-Testing/assets/82233556/5ba414d5-8295-4171-bc27-41c28cd90632)

This was not blocked or detected.

Hashes:

556ec387860d8dfc9417d4624482f0485e624d3fa738191efee9f3b00eaacfeb  c2.py

c90e63f99aa09fc9e89edaf1e5b129bd0b06eb99cc1773ba7e68dfd89a274727  inject.py

Note that c2.py is not necessarily a malicious hash.