# OWASP Juice Shop — Stored XSS Analizi

## Ortam
- Hedef: OWASP Juice Shop (localhost:3000, Docker ile kuruldu)
- Amaç: Ürün yorumu alanındaki Stored XSS zafiyetini göstermek

## Bulgu
Yorum alanına girdi doğrulanmadan kaydediliyor ve her ziyaretçide çalışıyor.

**Payload:**
<script>alert(document.cookie)</script>


## Etki
- Ziyaretçinin oturum çerezi (cookie) çalınabilir → hesap ele geçirme (session hijacking)
- Phishing içeriği sayfaya enjekte edilebilir

## Önerilen Çözüm
- Çıkış karakterlerine göre encode (output encoding)
- Content Security Policy (CSP) başlığı
- Girdi doğrulama (whitelist)
