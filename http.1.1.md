# Mini HTTP/1.1 Developer Docs

Bu hujjat HTTP/1.1 standartiga mos bo‘lib, quyidagilarni o‘z ichiga oladi:  

- HTTP Status Codes (1xx–5xx)  
- HTTP Request Methods  
- HTTP Headers (General, Request, Response, Entity)  

---

## 1. HTTP/1.1 Status Codes / Status Kodlar

### 1xx — Informational / Informatsion
| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 100 | Continue | Davom etish — Client keyingi so‘rovni yuborishi mumkin |
| 101 | Switching Protocols | Protokolni almashtirish — Server boshqa protokolga o‘tadi |

### 2xx — Successful / Muvaffaqiyatli
| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 200 | OK | OK — So‘rov muvaffaqiyatli bajarildi |
| 201 | Created | Yaratildi — Yangi resurs yaratildi |
| 202 | Accepted | Qabul qilindi — So‘rov qabul qilindi, lekin hali bajarilmadi |
| 203 | Non-Authoritative Information | Javob metadata boshqa serverdan |
| 204 | No Content | Body yo‘q, faqat headerlar |
| 205 | Reset Content | Client formni reset qilishi kerak |
| 206 | Partial Content | Fayl yoki ma’lumotning faqat bir qismi yuborildi |

### 3xx — Redirection / Yo‘naltirish
| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 300 | Multiple Choices | Resurs bir nechta variantda mavjud |
| 301 | Moved Permanently | Doimiy ko‘chirilgan URL |
| 302 | Found | Vaqtinchalik ko‘chirilgan URL |
| 303 | See Other | GET orqali boshqa URL’ga yo‘naltirish |
| 304 | Not Modified | Resurs o‘zgarmagan, cache uchun |
| 305 | Use Proxy | Resurs proxy orqali olinadi |
| 306 | (Unused) | Ishlatilmaydi |
| 307 | Temporary Redirect | Clientni boshqa URL’ga vaqtinchalik yo‘naltirish |

### 4xx — Client Error / Mijoz xatolari
| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 400 | Bad Request | Noto‘g‘ri so‘rov |
| 401 | Unauthorized | Autentifikatsiya talab qilinadi |
| 402 | Payment Required | To‘lov talab qilinadi |
| 403 | Forbidden | Resursga ruxsat yo‘q |
| 404 | Not Found | Resurs topilmadi |
| 405 | Method Not Allowed | Method ruxsat etilmagan |
| 406 | Not Acceptable | Qabul qilinmaydi |
| 407 | Proxy Authentication Required | Proxy autentifikatsiya talab qiladi |
| 408 | Request Timeout | So‘rov vaqtida yuborilmadi |
| 409 | Conflict | Resurs bilan ziddiyat mavjud |
| 410 | Gone | Resurs endi mavjud emas |
| 411 | Length Required | Content-Length talab qilinadi |
| 412 | Precondition Failed | Shart bajarilmadi |
| 413 | Request Entity Too Large | So‘rov body juda katta |
| 414 | Request-URI Too Long | URL juda uzun |
| 415 | Unsupported Media Type | Content-Type qo‘llab-quvvatlanmaydi |
| 416 | Requested Range Not Satisfiable | Byte range noto‘g‘ri |
| 417 | Expectation Failed | Expect header bajarilmadi |

### 5xx — Server Error / Server xatolari
| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 500 | Internal Server Error | Ichki server xatosi |
| 501 | Not Implemented | Server methodni qo‘llab-quvvatlamaydi |
| 502 | Bad Gateway | Gateway yoki proxy xatoligi |
| 503 | Service Unavailable | Server hozir ishlay olmaydi |
| 504 | Gateway Timeout | Gateway yoki proxy javob bermadi |
| 505 | HTTP Version Not Supported | HTTP versiyasi qo‘llab-quvvatlanmaydi |

---

## 2. HTTP Request Methods / Request Methodlari

| Method | Inglizcha Tavsif | O‘zbekcha Tavsif | Xususiyatlar |
|--------|-----------------|----------------|-------------|
| GET | Request a representation of the resource | Resursni olish | Idempotent, Safe |
| HEAD | Same as GET but without body | Body yo‘q, faqat headers | Resurs mavjudligini tekshirish |
| POST | Submit data to the resource | Ma’lumot yuborish | Idempotent emas, form/API submit |
| PUT | Replace the resource with request payload | Resursni yangilash | Idempotent, resurs to‘liq yangilanadi |
| DELETE | Remove the resource | Resursni o‘chirish | Idempotent |
| OPTIONS | Describe communication options | Resurs metodlarini ko‘rsatadi | CORS preflight uchun |
| TRACE | Echo the received request | Client yuborgan so‘rovni echo qiladi | Debug maqsadida |
| CONNECT | Establish a tunnel to the server | Tunnel yaratish (HTTPS proxy) | SSL/TLS tunnel |
| PATCH | Apply partial modifications | Resursni qisman yangilash | PUT ga o‘xshaydi, qisman update |

---

## 3. HTTP Headers / Headerlar

### 3.1 General Headers / Umumiy
| Header | Inglizcha Tavsif | O‘zbekcha Tavsif |
|--------|-----------------|----------------|
| Cache-Control | Directives for caching mechanisms | Cache mexanizmlari yo‘riqnomalari |
| Connection | Control options for current connection | Hozirgi connection’ni boshqarish |
| Date | Date and time the message was sent | Xabar yuborilgan sana/vaqt |
| Pragma | Implementation-specific directives | Maxsus yo‘riqnomalar (no-cache) |
| Trailer | Header fields in chunked message trailer | Chunked body trailer headerlari |
| Transfer-Encoding | Encoding applied to body | Body encoding turi (chunked) |
| Upgrade | Ask server to switch protocols | Protokolni almashtirish so‘rovi |
| Via | Intermediate protocols / proxies info | Proxy/gateway ma’lumotlari |
| Warning | General warning info | Umumiy ogohlantirishlar |

### 3.2 Request Headers / So‘rov
| Header | Inglizcha Tavsif | O‘zbekcha Tavsif |
|--------|-----------------|----------------|
| Accept | Media types client can accept | Client qabul qiladigan media (`text/html`, `json`) |
| Accept-Charset | Character sets client can accept | Client qabul qiladigan charset |
| Accept-Encoding | Content encodings client can accept | Client qabul qiladigan encoding (`gzip`) |
| Accept-Language | Preferred languages | Client afzal ko‘rgan til |
| Authorization | Authentication credentials | Autentifikatsiya ma’lumotlari |
| Expect | Expectations from server | Serverdan kutayotgan xatti-harakatlar |
| From | Email address of user | Foydalanuvchi email |
| Host | Host and port of request | Server va port |
| If-Match | Conditional request using ETag | ETag asosida shartli so‘rov |
| If-Modified-Since | Conditional GET | Oxirgi o‘zgartirish sanasiga shartli GET |
| If-None-Match | Conditional GET using ETag | ETag asosida shartli GET |
| If-Range | Range requests validation | Range request tekshiruvi |
| If-Unmodified-Since | Conditional if not modified | Oxirgi o‘zgartirishdan keyin o‘zgarmasa so‘rov |
| Max-Forwards | Limit number of hops | Proxy/gateway orqali maksimal yo‘naltirish |
| Proxy-Authorization | Authentication for proxy | Proxy uchun autentifikatsiya |
| Range | Request a specific range of bytes | Byte range so‘rov |
| Referer | Address of previous page | Oldingi sahifa manzili |
| TE | Transfer encodings client can accept | Qabul qilinadigan transfer encoding |
| User-Agent | Client software info | Client dasturi info |

### 3.3 Response Headers / Javob
| Header | Inglizcha Tavsif | O‘zbekcha Tavsif |
|--------|-----------------|----------------|
| Accept-Ranges | Supported range units | Qo‘llab-quvvatlanadigan byte range |
| Age | Age of resource in cache | Cache’dagi resurs yoshi |
| ETag | Entity tag | Resurs identifikatori |
| Location | Redirection target URL | Yo‘naltiriladigan URL |
| Proxy-Authenticate | Proxy authentication request | Proxy autentifikatsiya so‘rovi |
| Retry-After | Wait time before retry | Keyin qayta urinib ko‘rish vaqti |
| Server | Server info | Server dasturi va versiyasi |
| Vary | Response varies by request header | Javob headerga qarab o‘zgaradi |
| WWW-Authenticate | Authentication challenge | Autentifikatsiya chaqiruvi |

### 3.4 Entity Headers / Resurs / Body
| Header | Inglizcha Tavsif | O‘zbekcha Tavsif |
|--------|-----------------|----------------|
| Allow | Valid methods for resource | Resurs uchun ruxsat etilgan metodlar |
| Content-Encoding | Encoding applied to body | Body encoding turi (`gzip`) |
| Content-Language | Language of body | Body tili (`en`, `uz`) |
| Content-Length | Length of body in bytes | Body uzunligi (bayt) |
| Content-Location | Direct URL for entity | Resurs to‘g‘ridan-to‘g‘ri URL’i |
| Content-MD5 | MD5 checksum of entity | MD5 checksum body uchun |
| Content-Range | Range of bytes in response | Javobdagi byte range |
| Content-Type | MIME type of body | Body turi (`text/html`, `application/json`) |
| Expires | Expiration date/time | Resursning amal qilish muddati |
| Last-Modified | Last modification date | Oxirgi o‘zgartirish sanasi |




# HTTP (Request/Response) GET Method va Headers(Accept)

HTTP/1.1 da **Content-Type** va **Accept** headers orqali resurs formatini belgilash muhim. Quyida eng ko‘p ishlatiladigan formatlar va tavsiflar berilgan.

---

## 1. Video va Oqimli Media (Streaming)

| Fayl kengaytmasi | MIME turi (Content-Type) | Tavsif |
|-----------------|------------------------|--------|
| .m3u8           | application/vnd.apple.mpegurl | HLS (HTTP Live Streaming) pleylisti |
| .ts             | video/mp2t             | MPEG-2 Transport Stream segmenti |
| .mpd            | application/dash+xml   | MPEG-DASH manifest fayli |
| .mp4            | video/mp4              | Standart MP4 video |
| .webm           | video/webm             | Google WebM video formati |
| .m4s            | video/iso.segment      | DASH video fragmenti |

---

## 2. Matnli va Dasturlash formatlari

| MIME turi | Tavsif |
|-----------|--------|
| text/html | HTML hujjatlar (UTF-8 kodlash bilan) |
| application/json | JSON ma'lumotlar (API uchun standart) |
| application/xml | XML ma'lumotlar |
| text/javascript | JavaScript dastur kodlari |
| text/css | CSS stillari |
| text/plain | Oddiy matn (default matn turi) |
| text/markdown | Markdown formatidagi matnlar |

---

## 3. Tasvirlar va Grafika

| MIME turi | Tavsif |
|-----------|--------|
| image/jpeg | JPEG rasmlar |
| image/png | PNG rasmlar |
| image/webp | WebP (siqilgan veb-rasmlar) |
| image/avif | AVIF (yuqori sifatli siqilgan format) |
| image/svg+xml | SVG vektorli grafika |
| image/gif | GIF animatsiyalar |

---

## 4. Ilova va Binar ma'lumotlar

| MIME turi | Tavsif |
|-----------|--------|
| application/pdf | PDF hujjatlari |
| application/zip | ZIP arxivlari |
| application/octet-stream | Noma'lum binar ma'lumot (yuklab olish uchun) |
| multipart/form-data | Fayllarni forma orqali yuborishda ishlatiladi |
| application/x-www-form-urlencoded | Standart HTML forma ma'lumotlari |

---

## 5. HTTP Headers Vazifasi

| Header | Yo‘nalish | Tavsif | Misol |
|--------|----------|--------|-------|
| Accept | Client → Server | Mijoz serverdan qanday formatni qabul qilishi mumkinligini bildiradi | `Accept: application/json, text/javascript, */*; q=0.01` |
| Content-Type | Server → Client yoki Request tanasida | Yuborilayotgan ma'lumotning aniq formatini bildiradi | `Content-Type: application/vnd.apple.mpegurl` |

---

**Eslatma:**  

- GET requestlarda body yo‘q, shuning uchun `Content-Type` odatda kerak emas, lekin server javobida bo‘lishi mumkin.  
- `Accept` header mijozga serverga qaysi formatlar kerakligini bildiradi, masalan JSON API uchun `Accept: application/json`.  
- Media fayllar (video, audio, tasvirlar) uchun to‘g‘ri **MIME type** server va browser o‘rtasidagi to‘liq ishlashni ta’minlaydi.
