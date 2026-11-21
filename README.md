# Website Indrawan — KTA & Multiguna

Website statis (HTML + Tailwind CSS). Tidak perlu build/instalasi.

## Struktur
```
bpr-website/
├── index.html              ← teks halaman, SEO, section
├── assets/js/config.js     ← ★ EDIT DI SINI: kontak & TABEL ANGSURAN
├── assets/js/main.js       ← logika simulasi (jarang perlu diubah)
├── assets/img/             ← logo, favicon, og-image (preview share)
├── robots.txt
└── sitemap.xml
```

## Mengubah tabel angsuran (paling sering)
Buka `assets/js/config.js`. Tiap produk punya `tenor` dan `tabel`.
Satu baris = satu plafond: `[plafond, angsuran tenor-1, angsuran tenor-2, ...]`

```js
tenor: [6, 9, 12],
tabel: [
  [3000000, 650000, 484000, 400000],   // plafond 3 jt: 6 bln, 9 bln, 12 bln
  ...
]
```
- Tambah plafond baru = tambah satu baris. Hapus plafond = hapus barisnya.
- Tambah tenor baru = tambah angka di `tenor` dan satu angka di setiap baris.
- Simulator mengambil angka langsung dari tabel (tanpa rumus/pembulatan), jadi selalu sama dengan tabel resmi.

## Mengubah kontak
`config.js` → `brand`, `marketer`, `namaBpr`, `kontak` (WhatsApp, telepon, email, alamat, jam kerja).
Nomor WhatsApp format `6281234567890` (tanpa +, spasi, atau 0 di depan).

## Mengubah teks
- Teks, FAQ, persyaratan → `index.html`.
- Bila FAQ diubah, ubah juga blok JSON-LD `FAQPage` di `<head>`.

## Sebelum online (wajib)
1. Ganti `domainanda.co.id` di `index.html`, `robots.txt`, `sitemap.xml` dengan domain asli.
2. Isi `namaBpr`, WhatsApp, telepon, email di `config.js`.
3. Lengkapi persyaratan Multiguna di `index.html` (section `#persyaratan`).
4. Cek ulang angka tabel (lihat catatan di bawah).

## Catatan data tabel
- KTA plafond Rp 4.500.000 tenor 6 bulan = 875.000. Angka ini tampak janggal dibanding baris lain (seharusnya sekitar 975.000). Dimasukkan apa adanya sesuai gambar; mohon dicek ke tabel asli.
- Multiguna baris Rp 50.000.000 memiliki angsuran per juta yang lebih tinggi daripada baris Rp 55–60 juta (kemungkinan perbedaan tier). Sesuai gambar.

## Hosting
Upload seluruh folder ke hosting apa pun (cPanel, Netlify, Vercel, GitHub Pages, Cloudflare Pages).
Setelah live, daftarkan ke Google Search Console dan kirim `sitemap.xml`.

## Catatan Tailwind
Memakai Tailwind CDN agar mudah diedit tanpa build. Untuk performa maksimal bisa dikompilasi dengan Tailwind CLI nanti.
