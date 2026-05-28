# Instruksi Penggunaan Arsip RT Digital

## Cara Menambahkan Dokumen PDF

### 1. Siapkan File PDF
Pastikan file PDF Anda sudah siap. Berikut adalah daftar dokumen yang bisa ditambahkan:

| Nama File | Keterangan |
|---|---|
| `AD_ART_RT01_2025.pdf` | Anggaran Dasar & Anggaran Rumah Tangga |
| `LPJ_17_Agustus_2025.pdf` | Laporan Pertanggungjawaban 17 Agustus |
| `LPJ_Halal_Bihalal_2025.pdf` | Laporan Pertanggungjawaban Halal Bihalal |
| `Format_Surat_RT.pdf` | Template Surat Pengantar/Domisili |
| `Notulen_Rapat_Warga.pdf` | Notulen Rapat Warga |
| `Jadwal_Ronda_Malam.pdf` | Jadwal Ronda Malam |
| `Inventaris_RT.pdf` | Daftar Inventaris RT |
| `Kas_Keuangan_RT.pdf` | Laporan Kas & Keuangan |

### 2. Upload ke GitHub
1. Buka repository GitHub Anda
2. Masuk ke folder `documents/`
3. Upload file-file PDF Anda
4. Commit changes

### 3. Update Data Dokumen (jika perlu)
Jika nama file PDF berbeda, edit file `src/data/documents.ts` dan sesuaikan field `pdfUrl`:

```typescript
pdfUrl: '/documents/NAMA_FILE_ANDA.pdf',
```

### 4. Deploy Ulang
Setelah upload PDF, deploy ulang ke GitHub Pages:

```bash
npm run build
git add .
git commit -m "Tambah dokumen PDF"
git push origin main
```

## Cara Deploy ke GitHub Pages

### Setup Repository
1. Buat repository baru di GitHub
2. Upload semua file project ini
3. Pastikan folder `dist/` sudah di-build

### Enable GitHub Pages
1. Buka Settings > Pages di repository
2. Pilih source: `Deploy from a branch`
3. Pilih branch: `main`, folder: `/ (root)` atau `/docs`

### Alternatif: Deploy dari folder `dist/`
Jika menggunakan branch `gh-pages`:
```bash
npm run build
cd dist
git init
git add .
git commit -m "Deploy"
git branch -M gh-pages
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin gh-pages -f
```

## Struktur Folder
```
repo/
├── documents/          # Taruh file PDF di sini
│   ├── AD_ART_RT01_2025.pdf
│   ├── LPJ_17_Agustus_2025.pdf
│   └── ...
├── src/
│   ├── data/
│   │   └── documents.ts    # Data dokumen
│   └── ...
├── public/
│   └── documents/      # Folder untuk PDF (saat development)
└── dist/               # Output build (untuk deploy)
```

## Catatan Penting
- Website ini menggunakan **HashRouter** untuk kompatibilitas GitHub Pages
- PDF viewer menggunakan react-pdf dengan worker dari CDN
- Pastikan file PDF tidak terlalu besar (maksimal 10MB per file direkomendasikan)
- Semua file PDF harus berada di folder `documents/` di root repository
