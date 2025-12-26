http-(Hypertext Transfer Protocol)
https://datatracker.ietf.org/doc/html/rfc2616
1. Introduction (RFC 2616, HTTP/1.1)
HTTP (Hypertext Transfer Protocol) — bu ilova darajasidagi tarmoq protokoli bo‘lib, ma’lumotni (masalan HTML sahifalar yoki API javoblari) client va server o‘rtasida uzatish uchun ishlatiladi. 
Uning asosiy xususiyatlari:

Stateless (holatsiz) — har bir so‘rov‑javob alohida o‘tkaziladi, oldingi so‘rovlar saqlanmaydi. 
IETF HTTP Working Group

Generic (umumiy) — faqat web sahifalar emas, balki JSON, fayllar yoki boshqa ma’lumotlar ham uzatilishi mumkin. 
IETF Datatracker

Ko‘p vazifali — HTTP nafaqat hypertext uchun, balki nom serverlari, ob’ektlar boshqaruvi kabi tizimlar uchun ham ishlatiladi. 
IETF Datatracker

HTTP/1.1 RFC 2616’da aniqlangan standard bo‘lib, u 1990‑yillardan beri World Wide Web uchun asosiy protokol hisoblanadi.

# HTTP/1.1 Status Kodlari (HTTP Status Codes)

HTTP status kodlar 5 ta asosiy guruhga bo‘linadi:

1. **1xx — Informatsion / Informational**  
2. **2xx — Muvaffaqiyatli / Successful**  
3. **3xx — Yo‘naltirish / Redirection**  
4. **4xx — Mijoz xatolari / Client Error**  
5. **5xx — Server xatolari / Server Error**

---

## 1xx — Informatsion / Informational

| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 100 | Continue | Davom etish — Client keyingi so‘rovni yuborishi mumkin |
| 101 | Switching Protocols | Protokolni almashtirish — Server boshqa protokolga o‘tadi |

---

## 2xx — Muvaffaqiyatli / Successful

| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 200 | OK | OK — So‘rov muvaffaqiyatli bajarildi |
| 201 | Created | Yaratildi — Yangi resurs yaratildi |
| 202 | Accepted | Qabul qilindi — So‘rov qabul qilindi, lekin hali bajarilmadi |
| 203 | Non-Authoritative Information | Not-auth info — Javob metadata boshqa serverdan |
| 204 | No Content | Hech narsa yo‘q — Body yo‘q, faqat headerlar |
| 205 | Reset Content | Kontentni reset qilish — Client formni reset qilishi kerak |
| 206 | Partial Content | Qisman kontent — Fayl yoki ma’lumotning faqat bir qismi yuborildi |

---

## 3xx — Yo‘naltirish / Redirection

| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 300 | Multiple Choices | Bir nechta variant — Resurs bir nechta formatda mavjud |
| 301 | Moved Permanently | Doimiy ko‘chirilgan — URL doimiy o‘zgardi |
| 302 | Found | Topildi — Vaqtinchalik ko‘chirilgan URL |
| 303 | See Other | Boshqa ko‘rish — GET orqali boshqa URL’ga yo‘naltirish |
| 304 | Not Modified | O‘zgarmagan — Resurs o‘zgarmagan, cache uchun |
| 305 | Use Proxy | Proxy orqali foydalanish — Resurs proxy orqali olinadi |
| 306 | (Unused) | Ishlatilmaydi |
| 307 | Temporary Redirect | Vaqtinchalik yo‘naltirish — Clientni boshqa URL’ga yo‘naltirish |

---

## 4xx — Mijoz xatolari / Client Error

| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 400 | Bad Request | Noto‘g‘ri so‘rov — So‘rov yaroqsiz yoki noto‘g‘ri formatda |
| 401 | Unauthorized | Avtorizatsiya talab qilinadi — Kirish kerak |
| 402 | Payment Required | To‘lov talab qilinadi — Kam ishlatiladi |
| 403 | Forbidden | Ta’qiqlangan — Resursga ruxsat yo‘q |
| 404 | Not Found | Topilmadi — Resurs serverda mavjud emas |
| 405 | Method Not Allowed | Method ruxsat etilmagan — Masalan POST faqat GET ruxsatli |
| 406 | Not Acceptable | Qabul qilinmaydi — Resurs client qabul qiladigan formatda emas |
| 407 | Proxy Authentication Required | Proxy autentifikatsiya talab qiladi |
| 408 | Request Timeout | Vaqt tugadi — Client so‘rovni yuborishga kechikdi |
| 409 | Conflict | Ziddiyat — Resurs bilan qarama-qarshi amal |
| 410 | Gone | Yo‘q bo‘lib ketgan — Resurs endi mavjud emas |
| 411 | Length Required | Uzunlik talab qilinadi — Content-Length yo‘q |
| 412 | Precondition Failed | Precondition bajarilmadi — If-Match, If-None-Match xatolik |
| 413 | Request Entity Too Large | So‘rov juda katta — Body hajmi server tomonidan ruxsat etilganidan katta |
| 414 | Request-URI Too Long | URL juda uzun |
| 415 | Unsupported Media Type | Media turi qo‘llab-quvvatlanmaydi — Content-Type noto‘g‘ri |
| 416 | Requested Range Not Satisfiable | So‘ralgan range bajarib bo‘lmaydi |
| 417 | Expectation Failed | Expect header bajarilmadi |

---

## 5xx — Server xatolari / Server Error

| Kod | Inglizcha Tavsif | O‘zbekcha Tavsif |
|-----|-----------------|----------------|
| 500 | Internal Server Error | Ichki server xatosi — Server noto‘g‘ri ishladi |
| 501 | Not Implemented | Amal bajarilmagan — Server methodni qo‘llab-quvvatlamaydi |
| 502 | Bad Gateway | Yomon gateway — Gateway yoki proxy xatoligi |
| 503 | Service Unavailable | Xizmat mavjud emas — Server hozir ishlay olmaydi |
| 504 | Gateway Timeout | Gateway yoki proxy javob bermadi |
| 505 | HTTP Version Not Supported | HTTP versiyasi qo‘llab-quvvatlanmaydi |

