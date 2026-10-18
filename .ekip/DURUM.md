# Durum

> Her oturumun sonunda güncellenir. Yeni oturumda ekip ilk olarak bu dosyayı okur.
> Sır, şifre veya token yazmayın.

## Son güncelleme
- Tarih: 2026-10-18
- Aktif plan: `PLAN.md` (ekip iyileştirme planı, A0-A5 ve G1)

## Bitenler
- Dış araştırma (araştırmacı): Anthropic ajan ve bağlam rehberleri, hook, eval, eklenti paketleme, skill ve prompt uzunluğu.
- İç inceleme (gözden geçirici): 2 kritik, 6 yüksek, 8 orta bulgu.
- İyileştirme planı (mimar): 6 aşama, 3 karar önerisi.

## Yarım kalanlar
- Plan repo sahibinin onayını bekliyor. Onaydan önce hiçbir aşama uygulanmayacak.

## Sıradaki adım
- Onay gelirse A0 (`planlayici.md` YAML düzeltmesi ve duman testi) ayrı bir dalda yapılır.
- Repo sahibi G1'i (GitHub kural seti) kendisi kurar.

## Açık sorular (kullanıcıya)
1. Güvenlik bölümü ve bakıcının yasak listesi değişiklikleri: ekip metni ayrı dalda hazırlasın ve sen birleştirerek onaylayasın mı, yoksa metni kendin mi yapıştırmak istersin?
2. Eklenti paketleme ertelensin mi? (Öneri: evet, masaüstü kullanımı düzenli hale gelince yeniden bakılır.)
3. `lessons.md` akışı: "oturum sonunda en fazla 1 ders, sen onaylarsan" yeterli mi, yoksa ders yalnızca sen "ders yaz" dediğinde mi önerilsin?

## Bilinen sorunlar
- `planlayici.md` frontmatter'ı geçersiz YAML (description içinde tırnaksız `: `). Planlayıcı ajanı yüklenmeyebilir. A0'da düzeltilecek.
