# Durum

> Her oturumun sonunda güncellenir. Yeni oturumda ekip ilk olarak bu dosyayı okur.
> Sır, şifre veya token yazmayın.

## Son güncelleme
- Tarih: 2026-10-18
- Aktif plan: `PLAN.md` (Plan B: kalan bulguların kapatılması, onay bekliyor)
- Önceki plan: `arsiv/2026-10-18-plan-A.md` (kapandı)

## Bitenler
- Plan A uygulandı. Bağımsız inceleme süreç sapmasını tespit etti. Güvenlik bölümü ve bakıcı yasak listesi farkı repo sahibine gösterildi ve onaylandı.
- G1: `main` için kural seti kuruldu. Doğrudan push'un reddedildiği test edildi.
- Koordinasyon testi (planlayıcı, kuru çalıştırma) geçti: iş doğru bölündü, sınırlara uyuldu, devir mesajları eksiksiz.
- Güven sırası revizyonu `duzeltme/guven-sirasi` dalında hazırlandı.

## Yarım kalanlar
- `duzeltme/guven-sirasi` dalı için pull request açılıp birleştirilmesi (repo sahibi).
- Plan B onay bekliyor.

## Sıradaki adım
- Repo sahibi pull request'i birleştirir ve Plan B'yi onaylar veya değiştirir.
- Onaydan sonra B1-B8 yeni bir dalda uygulanır, B9'da bağımsız inceleme yapılır.

## Açık sorular (kullanıcıya)
1. Plan B'yi bu haliyle onaylıyor musun, çıkarmak veya eklemek istediğin bir adım var mı?
2. Bağımsız gözden geçiricinin dersi `lessons.md`'ye eklensin mi: "Bir adımın bitti işareti yalnızca bağımsız doğrulayıcının kararına bağlanmalı; genel onay, özel onay isteyen adımların yerine geçmemeli."

## Bilinen sorunlar
- `maxTurns` ve Haiku kuralının bulut sohbetinde uygulandığı test edilmedi.
- Ekip reposu ve proje reposu birlikte açıkken ajanların hangi repodan yüklendiği henüz denenmedi.
- Eski dallar (`ekip-v2`, `prompt-iyilestirme`, `iyilestirme/v3`) GitHub'da duruyor, hepsi `main`'de. Silinmeleri repo sahibine kalmış.
