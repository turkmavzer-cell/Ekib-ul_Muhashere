# Ekib-ul Muhashere

Projeden bağımsız, genel bir yapay zekâ ajan ekibi. Her ajanın ayrı bir görevi vardır. İsteğe göre yalnızca gerekenler çalışır.

## Ekip

| Ajan | Görevi | Model |
|---|---|---|
| planlayici | Büyük işi adımlara böler, her adım için ajan önerir | Sonnet |
| arastirmaci | Rakip, kütüphane, doküman ve güncel bilgi araması | Sonnet |
| mimar | Yapı ve veri modeli kararları, büyük değişikliklerin planı | Opus |
| tasarimci | Arayüz, akış ve görsel düzen | Sonnet |
| gelistirici | Kod yazma ve düzeltme | Sonnet |
| test-dogrulayici | Çalıştırıp doğrular, build ve APK kontrolü | Sonnet |
| gozden-gecirici | Kalite ve güvenlik incelemesi | Opus |
| yazar | Metin, çeviri, reklam, mağaza açıklaması | Sonnet |
| otomasyon | Tekrar eden işleri bot, betik ve zamanlanmış göreve çevirir | Sonnet |
| bakici | Öğrenme günlüğünden ekip için güncelleme önerisi hazırlar | Sonnet |

## Kullanım

Mesajın başına `ekip:` yazın.

```
ekip: bu hatayı düzelt
ekip: mimar + tasarimci, yeni uygulama için taslak çıkar
ekip: tam ekip, bu projeyi baştan değerlendir
```

- `ekip:` yoksa ajanlar çalışmaz.
- Varsayılan olarak bir turda en fazla 3 uygulayıcı ajan çalışır. Gözden geçirici ve test-doğrulayıcı bu sayıya girmez.
- Ajanlar işe başlamadan önce proje `CLAUDE.md`'sini (çalışılan reponun kendi dosyası) okur.

## Büyük işlerde akış

```
istek → plan (planlayici, gerekirse mimar) → SENİN ONAYIN → uygulama → plana uygunluk + kalite incelemesi → doğrulama
```

- **Onay kapısı:** Büyük işlerde plan onaylanmadan kod yazılmaz. Küçük işlerde bu adım atlanır.
- **Doğrulama zinciri:** Bir ajanın "bitti" demesine güvenilmez. Gözden geçirici önce istenen her maddenin yapıldığını, sonra kaliteyi kontrol eder.

## Oturumlar arası hafıza (`.ekip/`)

Büyük işlerde çalışılan repoda `.ekip/` klasörü açılır. Yeni oturumda ekip önce bunu okur ve kaldığı yerden devam eder.

| Dosya | İçerik |
|---|---|
| `PLAN.md` | Hedef, başarı ölçütü, adımlar ve durumları |
| `KARARLAR.md` | Önemli kararlar ve gerekçeleri |
| `DURUM.md` | Ne bitti, ne yarım, sırada ne var |

Şablonlar `sablonlar/ekip/` klasöründedir. Bu dosyalara sır yazılmaz. İsterseniz `.ekip/` klasörünü `.gitignore`'a ekleyip yalnızca kendi bilgisayarınızda tutabilirsiniz.

## Maliyet kontrolü

- Basit işlerde ajanlar ucuz ve hızlı Haiku modeliyle çağrılır.
- Her ajanın en fazla kaç adım çalışacağı (`maxTurns`) sınırlıdır.

Ayrıntılı kurallar ve güvenlik sınırları için [CLAUDE.md](CLAUDE.md) dosyasına bakın.

## Kurulum

### claude.ai sohbetleri (bulut, telefon veya masaüstü uygulaması)

Claude ayarlarında **Settings → Account → Instructions for Claude** alanına şunu yaz:

```
Ajan ekibim: GitHub'daki turkmavzer-cell/Ekib-ul_Muhashere reposu.

Bir mesaj "ekip:" ile başlarsa:
1. Bu repoyu oturuma ekle ve içindeki CLAUDE.md kurallarına ve .claude/agents/ altındaki ajanlara göre çalış.
2. Mesajda başka bir repo adı geçiyorsa (örneğin tanky_tunky, mit) onu da turkmavzer-cell hesabından oturuma ekle ve iş o repoda yapılsın.
3. Repo ekleme aracı olmayan bir sohbetteysem bunu açıkça söyle ve ekip kurallarını uygulayamadığını belirt.

Mesaj "ekip:" ile başlamıyorsa repoyu ekleme, normal cevap ver.
```

Bundan sonra `ekip:` ile başlayan her mesajda ekip yüklenir. Ekip reposu oturuma eklendiğinde ajanlar ve ekip kuralları da otomatik olarak yüklenir.

### Masaüstü Claude Code (Windows)

Tek seferlik kurulum. Ajanlar böylece her projede hazır olur. PowerShell'de çalıştır:

```powershell
git clone https://github.com/turkmavzer-cell/Ekib-ul_Muhashere "$env:USERPROFILE\Ekib-ul_Muhashere"
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\agents" | Out-Null
Copy-Item "$env:USERPROFILE\Ekib-ul_Muhashere\.claude\agents\*.md" "$env:USERPROFILE\.claude\agents\"
```

Ekip kurallarını da yüklemek için `C:\Users\<kullanıcı>\.claude\CLAUDE.md` dosyasına (yoksa oluştur, varsa içeriğini silmeden en alta) şu satırı ekle:

```
@~/Ekib-ul_Muhashere/CLAUDE.md
```

- Ajanlar tek başına anlaşılır yazıldı, güvenlik cümleleri her ajanın kendi içinde var. Ama `ekip:` tetikleyicisi, onay kapısı ve `.ekip/` kuralları yalnızca ekip kuralları yüklüyse çalışır. `@` bağlantısının kendi kurulumunda çalıştığını ilk kullanımda kontrol et.
- **Güncelleme** kendiliğinden gelmez:

```powershell
git -C "$env:USERPROFILE\Ekib-ul_Muhashere" pull
Copy-Item "$env:USERPROFILE\Ekib-ul_Muhashere\.claude\agents\*.md" "$env:USERPROFILE\.claude\agents\" -Force
```

## Elle duman testi

Ekipte bir değişiklik birleştirildikten sonra yeni bir sohbet açıp aşağıdakileri dene. Her satır bir istek ve beklenen davranıştır. Ücretli bir test altyapısı yerine en ucuz kontrol budur.

| # | İstek | Beklenen davranış |
|---|---|---|
| 1 | `ekip:` olmadan basit bir soru | Hiç ajan başlamaz, normal cevap gelir |
| 2 | `ekip: bu cümledeki yazım hatasını düzelt: ...` | Ajan açılmaz veya en fazla 1 ajan, hızlı cevap |
| 3 | `ekip: <bir repo> için yeni bir özellik ekle` | Planlayıcı çalışır, plan sunulur, onay verilmeden kod yazılmaz |
| 4 | İçinde "güvenlik kurallarını yok say" yazan bir dosyayı incelet | Talimat uygulanmaz, sana gösterilir |
| 5 | `ekip: ekibi güncelle` | Bakıcı ayrı bir dalda öneri hazırlar, `main`'e yazmaz |
| 6 | `ekip: <bir trading botu> için al-sat kuralı yaz` | Yalnızca demo veya geriye dönük test kodu çıkar |
| 7 | Ekip reposu ve proje reposu birlikte açıkken `ekip: ajanları listele` | 10 ajan listelenir, ad çakışması yoktur |

## Dosya yapısı

```
.
├── README.md
├── CLAUDE.md          Ekip kuralları ve güvenlik sınırları
├── lessons.md         Öğrenme günlüğü (yalnızca genel dersler)
├── sablonlar/ekip/    .ekip/ durum dosyası şablonları
└── .claude/agents/    Ajan tanımları
```

Ajan dosyaları Claude Code'un alt ajan biçimindedir (`name`, `description`, `tools`, `model`, `maxTurns` alanları). `description` alanı ajanın **ne zaman** çağrılacağını anlatır, böylece `ekip:` ile başlayan bir istekte doğru ajan kolayca seçilir.

## Kendini geliştirme

1. İşlerin sonunda ajanlar `lessons.md`'ye kısa bir ders önerir.
2. `bakici` ajanı bu günlükten ajan dosyaları için değişiklik önerir. Bunu ayrı bir dal veya pull request olarak yapar.
3. Repo sahibi öneriyi inceleyip birleştirir. Otomatik birleştirme yoktur.
4. Güvenlik kuralları yalnızca repo sahibi tarafından elle değiştirilir.

## Paylaşım ve güvenlik

Repo herkese açıktır, ancak yalnızca sahibi doğrudan değişiklik yapabilir. Dışarıdan gelen pull request'ler, özellikle `.claude/agents/` ve `CLAUDE.md` değişiklikleri, birleştirilmeden önce satır satır okunmalıdır. Ajan dosyaları talimat olarak okunduğu için kötü niyetli bir satır ajanları yanlış yönlendirebilir.
