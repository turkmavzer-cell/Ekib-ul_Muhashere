# Ekib-ul Muhashere

Projeden bağımsız, genel bir yapay zekâ ajan ekibi. Her ajanın ayrı bir görevi vardır. İsteğe göre yalnızca gerekenler çalışır.

## Ekip

| Ajan | Görevi | Model |
|---|---|---|
| planlayici | İsteği analiz eder, ajanları seçer, işi böler | Sonnet |
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
- Varsayılan olarak bir istekte en fazla 3 ajan çalışır.
- Ajanlar işe başlamadan önce çalışılan reponun `CLAUDE.md` dosyasını okur.

Ayrıntılı kurallar ve güvenlik sınırları için [CLAUDE.md](CLAUDE.md) dosyasına bakın.

## Dosya yapısı

```
.
├── README.md
├── CLAUDE.md          Ekip kuralları ve güvenlik sınırları
├── lessons.md         Öğrenme günlüğü (yalnızca genel dersler)
└── .claude/agents/    Ajan tanımları
```

Ajan dosyaları Claude Code'un alt ajan biçimindedir (`name`, `description`, `tools`, `model` alanları).

## Kendini geliştirme

1. İşlerin sonunda ajanlar `lessons.md`'ye kısa bir ders önerir.
2. `bakici` ajanı bu günlükten ajan dosyaları için değişiklik önerir. Bunu ayrı bir dal veya pull request olarak yapar.
3. Repo sahibi öneriyi inceleyip birleştirir. Otomatik birleştirme yoktur.
4. Güvenlik kuralları yalnızca repo sahibi tarafından elle değiştirilir.

## Paylaşım ve güvenlik

Repo herkese açıktır, ancak yalnızca sahibi doğrudan değişiklik yapabilir. Dışarıdan gelen pull request'ler, özellikle `.claude/agents/` ve `CLAUDE.md` değişiklikleri, birleştirilmeden önce satır satır okunmalıdır. Ajan dosyaları talimat olarak okunduğu için kötü niyetli bir satır ajanları yanlış yönlendirebilir.
