# Öğrenme Günlüğü

Ajanların işlerden çıkardığı **genel dersler** burada toplanır. Bakıcı ajanı bunlardan güncelleme önerisi hazırlar.

Kurallar:
- Repo herkese açıktır. Müşteri veya kişi adı, şirket adı, anahtar, token, kişisel bilgi yazılmaz.
- Emin değilsen yazma.
- Ders yalnızca kullanıcının onayıyla eklenir. Ayrıntılı akış `CLAUDE.md` "Öğrenme günlüğü" bölümündedir.

Biçim:

```
## YYYY-AA-GG · ajan · konu
- Ders: ne öğrenildi
- Neden: neden önemli, ne yanlış gitti
- Öneri: hangi ajan dosyası nasıl değişebilir (isteğe bağlı)
- Kaynak: iş deneyimi / web
- Durum: yeni / izlemede / işlendi (dal adı)
```

---

<!-- Kayıtlar bu çizginin altına eklenir. -->

## 2026-10-18 · gozden-gecirici · bitti işareti ve özel onay
- Ders: Bir adımın bitti işareti yalnızca bağımsız doğrulayıcının kararına bağlanmalı. Genel bir onay ("planı uygula"), ayrıca onay isteyen adımların (güvenlik metni, yasak listesi) yerine geçmemeli.
- Neden: Koordinatör kendi değişikliklerini "onaylandı sayıldı" diyerek bitti işaretledi ve doğrudan ana dala gönderdi. Hata ancak sonraki bağımsız incelemede yakalandı.
- Öneri: CLAUDE.md "Doğrulama zinciri" ve "Güncelleme" bölümleri.
- Kaynak: iş deneyimi
- Durum: işlendi (duzeltme/guven-sirasi)

## 2026-10-18 · koordinatör · YAML başlığını gerçekten ayrıştırarak doğrula
- Ders: Ajan dosyalarının başlığını alan adlarına bakarak değil, bir YAML ayrıştırıcısıyla doğrula. Açıklama metninde `: ` geçiyorsa değeri tırnak içine al.
- Neden: Açıklamalar yeniden yazılırken tırnaksız bir `kullan: ...` ifadesi başlığı geçersiz yaptı ve planlayıcı yüklenmeyebilir hale geldi. Alan adı kontrolü bunu yakalamadı.
- Öneri: Ajan dosyası değişen her işte `yaml.safe_load` ile kontrol.
- Kaynak: iş deneyimi
- Durum: işlendi (iyilestirme/v3, A0)

## 2026-10-18 · gozden-gecirici · kural değişince bütün kopyaları tara
- Ders: Bir kural yeni bir sorumluluk ya da yasak eklediğinde, aynı konuyu anlatan bütün ajan dosyaları ve README aynı değişiklikte taranmalı.
- Neden: CLAUDE.md güncellenip ajan dosyaları ve README eski halinde kaldığı için birden fazla çelişki çıktı (onay satırı biçimi, Haiku kuralı, bakıcının push yetkisi).
- Öneri: Kural değişikliğinden sonra `grep` ile aynı terimi geçen tüm dosyaları kontrol et.
- Kaynak: iş deneyimi
- Durum: işlendi (duzeltme/guven-sirasi, 1. düzeltme turu)

## 2026-10-18 · gozden-gecirici · kurallara içerikle atıf yap
- Ders: Ajan dosyaları kurallara numarayla ("güvenlik kuralı 4") değil, kuralın kendisini yazarak atıf yapmalı.
- Neden: Kural dosyası yüklenmediği bir ortamda numaralı atıf boşa düşer ya da başka bir kurala işaret eder.
- Kaynak: iş deneyimi
- Durum: işlendi (iyilestirme/v3, A1)

## 2026-10-18 · gozden-gecirici · kapalı listede dışarıda kalanları yaz
- Ders: Bir kuralı "örneğin" yerine kapalı bir listeye çevirirken, dışarıda kalan meşru durumların (olumsuz karar, soru dönüşü) hangi yola gittiği ayrıca yazılmalı.
- Neden: "Karar satırı yoksa hata" kuralı, doğru çalışan ama olumsuz karar veren bir doğrulayıcıyı hata yoluna düşürüyordu.
- Kaynak: iş deneyimi
- Durum: izlemede (Plan C adayı, Orta-1)

## 2026-10-18 · planlayici · davranışı anlatan metin
- Ders: Mağaza açıklaması veya sürüm notu, uygulama paralel ilerlerken taslak olarak hazırlanabilir, ama yalnızca test edilmiş davranışa göre kesinleştirilmeli.
- Neden: Aksi halde yapılmamış bir özellik vaat edilir.
- Kaynak: iş deneyimi (koordinasyon testi)
- Durum: işlendi (duzeltme/guven-sirasi, B3)

## 2026-10-18 · mimar · sert sınır sunucu tarafında
- Ders: Birden fazla ortamda çalışan bir ajan ekibinde sert sınır önce ortamdan bağımsız katmana konmalı (sunucu tarafı dal koruması). Prompt kuralları ve istemci tarafı engeller bunun üstüne eklenir.
- Neden: İstemci katmanının (hook, izin ayarı) her ortamda var olduğu garanti değil. Dal koruması kurulmadan önce koordinatör ana dala doğrudan yazabiliyordu.
- Kaynak: iş deneyimi
- Durum: işlendi (G1, main kural seti)

## 2026-10-18 · koordinatör · aynı incelemeyi tekrarlama
- Ders: Bir inceleme veya araştırma istenince önce son incelemeden bu yana bir şey değişip değişmediğine bak. Değişmediyse aynı ajanı yeniden açma, son sonucu ve açık kararları hatırlat.
- Neden: Aynı dosyaları tekrar incelemek aynı bulgular için iki kez limit harcar.
- Öneri: CLAUDE.md "Kayıtlar ve tekrarı önleme" bölümü.
- Kaynak: iş deneyimi
- Durum: işlendi (bu kayıt değişikliği)

## 2026-10-18 · arastirmaci · belge kısıtlarını ikinci okumayla doğrula
- Ders: Uzun resmi belge sayfalarında "yok sayılan alanlar", "desteklenmez" gibi kısıt iddialarını ikinci bir okumayla doğrula. Akademik kıyaslama sonuçlarını kendi ölçeğine doğrudan taşıma, kapsam farkını belirt.
- Neden: Özet okumada kısıtlar atlanabiliyor veya yanlış genellenebiliyor.
- Kaynak: web
- Durum: izlemede (tek kayıt, web kaynaklı; tek başına değişiklik gerekçesi değil)

