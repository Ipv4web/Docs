# CURL
```
curl --Proxy pr.ipv4web:8090 --Proxy-User {USERNAME}:{PASSWORD} "https://ipinfo.io"
```

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
```

# PHP
```
<?php
$username = 'USERNAME';
$country  = 'US';
$password = 'PASSWORD';

$user_agent = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.83 Safari/537.36';

$port = 8090;

$session = mt_rand();
$username .= "-cc-".$country ;
$username .= "-sessid-".$session;

$super_proxy = 'pr.ipv4web.com';

$curl = curl_init('https://ipinfo.io/');

curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);

curl_setopt($curl, CURLOPT_PROXY, "http://$super_proxy:$port");

curl_setopt($curl, CURLOPT_PROXYUSERPWD, "$username:$password");

$result = curl_exec($curl);

curl_close($curl);

if ($result)

echo $result;
?>
```

# Nodejs
```
#!/usr/bin/env node

var request = require('request-promise');

var username = 'USERNAME';

var password = 'PASSWORD';

var port = 8090;

var session_id = (1000000 * Math.random())|0;

var super_proxy = 'http://'+username+':'+password+'@pr.ipv4web.com:8090';

var options = {

url: 'https://ipinfo.io',

proxy: super_proxy

headers: {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.83 Safari/537.36'}

};

request(options)

.then(function(data){ console.log(data); },

function(err){ console.error(err); });
