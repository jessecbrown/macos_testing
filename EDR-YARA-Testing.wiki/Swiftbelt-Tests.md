**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: Yes (Blocked)
* Enterprise YARA Solution: Yes

Cloned, compiled and ran [SwiftBelt](https://github.com/cedowens/SwiftBelt), a MacOs local enumeration tool.

`git clone https://github.com/cedowens/SwiftBelt`

`cd SwiftBelt`

`swift build`

`cd .build/debug/`

`./SwiftBelt -CheckFDA`

`./SwiftBelt -Clipboard`

`./SwiftBelt -ListUsers`