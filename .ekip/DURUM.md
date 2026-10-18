# Durum

> Her oturumun sonunda güncellenir. Yeni oturumda ekip ilk olarak bu dosyayı okur.
> Sır, şifre veya token yazmayın.

## Son güncelleme
- Tarih: 2026-10-18
- Aktif plan: `PLAN.md` (Plan B, sürüm 1, onaylandı)
- İş dalı: `duzeltme/guven-sirasi`
- Önceki plan: `arsiv/2026-10-18-plan-A.md` (kapandı)

## Bitenler
- Kayıt düzeni: `DEGISIKLIKLER.md` (geçmiş, araştırılanlar, yapılmayacaklar), `lessons.md`'ye 9 ders ve CLAUDE.md'ye "Kayıtlar ve tekrarı önleme" kuralı eklendi. Kullanıcı 2026-10-18'de "tüm değişiklik ve öğrenilenler kayıt altına alınsın" dedi.
- Plan A kapandı. G1 (`main` koruması) kuruldu ve test edildi.
- Güven sırası revizyonu repo sahibinin açık onayıyla hazırlandı.
- Plan B, adım B1-B8, iş dalında uygulandı. Koordinatörün kendi kontrolü: 10 ajan geçerli YAML, araç/model/adım sınırları değişmedi, güvenlik bölümü B commit'lerinde değişmedi, plandaki 30 madde dosyalarda var.

## Yarım kalanlar
- B9: bağımsız inceleme tamamlandı (2. tur: onay). Repo sahibi 2026-10-18'de güvenlik bölümü farkını ve bakıcının korunan bölüm farklarını ayrı ayrı görüp onayladı. Kalan tek adım: repo sahibinin pull request'i birleştirmesi.

## Sıradaki adım
- Birleştirmeden sonra yeni bir sohbette README'deki 10 maddelik elle duman testi denenir.
- Sonraki iş (Plan C adayı, henüz onaylanmadı), 2. inceleme turunun orta bulguları:
  - Orta-1: Olumsuz karar ("düzeltme gerekli", "kaldı") düzeltme döngüsüne gitmeli, "Kullanıcıya sorular" dönüşü hata sayılmamalı.
  - Orta-2: Yedek yolda başlangıç kaydı eksik (`status --porcelain --ignored`, diff özeti, `for-each-ref`).
  - Orta-3: Workflow kontrolü, `.github/workflows` değişen her push'tan önce tekrarlanmalı. Açık PR dallarındaki `.ekip/` de aranmalı.
  - Düşük: `bakici.md` dal adı ve yetki metni `CLAUDE.md` ile eşitlenmeli. Bu değişiklik bakıcının korunan bölümüne dokunduğu için ayrı onay gerekir.

## Açık sorular (kullanıcıya)
- Yok.

## Bilinen sorunlar
- `maxTurns` ve Haiku kuralının bulut sohbetinde uygulandığı test edilmedi.
- Ekip reposu ve proje reposu birlikte açıkken ajanların hangi repodan yüklendiği henüz denenmedi (duman testi 7 ve 10).
- Eski dallar (`ekip-v2`, `prompt-iyilestirme`, `iyilestirme/v3`) GitHub'da duruyor, hepsi `main`'de. Silinmeleri repo sahibine kalmış.
