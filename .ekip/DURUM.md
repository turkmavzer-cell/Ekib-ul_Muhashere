# Durum

> Her oturumun sonunda güncellenir. Yeni oturumda ekip ilk olarak bu dosyayı okur.
> Sır, şifre veya token yazmayın.

## Son güncelleme
- Tarih: 2026-10-18
- Aktif plan: `PLAN.md` (ekip iyileştirme planı)

## Bitenler
- A0: Ajan başlıkları geçerli YAML, README'ye elle duman testi.
- A1: Güven sırası, kendi başına anlaşılan güvenlik atıfları, şablon yedek alanları.
- A2: Uygulayıcı ajan sınırı, "Ajan açmadan önce" ve "Alt ajanlarla çalışma" kuralları, README kurulum bölümü.
- A3: Yazma yetkili ajanların sınırları.
- A4 + A5: Ders akışı (kullanıcı onayıyla), bakıcı yasak listesi, güvenlik bölümleri dosya başında.

## Yarım kalanlar
- G1: GitHub'da `main` için kural seti. Repo sahibi kuracak.

## Sıradaki adım
- Repo sahibi G1'i kurar.
- Yeni bir sohbette README'deki 7 maddelik elle duman testi yapılır. Sonuç bu dosyaya yazılır.

## Açık sorular (kullanıcıya)
- Yok. Varsayılanlar: güvenlik bölümü değişikliği "planı uygula" talimatıyla onaylandı sayıldı; ders akışı "oturum sonunda en fazla 1 ders, kullanıcı onaylarsa" olarak uygulandı.

## Bilinen sorunlar
- `maxTurns` ve Haiku kuralının bulut sohbetinde uygulandığı test edilmedi.
- Ekip reposu ve proje reposu birlikte açıkken ajanların hangi repodan yüklendiği duman testinin 7. maddesiyle kontrol edilecek.
