# ENGINEER — Log Perubahan

> Dokumen ini wajib di-update setiap kali ada perubahan lewat PR.
> Format: tanggal, judul, apa yang berubah + kenapa, file yang kena.

---

## 2026-10-14

### Inisialisasi monorepo website InDeep CleaningID

**Apa:** Setup awal repository monorepo untuk website InDeep CleaningID.

**Kenapa:** Sebelumnya website di-deploy manual (zip upload) dan app booking
di repo terpisah. Monorepo menyatukan semua jadi satu sumber kebenaran dan
memudahkan deploy via GitHub → Hostinger Git.

**Yang berubah:**
- Buat `.gitignore` — block file development (`__shot.html`, `chat.md`, `*.sh`)
- Buat `README.md` — dokumentasi overview website
- Buat `LICENSE` — proprietary license (source available for inspection)
- Buat `CONTRIBUTING.md` — aturan kontribusi (wajib PR, owner review)
- Buat `ENGINEER.md` — file ini (log perubahan)
- `git init` — inisialisasi repository

**File:** `.gitignore`, `README.md`, `LICENSE`, `CONTRIBUTING.md`, `ENGINEER.md`

### Hapus folder invoice/ dan landingpage/

**Apa:** Hapus folder `invoice/` (app lama yang sudah tidak dipakai) dan
`landingpage/` (landing page ads lama yang akan dibuat ulang di subdomain
terpisah). Bersihkan referensi di `sitemap.xml` dan `.htaccess`.

**Kenapa:** `invoice/` adalah app lama yang sudah tidak digunakan.
`landingpage/` akan diganti dengan landing page baru di subdomain khusus
(terpisah dari website utama).

**Yang berubah:**
- Hapus folder `invoice/` (5 file)
- Hapus folder `landingpage/` (1 file: `v2.html`)
- Hapus 2 entry landing page dari `sitemap.xml`
- Hapus rewrite rules `/landingpage/v2` dari `.htaccess`

**File:** `sitemap.xml`, `.htaccess`, `invoice/`, `landingpage/`

### Update README.md sinkron dengan struktur terkini

**Apa:** Perbarui README.md setelah penghapusan folder `invoice/` dan
`landingpage/`. Hapus referensi ke folder yang sudah dihapus, perbarui
nama repo dan URL clone.

**Kenapa:** README harus mencerminkan kondisi aktual repository.

**Yang berubah:**
- Hapus `invoice/` dan `landingpage/` dari diagram struktur
- Tandai `booking/` sebagai "[akan ditambahkan]"
- Update nama repo di diagram struktur
- Update URL clone di bagian Local Development

**File:** `README.md`

---

## 2026-10-16

### SEO: OG image 1200×630 di semua halaman (issue #23)

**Apa:** Ganti `og:image`/`twitter:image` di website utama dari `Logo.webp`
(513×513) ke `assets/img/og-banner.webp` (**1200×630**, standar OG).

**Kenapa:** Sebelumnya semua halaman pakai logo polos sebagai OG image → saat
di-share di WA/FB/Twitter cuma tampil logo, kurang menarik klik. Sekarang visual
khusus + dimensi sesuai standar social preview.

**Yang berubah:**
- Tambah aset `assets/img/og-banner.webp` (1200×630).
- `og:image` + `twitter:image` → `og-banner.webp` di 13 halaman (index, about,
  contact, gallery, coverage, pricing-estimator, 404, dan 6 halaman services).
- `og:image:width`/`height` sudah 1200/630 (konsisten dengan aset).

**File:** `assets/img/og-banner.webp` (baru) + 13 halaman HTML

---

## 2026-10-15

### Security: header HSTS di website utama + booking (issue #28)

**Apa:** Tambah header `Strict-Transport-Security` di root `.htaccess` dan
`booking/public/.htaccess`.

**Kenapa:** Tanpa HSTS, browser masih memulai request HTTP pertama yang bisa
diganggu (SSL-strip) sebelum redirect 301 ke HTTPS berlaku. 1 baris, biaya
hampir nol.

**Yang berubah:**
- Nilai: `max-age=31536000; includeSubDomains` (**tanpa** `preload` — tunggu
  semua subdomain siap HTTPS penuh).
- Dipasang di header utama (`Header always set`) supaya tetap terkirim di
  respons redirect maupun error.

**File:** `.htaccess`, `booking/public/.htaccess`

---

## 2026-10-15

### SEO website: H1 about.html + meta description + title baby-stuff (issue #20, #21, #22)

**Apa:** Perbaikan SEO on-page di website utama (root).

**Kenapa:** Hasil audit SEO — `about.html` tidak punya tag `<h1>` (Google lemah
paham topik halaman); meta description `about.html` 170 char (kepotong di hasil
search); title `services/baby-stuff.html` 71 char (>60, kepotong).

**Yang berubah:**
- `about.html`: heading hero `Mengapa Indeep Cleaning Ada?` (dulu `<h2>`) →
  `<h1>Tentang Indeep Cleaning — Jasa Cuci Soft Furniture Jabodetabek</h1>`;
  meta description dipendekkan 170 → 140 char.
- `services/baby-stuff.html`: title 71 → 58 char
  (`Jasa Cuci Baby Stuff Jakarta - Indeep Cleaning | Aman Bayi`).

**File:** `about.html`, `services/baby-stuff.html`

---

## 2026-10-22

### Ignore folder plan_prd di .gitignore

**Apa:** Menambahkan folder `plan_prd/` ke `.gitignore`.

**Kenapa:** Folder `plan_prd/` digunakan untuk menyimpan dokumen rencana perakitan/spesifikasi dan desain internal (`design.md`, `spec.md`) saat proses planning, sehingga tidak ikut ter-commit ke repositori produksi.

**Yang berubah:**
- Tambah rule `plan_prd/` di `.gitignore`.

**File:** `.gitignore`, `ENGINEER.md`

### Rapihin minor website utama: logo, BENTO Baby Stuff, hapus services/index, nav Layanan, SEO

**Apa:** Lima perubahan minor di website utama: (1) logo navbar+footer yang salah
pakai `og-banner.webp` diganti ke `assets/img/Logo.webp` (25 tag di 13 file);
(2) `CTA Tile (navy)` di section SERVICES BENTO homepage diganti `Service Card 5:
Baby Stuff` dengan style sama kayak Service Card 4; (3) hapus `services/index.html`
(noise, sudah ke-cover homepage) + arahkan semua link ke anchor `#layanan`,
bersihkan sitemap, tambah redirect 301 `/services/` → `/#layanan`;
(4) hapus item menu "Layanan" dari navbar desktop+mobile (tetap ada di footer);
(5) hapus semua meta `twitter:*` (tidak ada akun Twitter) + tambah 1 link promo
ke landing page conversion di footer homepage.

**Kenapa:** Logo yang tampil salah (pakai banner OG). CTA tile navy redundan
dengan halaman layanan. `services/index.html` noise dan duplikat homepage.
Menu Layanan double (navbar + footer). Twitter card tidak dipakai. Landing page
conversion di subdomain butuh sinyal internal link dari website utama.

**Yang berubah:**
- Logo `og-banner.webp` → `Logo.webp` + alt `Logo Indeep Cleaning` (13 file)
- `index.html` BENTO: CTA navy → Service Card 5 Baby Stuff (`services/baby-stuff.html`)
- Hapus `services/index.html`; nav/breadcrumb → `index.html#layanan`; sitemap hapus
  entry `/services/`; `.htaccess` 301 `/services/` → `/#layanan`
- Hapus 22 link nav "Layanan" (11 file, desktop+mobile); footer + `#layanan` utuh
- Hapus ±50 tag `twitter:*` (11 file utama; `booking/` + `landing_page/` tidak disentuh)
- `index.html` footer: link promo `promo jasa cuci sofa, kasur & karpet profesional
  Jabodetabek` → `https://landingpage.indeepcleaningid.site/`
- `.gitignore`: tambah `.commandcode/`, `landing_page/`, `assets-arsip/`

**File:** `index.html`, `about.html`, `contact.html`, `coverage.html`, `gallery.html`,
`pricing-estimator.html`, `404.html`, `services/baby-stuff.html`,
`services/cuci-kasur.html`, `services/cuci-sofa.html`,
`services/cuci-karpet-gordyn.html`, `services/interior-mobil.html`,
`services/index.html` (dihapus), `.htaccess`, `sitemap.xml`, `.gitignore`, `ENGINEER.md`

---

## 2026-10-23

### Pisahkan repo: `booking/` dan `landing_page/` keluar dari repo website

**Apa:** `booking/` dan `landing_page/` dihapus dari working directory karena
keduanya sudah punya repo sendiri. Dokumentasi disesuaikan supaya tidak lagi
mengklaim repo ini sebagai monorepo.

**Kenapa:** Dua folder itu stack-nya beda dan deploy-nya ke subdomain sendiri,
jadi lebih rapi kalau repo-nya terpisah. `booking/` juga menyimpan credential
asli (`config/config.php`, `web/.env.development`) serta `node_modules` 173MB —
risikonya terlalu besar kalau ikut repo website. Repo ini sekarang murni isi
halaman statis.

**Yang berubah:**
- Hapus folder `booking/` dari working directory (pindah ke repo sendiri)
- Hapus folder `landing_page/` dari working directory (sudah punya repo
  `landingpage-conv.git`)
- `README.md`: framing "monorepo" → "website utama"; hapus referensi `booking/`
  dan `services/index.html` dari diagram struktur; section App Booking diubah
  jadi penjelasan repo terpisah; URL clone dijadikan placeholder
- `README.md`: perbaiki 3 link rusak — `CONTRIBUTING.md` → `contributing.md`,
  `ENGINEER.md` → `engineering.md` (nama file asli huruf kecil, di Linux 404)
- `contributing.md`: "berisi dua aplikasi" → hanya website utama; hapus
  sub-section App Booking; hapus sebutan `landingpage/`; tambah tabel subdomain
  untuk booking & landing page

**File:** `README.md`, `contributing.md`, `engineering.md`

### Tambah `humans.txt`

**Apa:** Tambah `humans.txt` di root. Isinya info tim, info situs, projek
terkait, dan catatan cakupan repo — format mengikuti `humans.txt` yang sudah
ada di repo landing page.

**Kenapa:** Wajib ada sebelum go-live (aturan stack). Juga jadi penanda eksplisit
buat siapa pun yang buka repo bahwa app booking & landing page dikelola di
repo terpisah.

**Yang berubah:**
- Buat `humans.txt` — data kontak diambil dari JSON-LD `LocalBusiness` di
  `index.html` supaya konsisten (telepon, email, alamat, IG)

**File:** `humans.txt`

### Blokir file dokumentasi repo dari akses publik

**Apa:** `README.md`, `contributing.md`, `engineering.md`, dan `LICENSE`
diblokir dari akses web lewat `.htaccess`, plus ditambah `Disallow` di
`robots.txt`.

**Kenapa:** Auto-deploy Hostinger menyalin seluruh isi repo ke `public_html/`,
jadi file dokumentasi ikut bisa dibuka publik di `indeepcleaningid.site/README.md`
dan berpotensi keindeks mesin pencari. Ditemukan saat verifikasi production
pasca-deploy pertama: keempat file itu balas `200`. Isinya tidak memuat
credential, tapi `engineering.md` memuat path internal dan alur kerja repo —
tidak layak tampil di halaman publik.

**Yang berubah:**
- `.htaccess`: tambah `RedirectMatch 404` untuk README/contributing/engineering/LICENSE
  (dengan atau tanpa ekstensi, case-insensitive). Dipilih `RedirectMatch` (mod_alias)
  bukan `Require all denied` supaya kompatibel Apache 2.2 maupun 2.4 — aman di
  shared hosting mana pun. `humans.txt` sengaja tidak diblokir.
- `robots.txt`: tambah `Disallow` untuk 4 file tersebut

**File:** `.htaccess`, `robots.txt`

### Update `lastmod` sitemap.xml ke 2026-10-23

**Apa:** Semua 11 entry di `sitemap.xml` diubah `lastmod`-nya dari `2026-10-14`
jadi `2026-10-23`.

**Kenapa:** Seluruh halaman HTML terakhir dimodifikasi 2026-10-23 (perubahan
meta, logo, dan struktur section), tapi `sitemap.xml` masih menandai
2026-10-14. Sitemap yang `lastmod`-nya basi bikin crawler malas re-crawl
halaman yang sebenarnya sudah berubah.

**Yang berubah:**
- `sitemap.xml`: 11 `lastmod` → `2026-10-23`

**File:** `sitemap.xml`

---

## Format Entry

Copy template di bawah ini untuk entry baru:

```markdown
### Judul singkat perubahan

**Apa:** Apa yang berubah.

**Kenapa:** Kenapa perubahan ini dilakukan.

**Yang berubah:**
- Item 1
- Item 2

**File:** file1, file2, folder/file3
```
