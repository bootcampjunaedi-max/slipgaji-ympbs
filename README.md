# Slip Gaji Terpusat — YASMA PB. Soedirman (v2.0)

Portal slip gaji 7 unit: 6 unit sekolah (TK – SMK-2) + unit Non Pendidikan. Frontend statis di **GitHub Pages**, backend **Google Apps Script** sebagai REST API (JSON).

- Pegawai melihat slip lewat **tautan pribadi WhatsApp** atau masuk dengan **NRP + kata sandi**
- Admin Yayasan: unggah rekap Excel, validasi, kirim slip via Email / WhatsApp (±350 nomor), arsip PDF, log audit
- Admin Sekolah: pemantauan unit tanpa melihat nominal gaji

## Struktur repo

```
index.html              ← halaman aplikasi (SPA)
css/style.css           ← tampilan (tema zamrud–emas, mode gelap)
js/config.js            ← GAS_URL — URL /exec Apps Script (WAJIB diisi)
js/api.js               ← koneksi fetch() ke backend (POST text/plain)
js/app.js               ← seluruh logika halaman
PANDUAN-INSTALASI.md    ← panduan lengkap backend + GitHub Pages
.nojekyll               ← matikan Jekyll di GitHub Pages
```

Repo ini **tidak berisi rahasia**: token WhatsApp, kata sandi, ID spreadsheet, dan data gaji tetap di Google (Sheets + Script Properties). Backend (`Kode.gs`, `appsscript.json`) ada di folder `backend/` paket migrasi dan ditempel ke editor Apps Script — tidak disimpan di repo ini.

## Deploy singkat

1. Isi `GAS_URL` di `js/config.js` dengan URL `/exec` (Deploy Web App: *Execute as* **Me**, *Who has access* **Anyone**).
2. Dari folder ini (`slip-gaji-yasma/frontend` — yang berisi `index.html`):
   ```bash
   git init
   git add .
   git commit -m "Upload pertama"
   git branch -M main
   git remote add origin https://github.com/USERNAME/slip-gaji-yasma.git
   git push -u origin main
   ```
3. GitHub → **Settings → Pages** → *Deploy from a branch* · **main** · **/ (root)** → centang **Enforce HTTPS**.
4. Buka `https://USERNAME.github.io/slip-gaji-yasma/`, masuk sebagai Admin Yayasan, lalu isi **Pengaturan → URL Aplikasi** dengan alamat tersebut.

## Update

```bash
git add .
git commit -m "Deskripsi perubahan"
git push
```

Panduan lengkap & troubleshooting: [PANDUAN-INSTALASI.md](PANDUAN-INSTALASI.md)
