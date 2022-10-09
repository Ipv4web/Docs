# python
```python
import urllib.request
import random
username = 'USERNAME' # 1001-name
password = 'PASSWORD'
country = 'DE'
entry = ('http://%s-country-%s:%s@pr.ipv4web.com:8090' %
    (username, country, password))
query = urllib.request.ProxyHandler({
    'http': entry,
    'https': entry,
})
execute = urllib.request.build_opener(query)
print(execute.open('https://ipinfo.io').read())
