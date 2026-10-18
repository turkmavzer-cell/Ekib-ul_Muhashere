# Durum

> Her oturumun sonunda güncellenir. Yeni oturumda ekip ilk olarak bu dosyayı okur.
> Sır, şifre veya token yazmayın.

## Son güncelleme
- Tarih: 2026-10-18
- Aktif plan: `PLAN.md` (Plan B, sürüm 1, onaylandı)
- İş dalı: `duzeltme/guven-sirasi`
- Önceki plan: `arsiv/2026-10-18-plan-A.md` (kapandı)

## Bitenler
- Plan A kapandı. G1 (`main` koruması) kuruldu ve test edildi.
- Güven sırası revizyonu repo sahibinin açık onayıyla hazırlandı.
- Plan B, adım B1-B8, iş dalında uygulandı. Koordinatörün kendi kontrolü: 10 ajan geçerli YAML, araç/model/adım sınırları değişmedi, güvenlik bölümü B commit'lerinde değişmedi, plandaki 30 madde dosyalarda var.

## Yarım kalanlar
- B9: bağımsız inceleme. 1. tur "düzeltme gerekli" dedi (4 yüksek, 6 orta bulgu). 1. düzeltme turu yapıldı, 2. inceleme bekleniyor. Döngü sınırı 2 tur.
- Bakıcının korunan bölümüne dokunan farklar (B8 ve 1. düzeltme turu: README korumaları, yeni ajana araç kısıtı) repo sahibine ayrıca gösterilip onaylanacak.
- İş dalının pull request ile `main`'e birleştirilmesi (repo sahibi).

## Sıradaki adım
1. Kullanıcı `ekip: gozden-gecirici, duzeltme/guven-sirasi dalını incele` gibi bir mesaj yazar.
2. Gözden geçirici iki aşamalı inceler, en fazla 2 düzeltme turu.
3. Repo sahibi pull request'i birleştirir.
4. Yeni bir sohbette README'deki 10 maddelik elle duman testi denenir.

## Açık sorular (kullanıcıya)
1. Bağımsız gözden geçiricinin dersi `lessons.md`'ye eklensin mi: "Bir adımın bitti işareti yalnızca bağımsız doğrulayıcının kararına bağlanmalı; genel onay, özel onay isteyen adımların yerine geçmemeli."

## Bilinen sorunlar
- `maxTurns` ve Haiku kuralının bulut sohbetinde uygulandığı test edilmedi.
- Ekip reposu ve proje reposu birlikte açıkken ajanların hangi repodan yüklendiği henüz denenmedi (duman testi 7 ve 10).
- Eski dallar (`ekip-v2`, `prompt-iyilestirme`, `iyilestirme/v3`) GitHub'da duruyor, hepsi `main`'de. Silinmeleri repo sahibine kalmış.
