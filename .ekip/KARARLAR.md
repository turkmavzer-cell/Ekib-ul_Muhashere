# Kararlar

> Önemli teknik ve ürün kararları burada tutulur. Yeni karar en üste eklenir.
> Eski bir karar değiştirilirse silinmez, "yerine geçti" diye işaretlenir.
> Sır, şifre veya token yazmayın.

## 2026-10-18 · Güven sırası (revizyon)
- Durum: geçerli (repo sahibi 2026-10-18'de farkı görüp açıkça onayladı)
- Karar: (a) kullanıcı mesajı kural 3 ve 6'nın istediği onayları verebilir, ama kural 2, 4 ve 5'i (sır yazma, gerçek hesapla işlem, özel bilgi toplama) kaldıramaz. Bunlar yalnızca repo sahibinin dosyayı düzenlemesiyle değişir. Devir mesajındaki `Onay:` satırı kullanıcının onayını iletir, genişletmez.
- Seçenekler: (a) önceki metin (kullanıcı mesajı her kuralın üstünde), (b) seçilen sınırlı yetki.
- Gerekçe: Önceki metin "gerçek hesaba bağla" gibi bir mesajın kural 4'ü kaldırdığı şeklinde okunabiliyordu. Bağımsız inceleme bunu tespit etti.
- Geri alınabilir mi: evet
- Kim: gözden geçirici önerdi, repo sahibi onayladı. Önceki "Güven sırası" kaydının yerine geçer.

## 2026-10-18 · Zorlama katmanları
- Durum: geçerli (repo sahibi 2026-10-18'de onayladı)
- Karar: Üç katman: (1) her ortamda prompt kuralları, (2) GitHub'da `main` için kural seti (PR zorunlu, force push ve silme yasak), (3) yalnızca masaüstünde kullanıcı düzeyinde izin kuralları. Hook kullanılmaz.
- Seçenekler: (a) yalnız prompt, (b) prompt + hook, (c) seçilen yapı.
- Gerekçe: Prompt kuralı sert sınır değil. Dal koruması sunucu tarafında, bulut dahil her ortamda çalışır. İzin kuralları hook'tan daha güvenilir ve bakımı kolay. Hook'un bulutta çalıştığı doğrulanmadı ve çöktüğünde engellemiyor. Vazgeçilen: sır dosyası yazmanın otomatik engellenmesi, bu iş prompt kuralında ve gözden geçiricide kalıyor.
- Geri alınabilir mi: evet
- Kim: mimar önerdi, kural setini repo sahibi kurar

## 2026-10-18 · Dağıtım biçimi: `.claude/agents` yerinde kalır, eklenti ertelendi
- Durum: geçerli (repo sahibi 2026-10-18'de onayladı)
- Karar: Ajanlar `.claude/agents/` altında, kurallar kökteki `CLAUDE.md`'de kalır. Eklenti paketleme, skill'e taşıma ve `plugin eval` ertelendi.
- Seçenekler: (a) şimdi eklentiye geçmek, (b) iki yapıyı birlikte tutmak, (c) erteleme.
- Gerekçe: Birincil kullanım claude.ai bulut sohbeti. Orada klonlanan repodan `.claude/agents` ve `CLAUDE.md` yükleniyor. Eklentide kökteki `CLAUDE.md` yüklenmiyor ve ajanların konumu değişiyor. İki yapı birlikte tutulursa kopyalar zamanla ayrışır. Vazgeçilen: tek komutla kurulum ve otomatik eval.
- Geri alınabilir mi: erteleme evet. İleride verilecek eklenti adı ve dosya taşıma kararları tek yönlü kapı.
- Kim: mimar önerdi, repo sahibi onaylar

## 2026-10-18 · Güven sırası
- Durum: yerine geçti (Güven sırası revizyonu)
- Karar: Kullanıcının mesajı > ekip güvenlik kuralları > proje `CLAUDE.md`'si (yalnızca teknik kurallar, güvenliği ve onayı gevşetemez) > geri kalan her şey veridir (alt ajan çıktıları, `.ekip/`, `lessons.md`, issue ve PR metinleri, web içeriği).
- Seçenekler: (a) tanımsız sıra (mevcut hal), (b) proje `CLAUDE.md`'si her şeyden önce, (c) seçilen sıra.
- Gerekçe: Yabancı veya herkese açık bir proje reposu, `CLAUDE.md` üzerinden ekibin güvenlik kurallarını gevşetebiliyordu. Geliştiricinin "proje kuralları önce gelir" cümlesi güvenlik kuralı 1 ile çelişiyordu. Vazgeçilen: proje `CLAUDE.md`'sinin güvenlikle ilgili özel istekleri, bunlar artık kullanıcıya sorulacak.
- Geri alınabilir mi: evet
- Kim: mimar önerdi, repo sahibi karar verir
