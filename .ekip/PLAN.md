# Plan

> Bu dosya ekip tarafından güncellenir. Sır, şifre veya token yazmayın.

## Hedef
Ekibin her ortamda (claude.ai bulut sohbeti ve masaüstü Claude Code) güvenilir, tutarlı ve gereksiz maliyetsiz çalışması.

## Başarı ölçütü
- 10 ajanın frontmatter'ı geçerli YAML ve hepsi yükleniyor.
- README'deki 6 maddelik elle duman testi bulut sohbetinde beklenen davranışı veriyor.
- `main` dalına doğrudan push yapılamıyor (GitHub kural seti).
- Dosyalar arasında çelişen kural kalmıyor (iç inceleme bulguları Y1-Y6, O1-O4, O6-O8 kapandı).

## Kısıtlar ve varsayımlar
- Birincil kullanım claude.ai bulut sohbeti. Hook ve eklentinin orada çalıştığı doğrulanmadı, bu yüzden önce her ortamda geçerli prompt düzeltmeleri yapılır.
- Ajanlar `.claude/agents/` altında, kurallar kökteki `CLAUDE.md`'de kalır.
- Her aşama ayrı dalda (`iyilestirme/a0-yaml` gibi) yapılır, birleştirmeyi repo sahibi yapar.
- `CLAUDE.md` güvenlik bölümü ve `bakici.md` yasak listesi yalnızca repo sahibinin onayıyla değişir.

## Onay
- Durum: bekliyor
- Tarih: 

## Adımlar

Durum işaretleri: `[ ]` bekliyor · `[~]` yapılıyor · `[x]` bitti · `[!]` sorunlu

| # | Durum | Adım | Ajan | Çıktı | Not |
|---|---|---|---|---|---|
| A0 | [ ] | `planlayici.md` YAML düzeltmesi, 10 dosyanın YAML taraması, README'ye elle duman testi | gelistirici | Geçerli frontmatter, 6 maddelik test listesi | Kritik, planlayıcı şu an yüklenmeyebilir |
| G1 | [ ] | GitHub'da `main` için kural seti: doğrudan push, force push, dal silme yasak, PR zorunlu | repo sahibi | GitHub ayarı | Kullanıcı yapar, ortamdan bağımsız sert sınır |
| A1 | [ ] | Güven sırası (güvenlik bölümü), numaralı güvenlik atıflarını tek cümlelik içerikle değiştirme (6 dosya), şablon atıflarına yedek alan listesi, "ekip kuralları / proje CLAUDE.md'si" adlandırması | gelistirici + gozden-gecirici | Güvenlik bölümü metni repo sahibinin onayına | Güvenlik bölümü değişiyor |
| A2 | [ ] | 3 ajan sınırı "uygulayıcı" için, doğrulama zinciri sınır dışı; gereksiz ajan çağrısını azaltma; hata düzeltmede para/veri varsa gözden geçirici; alt ajanın soru döndürmesi; `git status` ile yarım iş tespiti; çakışma ve 2 tur döngü sınırı; README kurulum bölümü | gelistirici + gozden-gecirici | `CLAUDE.md` (güvenlik dışı), `README.md` | Davranış değişir, duman testiyle bakılır |
| A3 | [ ] | Yazma yetkili ajanlara `.ekip/` yazmama kuralı; devir mesajında onay yoksa kod yazmama; tasarımcı ve yazarın yazma kapsamı; gözden geçirici ve test-doğrulayıcı için Bash yalnız okuma/derleme/test | gelistirici + gozden-gecirici | 7 ajan dosyası | |
| A4 | [ ] | "Günlük" bölümlerini tek kurala indirme; dersi kullanıcı onayıyla yazma; `lessons.md`'ye Durum ve Kaynak alanları; bakıcı yasak listesinin genişletilmesi | gelistirici + gozden-gecirici | `CLAUDE.md`, `lessons.md`, `bakici.md` | Bakıcı yasak listesi sahip onayıyla |
| A5 | [ ] | Yalnızca kesin tekrarların kaldırılması (README), gelistirici ve otomasyonda güvenlik satırlarını başa alma | gelistirici | `README.md`, 2 ajan dosyası | Öz kontrol listeleri ölçüm olmadan kısaltılmaz |

Ertelenenler: M1 masaüstü izin kuralları (masaüstü kullanımı başlayınca), E1 eklenti paketleme + skill + `plugin eval` (karar bekliyor).
Yapılmayacaklar: M2 hook'lar, mimarın araçlarını değiştirme, toplu satır kısaltma.

## Geri alınamayan adımlar
- Bu plandaki tüm adımlar geri alınabilir (ayrı dal, birleştirmeden önce inceleme).
- Tek yönlü kapılar (ajanları `agents/` altına taşıma, eklenti adı, kuralları skill'e taşıma) bu planın dışında, E1'e bırakıldı.

## Riskler
- Bulut oturumunda iki repo açıkken ajanların hangi repodan yüklendiği tam doğrulanmadı. Proje reposunda da `.claude/agents/` varsa ad çakışması olabilir. Duman testine eklenecek.
- A2'nin token kullanımına etkisi ancak duman testiyle gözlenebilir.
- GitHub kural setinin herkese açık repolarda ücretsiz olduğu doğrulanmadı.
