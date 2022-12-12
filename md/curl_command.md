# **Curl Command**
<pre>
curl <url> 
   -v เอาไว้แสดง detail การ connection
   -X <GET, POST> 
   -H <header>
   -F <body>
   --proxy <[protocol://][user:password@]proxyhost[:port]>
</pre>

**ยิงหา line notify proxy bi-proxy-dev**

<pre>
curl -v https://notify-api.line.me/api/notify -X POST -H "Authorization: Bearer 4AGkJ9hkli78oV7I2XSXiJW2hxIPDxMLYakxc8WR1bq" -F "message=line test bi-proxy" --proxy "http://proxy:8080"
</pre>


**Escape character**
<pre>
@ - %40
# - %23
& - %26
</pre>


**ตัวอย่าง curl proxy**
<pre>
curl -lv -x "http://proxy:8080" https://google.com
</pre>

<pre>
curl -lv -x "http://proxy:8080" https://google.com
</pre>


**คำสั่งเอาไว้ดูว่า default proxy เป็นอะไร**
<pre>
env | grep -i proxy
</pre>