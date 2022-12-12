# Redis Command 
**ใช้คำสั่ง redis-cli เพื่อ connect กับ redis server ก่อน ค่อยใช้คำสั่งอื่นๆ**
`redis-cli`

**Search / List Key**
**หาทั้งหมด**
`keys *`

**หา keys จาก username**
`keys [username]`

**ลบ key**
`del [key]`

**ดูว่ามี key มั้ย**
`exists [key]`

**Clear cache ทั้งหมด**
`flushdb`

**ดู key ที่เข้ามาแบบ Live** 
`monitor`

# Docker Run Redis เพื่อต่อ redis แบบ local
`docker run -d --name cxpaymentapi-redis -p 6379:6379 -e maxmemory="1024mb" -e maxmemory-policy="allkeys-lru" redis:6.0.4`

