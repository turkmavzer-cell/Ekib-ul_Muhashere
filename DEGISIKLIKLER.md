# Değişiklik Geçmişi

> Ekipte yapılan her değişiklik burada kayıtlıdır. Amaç, aynı geliştirmeyi tekrar yapmamak ve reddedilmiş bir fikri yeniden önermemek.
> Ekibi değiştirmeyi önermeden önce bu dosyayı, `.ekip/KARARLAR.md` dosyasını ve `lessons.md` dosyasını oku.
> Yeni sürüm en üste eklenir. Her birleştirilen değişiklik buraya bir satırla girer.

## Sürümler

### v4 · 2026-10-18 · `duzeltme/guven-sirasi` (birleştirme bekliyor)
- **Güven sırası revizyonu:** Kullanıcı mesajı kural 3 ve 6'nın onaylarını verebilir, kural 2, 4 ve 5'i (sır yazma, gerçek hesapla işlem, özel bilgi toplama) kaldıramaz. Devir mesajındaki `Onay:` satırı onayı iletir, genişletmez.
- **Plan B (B1-B8):**
  - Ajan bulunamazsa yedek yol. Bu yol yazmayı engellemez, sonradan tespit eder.
  - Git akışı: `ekip/` dalları, commit ve push'u koordinatör yapar, birleştirmeyi kullanıcı yapar. `.ekip/` dosyaları oturum sonunda dala gönderilir.
  - Onay kapsamı: tarih, plan sürümü ve adımlar. Plan değişince veya iptal edilince eski onay geçersiz. Tek onay kapısı. Davranışı anlatan metin doğrulanmadan kesinleşmez.
  - `.ekip/` karışmasını önleme ve eski planı arşivleme.
  - Çelişkiler giderildi: Haiku, Bash ve derleme, "tur" tanımı, test ve inceleme sırası.
  - Hata veya boş dönüşte `[!]`. `[x]` yalnızca doğrulayıcının kararından sonra.
  - Açık repolarda `.ekip/` yasak listesi, büyük iş ölçütü, planlayıcının repo keşfi ve `maxTurns`'e göre bölme.
  - `tam ekip`, tanınmayan ajan adı, bakıcının README korumaları.
- **1. düzeltme turu:** Bağımsız incelemenin 10 bulgusu kapatıldı. 2. tur kararı: onay.
- **Kayıt düzeni:** Bu dosya, `lessons.md`'deki ilk dersler ve "Kayıtlar ve tekrarı önleme" kuralı.

### v3 · 2026-10-18 · `iyilestirme/v3` (birleşti)
Plan A: dış araştırma, iç inceleme ve mimar planı.
- A0: Ajan başlıkları geçerli YAML hale getirildi, README'ye elle duman testi eklendi.
- A1: Güven sırası (ilk sürüm), numaralı güvenlik atıfları kuralın kendisiyle değiştirildi, şablon yedek alanları eklendi.
- A2: 3 uygulayıcı ajan sınırı, "Ajan açmadan önce" ve "Alt ajanlarla çalışma" kuralları, README kurulum bölümü.
- A3: Yazma yetkili ajanların sınırları.
- A4 + A5: Dersler kullanıcı onayıyla, bakıcı yasak listesi, güvenlik bölümleri dosya başına alındı.
- G1: GitHub'da `main` için kural seti (PR zorunlu, force push ve silme yasak). Repo sahibi kurdu.
- Not: Bu sürüm doğrudan `main`'e yazıldı ve bağımsız inceleme olmadan bitti işaretlendi. Bu hata `lessons.md`'ye kaydedildi.

### v2 · 2026-10-18 · `ekip-v2` (birleşti)
- `.ekip/` durum dosyaları (`PLAN.md`, `KARARLAR.md`, `DURUM.md`) ve şablonları.
- Büyük işte onay kapısı.
- Gözden geçirici: önce plana uygunluk, sonra kalite.
- Test doğrulayıcı: önceki ajanın "bitti" iddiasına güvenmez.
- Açıklamalar "ne zaman kullan" biçimine çevrildi, `maxTurns` ve Haiku kuralı eklendi.

### v1.1 · 2026-10-18 · `prompt-iyilestirme` (birleşti)
- 10 ajana düşünme yöntemi, devir, teslim öncesi öz kontrol listesi ve kaçınılacaklar eklendi.

### v1 · 2026-10-18 · ilk kurulum
- 10 ajan: planlayici, arastirmaci, mimar, tasarimci, gelistirici, test-dogrulayici, gozden-gecirici, yazar, otomasyon, bakici.
- `CLAUDE.md`: `ekip:` tetikleyicisi, seçim rehberi, güvenlik kuralları. `lessons.md`, `README.md`.

## Araştırılan kaynaklar (tekrar araştırmadan önce bak)

| Tarih | Kaynak | Ne alındı |
|---|---|---|
| 2026-10-18 | obra/superpowers | Fikir netleştirme, görev başına yeni ajan, iki aşamalı inceleme, "bitti" demeden doğrulama |
| 2026-10-18 | gsd-build/get-shit-done | Dosyalarda iş durumu (bizde `.ekip/`), paralel dalgalar, görev başına commit (ertelendi) |
| 2026-10-18 | wshobson/agents | Model katmanlama, `plugin eval` (ertelendi) |
| 2026-10-18 | VoltAgent/awesome-claude-code-subagents | Ajan türüne göre en az araç yetkisi |
| 2026-10-18 | BMAD-METHOD | Hikâye dosyaları. Eleştiriler: token maliyeti, hata yayılımı (bizim hafif yapı ve doğrulama zinciri buna cevap) |
| 2026-10-18 | rube-de/cc-skills (cdt), niksacdev/engineering-team-agents | Rol dağılımı ve sade dosya biçimi |
| 2026-10-18 | Anthropic: Building effective agents, multi-agent research system, context engineering, prompting best practices | Az ajan, çaba ölçeği, devir mesajı alanları, büyük harfli vurgudan kaçınma |
| 2026-10-18 | Claude Code belgeleri: sub-agents, hooks, plugins, plugin-evals, skills | Frontmatter alanları, hook sınırları, eklentide kök `CLAUDE.md`'nin yüklenmemesi |

## Yapılmayacaklar ve ertelenenler (yeniden önermeden önce gerekçeye bak)

| Fikir | Durum | Gerekçe | Ayrıntı |
|---|---|---|---|
| Hook'larla güvenlik zorlaması | Yapılmayacak | İzin kuralları ve dal koruması aynı işi daha güvenilir yapıyor. Hook çökünce engellemiyor ve bulutta çalıştığı doğrulanmadı | `.ekip/KARARLAR.md` · Zorlama katmanları |
| Eklenti (plugin) paketleme, kuralları skill'e taşıma | Ertelendi | Bulut kullanımında kök `CLAUDE.md` ve `.claude/agents` yükleniyor, eklentide kök `CLAUDE.md` yüklenmiyor. Ad ve taşıma tek yönlü kapı | `.ekip/KARARLAR.md` · Dağıtım biçimi |
| `claude plugin eval` ile otomatik ajan testi | Ertelendi | Eklenti gerektiriyor ve ücretli. Şimdilik elle duman testi yeterli | Plan A |
| Masaüstü izin kuralları (`permissions.deny`) | Ertelendi | Masaüstü düzenli kullanılınca | Plan A, M1 |
| Mimarın araçlarını değiştirme | Yapılmayacak | WebSearch hızlı kontrol için yeterli, derin okuma araştırmacının işi | Plan A |
| Ölçümsüz toplu prompt kısaltma | Yapılmayacak | Kural kaybı riski. Kısaltma yalnızca kesin tekrarlarda | Plan A |
| Görev başına commit, önce test yazma | Ertelendi | Ekip gerçek işlerde kullanıldıktan sonra değerlendirilecek | v2 araştırması |
| Claude-mem, Task Observer, Headroom, OmniRoute kurulumu | Yapılmayacak | Kullanıcı vazgeçti. claude-mem kuruldu ve kaldırıldı | İlk oturum |

## Açık işler

`.ekip/DURUM.md` dosyasındaki "Sıradaki adım" bölümüne bak (Plan C adayı: 2. inceleme turunun orta bulguları).
