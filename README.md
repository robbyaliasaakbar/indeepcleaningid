# InDeep Cleaning ID — Website

Website resmi **InDeep CleaningID** — jasa cleaning service profesional (cuci sofa, kasur, karpet, gordyn, interior mobil, baby stuff).

🌐 **Live:** [https://indeepcleaningid.site](https://indeepcleaningid.site)

---

## Tentang Repository Ini

Repo ini berisi **website utama** InDeep CleaningID — halaman statis (HTML + CSS + vanilla JS) yang di-serve langsung dari Apache.

App booking dan landing page conversion **tidak** ada di sini. Keduanya punya repo sendiri karena stack-nya beda:

| Projek | Repo | URL Live |
|--------|------|----------|
| Website utama | repo ini | `indeepcleaningid.site` |
| App booking | repo terpisah | `booking.indeepcleaningid.site` |
| Landing page ads | repo terpisah | `landingpage.indeepcleaningid.site` |

### Struktur Repository

```
indeepcleaningid.site/
│
├── index.html                  ← Halaman utama
├── about.html                  ← Tentang kami
├── contact.html                ← Kontak
├── gallery.html                ← Galeri
├── pricing-estimator.html      ← Estimasi harga
├── coverage.html               ← Area layanan
├── 404.html                    ← Halaman tidak ditemukan
│
├── assets/                     ← Aset statis
│   ├── css/                    ← Stylesheet
│   ├── js/                     ← JavaScript
│   ├── img/                    ← Gambar
│   └── data/                   ← Data (JSON)
│
├── services/                   ← Halaman layanan
│   ├── cuci-sofa.html
│   ├── cuci-kasur.html
│   ├── cuci-karpet-gordyn.html
│   ├── interior-mobil.html
│   └── baby-stuff.html
│
├── .htaccess                   ← URL rewriting & redirect rules
├── robots.txt                  ← Robot crawler rules
├── sitemap.xml                 ← XML sitemap
├── humans.txt                  ← Info tim & situs
└── favicon.svg                 ← Ikon website
```

---

## Tech Stack

- **Frontend:** HTML5, CSS3, JavaScript (vanilla)
- **Server:** Apache (Hostinger Shared Hosting)
- **Deploy:** GitHub → Hostinger Git (auto-deploy)
- **App Booking:** repo terpisah (PHP 8.3 + React/Vite)

---

## Local Development

Karena ini website static, lo bisa langsung buka file HTML di browser:

```bash
# Clone repo
git clone https://github.com/robbyaliasaakbar/indeepcleaningid.git
cd indeepcleaningid

# Buka di browser (atau pakai Live Server di VS Code)
open index.html
```

Atau pakai simple HTTP server:

```bash
# Python
python3 -m http.server 8000

# Node (kalau ada)
npx serve .
```

Buka `http://localhost:8000` di browser.

---

## Deployment

Website ini **auto-deploy** ke Hostinger setiap push ke branch `main`:

1. Push code ke GitHub
2. GitHub notify Hostinger via webhook
3. Hostinger pull latest code ke `public_html/`
4. Website live dalam ±15-20 detik

> ⚠️ **Penting:** Karena auto-deploy aktif, semua perubahan WAJIB lewat Pull Request. Lihat [contributing.md](contributing.md).

---

## App Booking

App booking online **tidak** ada di repo ini. Kodenya hidup di repo terpisah dan di-deploy ke subdomain sendiri:

- **URL:** [https://booking.indeepcleaningid.site](https://booking.indeepcleaningid.site)
- **Tech:** PHP 8.3 (backend) + React/Vite (frontend)
- **Database:** MySQL (Hostinger)

Website ini cuma nautin link ke subdomain tersebut. Kalau mau mengubah app booking, kerjakan di repo-nya sendiri.

---

## Kontribusi

Baca [contributing.md](contributing.md) sebelum contribute.

**Ringkasan:**
- `main` = production → **dilarang push langsung**
- Semua perubahan lewat **Pull Request**
- **Bang Rob** yang review dan merge
- Setiap PR wajib update [engineering.md](engineering.md)

---

## License

Proprietary — lihat [LICENSE](LICENSE).

Copyright (c) 2026 Robby. All rights reserved.

---

## Kontak

- **Website:** [indeepcleaningid.site](https://indeepcleaningid.site)
- **WhatsApp:** +62 877-4824-4464
- **Email:** [kontak via website](https://indeepcleaningid.site/contact)
