# Plan B: kalan bulguların kapatılması

> Bu dosya ekip tarafından güncellenir. Sır, şifre veya token yazmayın.
> Önceki plan: `.ekip/arsiv/2026-10-18-plan-A.md`

## Hedef
Ekibin birden fazla oturuma yayılan, iki repo birlikte açıkken yürüyen ve plan değişikliği içeren işlerde de tutarlı ve güvenli çalışması.

## Başarı ölçütü
- Bağımsız incelemenin 10 bulgusu ve koordinasyon testinin 12 notu ya kapatıldı ya da gerekçesiyle "yapılmayacak" işaretlendi.
- README duman testine 3 yeni madde eklendi (iki oturuma yayılan iş, onaydan sonra plan değişikliği, proje reposu açıkken ajan yüklenmesi) ve 10 madde bulut sohbetinde denendi.
- Değişiklikler tek bir dalda, aşama başına bir commit olarak hazırlandı, bağımsız gözden geçirici "onay" verdi, birleştirmeyi repo sahibi yaptı.

## Kısıtlar ve varsayımlar
- `main` korumalı. Her şey dal ve pull request ile gelir, birleştirmeyi yalnızca repo sahibi yapar.
- Güvenlik bölümünde değişiklik gerekirse fark ayrıca gösterilir ve ayrı onay alınır.
- Bir adım ancak bağımsız gözden geçiricinin karar satırından sonra `[x]` olur.
- Ajanların `tools`, `model` ve `maxTurns` alanları değişmez.

## Onay
- Durum: onaylandı
- Tarih: 2026-10-18
- Sürüm: 1
- Kapsam: B1-B9

## Adımlar

Durum işaretleri: `[ ]` bekliyor · `[~]` yapılıyor · `[x]` bitti · `[!]` sorunlu

B1-B8 `duzeltme/guven-sirasi` dalında uygulandı. Bağımsız inceleme: 1. tur "düzeltme gerekli" (10 bulgu), 1. düzeltme turundan sonra 2. tur "onay" (2026-10-18). B1-B8 bu karara dayanarak `[x]`. B9, repo sahibinin ayrı onayları ve birleştirmesi bekleniyor.

Not: B5'teki Bash kuralı 1. düzeltme turunda değişti. Güncel metin `test-dogrulayici.md` ve `gozden-gecirici.md` içinde: `npm ci` kullanılır, izin yoksa `cap sync` gibi komutlar çalıştırılmaz, bir dosya yine de değişirse geri alınmaz, raporlanır.

| # | Durum | Adım | Kapattığı bulgular | Dosyalar |
|---|---|---|---|---|
| B1 | [x] | **Ajanlar yüklenmezse yedek yol:** Ajan tipi oturumda yoksa kullanıcıya söylenir. Ajanın `.md` dosyası devir mesajına eklenir, `tools` kısıtı devir mesajında da yazılır ve okuma yetkili ajanın değişikliği `git status` ile kontrol edilir. Duman testine 3 yeni madde. | İnceleme 2 | `CLAUDE.md`, `README.md` |
| B2 | [x] | **Git akışı ve `.ekip/` kalıcılığı:** Kim commit/push eder (koordinatör, iş dalına), `.ekip/` oturum sonunda iş dalına commit ve push edilir ve dal adı kullanıcıya söylenir, yeni oturum iş dallarındaki `DURUM.md`'ye de bakar, APK derlemesini kim tetikler ve sonucu kim okur, `.gitignore` seçeneği yalnızca masaüstü için. | İnceleme 3, test 6 | `CLAUDE.md`, `README.md` |
| B3 | [x] | **Onay kapsamı:** `Onay:` satırı plan sürümü ve adım numarası içerir. Plan değişince veya iptal edilince eski onay geçersiz olur, iptal durumu şablona eklenir. Onay kapısı planlayıcı ve mimar çıktısından sonra tek kapıdır. Tasarımı değiştiren sorular mimardan önce sorulur. Tasarımcı ve yazara onay satırı kuralı eklenir. Davranışı anlatan metin, davranış doğrulanmadan kesinleşmez. | İnceleme 5, test 1, 5, 8, 11, plan A'daki A3 eksiği | `CLAUDE.md`, `sablonlar/ekip/PLAN.md`, `tasarimci.md`, `yazar.md` |
| B4 | [x] | **`.ekip/` karışması ve paralel işler:** Ekip reposunun `.ekip/` klasörü yalnızca istek ekibin kendisiyle ilgiliyse okunur. Çalışılan repoda başka bir işe ait aktif plan varsa üzerine yazılmaz, kullanıcıya sorulur, eski plan `.ekip/arsiv/` altına taşınır. | İnceleme 4 | `CLAUDE.md` |
| B5 | [x] | **Çelişkilerin giderilmesi:** Haiku yalnızca ajan açmak zaten gerekçeliyse seçilir, çağrıdaki model frontmatter'ın yerine geçer, mimar ve gözden geçirici Haiku ile çağrılmaz. Derleme ve bağımlılık klasörleri dışında izlenen dosyalar değiştirilmez, sonda `git status` rapora eklenir. "Tur" tanımı. Test-doğrulayıcı ve gözden geçirici sırası. | İnceleme 7, 8, test 2, 3 | `CLAUDE.md`, `test-dogrulayici.md`, `gozden-gecirici.md` |
| B6 | [x] | **Hata ve boş dönüş:** Ajanın çıktısında karar satırı yoksa, ajan hata verdiyse veya boş döndüyse adım `[!]` olur, iş küçültülüp bir kez tekrar denenir, yine olmazsa kullanıcıya söylenir. `[x]` yalnızca doğrulayıcının karar satırından sonra konur. | İnceleme 9, 1 | `CLAUDE.md` |
| B7 | [x] | **Açık repolar ve kapsam:** Repo görünürlüğü kontrol edilir; açık repoda `.ekip/`'e iş verisi, fiyat ve kapatılmamış güvenlik bulgusu yazılmaz. Proje reposu okunamıyorsa planlayıcı yol varsaymaz, repo keşfini ilk adım yapar. Seçim rehberine "yeni görsel veya ekran gerekiyorsa + tasarimci". Büyük iş ölçütü netleşir. Planlayıcı büyük işi `maxTurns`'e göre önceden bölebilir. | İnceleme 10, test 4, 9, 10, 12 | `CLAUDE.md`, `planlayici.md` |
| B8 | [x] | **Küçük notlar:** `tam ekip` sınırla ilişkisi ve yanlış yazılan ajan adı. Bakıcı, README'deki hesap ayarı talimatı ve duman testi bölümlerine dokunamaz. Bakıcı açıklamasındaki "zamanlanmış bakım" ifadesi `ekip:` kuralıyla uyumlu hale gelir. | İnceleme düşük notlar | `CLAUDE.md`, `bakici.md` |
| B9 | [~] | **Bağımsız inceleme ve birleştirme:** Gözden geçirici iki aşamalı inceler, en fazla 2 düzeltme turu. Sonra repo sahibi pull request'i birleştirir. Ardından bulut sohbetinde 10 maddelik duman testi. | Başarı ölçütü | – |

## Geri alınamayan adımlar
- Yok. Tüm adımlar dalda hazırlanır, birleştirmeden önce incelenir ve geri alınabilir.
- B6'daki `[x]` kuralı ve B8'deki bakıcı yasakları bakıcı dosyasının korunan bölümlerine dokunduğu için fark sahibe ayrıca gösterilir.

## Riskler
- Kural sayısı artıyor. `CLAUDE.md` her oturumda yüklendiği için şişerse kurallar gözden kaçabilir. Her adımda eklenen satır kadar tekrar eden satır çıkarılmaya çalışılacak.
- B1'in yedek yolu, bulutta ajanların gerçekten yüklenip yüklenmediğini çözmez, sadece yüklenmediğinde güvenli davranışı tarif eder. Asıl doğrulama duman testinde.
