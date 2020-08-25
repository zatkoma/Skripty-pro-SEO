## cURL with header
```
curl -X HEAD -i http://www.google.com
```

## cURL as Googlebot
```
curl -X HEAD -i -A "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)" http://www.google.com
```

## cURL follow redirects as Googlebot
```
curl -A "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"  -sLD - -o /dev/null -w "%{url_effective}" http://www.google.com
```
