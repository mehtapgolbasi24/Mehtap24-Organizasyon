# Mehtap Organizasyon — Web Sitesi Kurulum Rehberi

Bu depo, mehtap24organizasyon.com için hazırlanmış tam kapsamlı web sitesini içerir.

## İçindekiler
- `index.html` — ana sayfa
- `content.json` — düzenlenebilir metin/görsel içerikleri
- `admin/` — içerik yönetim paneli (Decap CMS)
- `robots.txt`, `sitemap.xml` — arama motoru optimizasyonu
- `404.html` — özel hata sayfası
- `favicon.svg` — site ikonu
- `netlify.toml` — sunucu/güvenlik ayarları

---

## 1) GitHub'a Yükleme

```bash
git init
git add .
git commit -m "İlk yükleme"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADIN/mehtap-organizasyon.git
git push -u origin main
```

## 2) Netlify'a Bağlama

1. [app.netlify.com](https://app.netlify.com) → **Add new site → Import an existing project**
2. GitHub hesabını bağla, `mehtap-organizasyon` reposunu seç
3. Build ayarlarını değiştirme (bu site statik, build komutu gerekmez), **Deploy** de
4. Birkaç saniyede geçici bir `xxx.netlify.app` linki alırsın

## 3) Domain Satın Alma — mehtap24organizasyon.com

Önerilen sağlayıcılar:
- **Natro** (natro.com) — Türkiye'de yaygın, TL ile ödeme
- **isimtescil.com** — Türkiye merkezli
- **Namecheap** (namecheap.com) — uluslararası, genelde ucuz

Adımlar:
1. Sağlayıcıya git, arama kutusuna `mehtap24organizasyon.com` yaz
2. Müsaitse sepete ekle, ödemeyi tamamla (yıllık ~150–400₺ arası değişir)
3. Domain paneline (sağlayıcının "DNS Yönetimi" veya "Domain Management" ekranı) giriş yap — bir sonraki adımda buraya kayıt ekleyeceğiz

## 4) Domaini Netlify'a Bağlama

1. Netlify'da sitene git → **Domain settings → Add a domain** → `mehtap24organizasyon.com` yaz
2. Netlify sana iki seçenek sunar:
   - **Netlify DNS kullan** (kolay yol): Netlify'ın verdiği 4 nameserver'ı, domain sağlayıcındaki "Nameserver" ayarlarına yapıştır. Yayılması 1-24 saat sürebilir.
   - **Kendi DNS'ini kullan**: Sağlayıcının DNS panelinde bir `A` kaydı (Netlify'ın IP'sine) ve `www` için bir `CNAME` kaydı (`xxx.netlify.app`'e) eklersin. Netlify ekranında tam değerleri gösterir.
3. Bağlandıktan sonra Netlify otomatik ve ücretsiz **SSL sertifikası** (https) kurar — genelde birkaç dakika sürer

## 5) İçerik Yönetim Paneli (Decap CMS) Kurulumu

1. Netlify panelinde **Identity** sekmesine git → **Enable Identity**
2. **Identity → Settings → Registration** → "Invite only" seç (herkes kayıt olamasın)
3. **Identity → Settings → Services → Git Gateway** → **Enable Git Gateway**
4. **Identity** sekmesinden kendi e-postanı **Invite user** ile davet et
5. Gelen davet e-postasındaki linke tıkla, şifreni belirle
6. `mehtap24organizasyon.com/admin` adresine git, giriş yap
7. Artık hizmetleri, süreç adımlarını, galeri fotoğraflarını, iletişim bilgilerini buradan değiştirebilirsin — her kaydetme otomatik olarak siteyi günceller

## 6) Form Mesajlarını Görüntüleme

Netlify panelinde site → **Forms** sekmesi → "teklif" formu altında gelen tüm mesajlar otomatik listelenir. İsteğe bağlı olarak **Forms → Settings → Form notifications** üzerinden her yeni mesaj için e-posta bildirimi kurabilirsin.

## 7) Google'da Görünürlük

1. [Google Search Console](https://search.google.com/search-console) → domainini ekle
2. Sağlanan doğrulama kaydını DNS'ine ekle (sağlayıcı panelinden)
3. `sitemap.xml` dosyasının linkini ("https://mehtap24organizasyon.com/sitemap.xml") Search Console'a gönder
4. Google'ın indexlemesi birkaç gün sürebilir

---

## Yardım Gerekirse

Herhangi bir adımda takılırsan (DNS kaydı, Netlify hatası, CMS girişi vs.) ilgili ekran görüntüsünü paylaşman yeterli, birlikte çözeriz.
