# Display Informasi All in One — Web Edition

Versi browser tanpa Electron dan tanpa instalasi aplikasi. Cocok dihosting pada HTTPS lalu dibuka menggunakan Chrome, Edge, Firefox, atau browser Smart TV yang mendukung fitur web.

## Fitur
- Visual Layout Designer: tambah komponen, drag untuk pindah, resize dari handle kanan bawah, edit properti, duplikat, hapus, reset.
- Posisi dan ukuran berbasis persentase untuk layout responsif.
- Komponen identitas/logo, jam, area video/foto, agenda, jadwal sholat, dua ticker.
- Video lokal, foto lokal, dan YouTube.
- Playlist dengan urutan naik/turun; video lokal lanjut saat selesai, foto berganti otomatis.
- Agenda/rencana kerja.
- Jam dan tanggal sinkron ke jam perangkat.
- Lokasi GPS via browser (izin lokasi dan HTTPS diperlukan).
- Jadwal sholat dari API AlAdhan.
- Tema, warna, font, transparansi, dan komponen tampil/sembunyi.
- Penyimpanan browser (localStorage), backup/restore JSON.
- Sinkronisasi online opsional melalui endpoint HTTPS GET/PUT JSON.

## Jalankan tanpa instalasi
Tidak perlu Node.js, Electron, atau installer.
1. Ekstrak ZIP.
2. Untuk uji coba, buka `index.html` di Chrome atau Edge. Fitur layout dan pengaturan dasar dapat dicoba.
3. Untuk penggunaan penuh (izin lokasi, penyimpanan media stabil, YouTube embed, dan sinkronisasi), upload tiga file (`index.html`, `styles.css`, `app.js`) ke hosting HTTPS.
4. Buka alamat website dari browser. Tidak ada aplikasi yang perlu diinstal.

## Hosting gratis (contoh GitHub Pages)
1. Buat repository GitHub baru.
2. Upload `index.html`, `styles.css`, dan `app.js` ke root repository.
3. Buka Settings → Pages.
4. Pilih Deploy from a branch → `main` → `/ (root)` → Save.
5. Buka URL GitHub Pages yang diberikan. Hosting serupa dapat digunakan melalui Netlify, Cloudflare Pages, atau server web sendiri.

## Penting tentang penyimpanan
- Konfigurasi dan media yang dipilih disimpan pada browser perangkat yang sedang digunakan. Browser dapat membatasi kuota localStorage; file media besar dapat membuat kuota penuh.
- File media disimpan sebagai data browser pada versi ini. Jangan gunakan video berukuran sangat besar. Untuk instalasi produksi, pindahkan media ke object storage/cloud storage dan simpan URL-nya.
- Browser tidak dapat membaca folder komputer secara diam-diam; pengguna harus memilih file melalui dialog file.
- Browser tidak dapat memaksa jam sistem berubah. Jam display mengikuti waktu perangkat.
- Lokasi GPS memerlukan izin dan umumnya hanya tersedia pada localhost atau HTTPS.
- YouTube perlu internet, video harus mengizinkan embedding, dan autoplay dapat berjalan tanpa suara karena aturan browser.
- Jadwal sholat diambil dari API AlAdhan. Periksa kesesuaian metode dan hasil dengan otoritas resmi setempat.

## Sinkronisasi online antarperangkat
Kolom endpoint membutuhkan backend milik Anda. Kontrak sederhana:
- `GET https://domain/api/config` → mengembalikan JSON konfigurasi.
- `PUT https://domain/api/config` → menerima JSON konfigurasi dan menyimpannya.
- CORS harus mengizinkan domain hosting aplikasi.
- Gunakan HTTPS dan autentikasi token. Jangan letakkan kunci rahasia server di source code frontend.

Versi paket ini tidak menyediakan akun, database cloud, atau penyimpanan media cloud otomatis. Untuk pemakaian banyak layar, backend dan object storage perlu disiapkan.

## File
- `index.html`: aplikasi web.
- `styles.css`: desain.
- `app.js`: logika layout, media, agenda, prayer, storage, cloud API.

## Saran produksi
Tambahkan autentikasi admin, database cloud, object storage, sinkronisasi playlist lintas perangkat, pengelolaan hak akses, dan backup terjadwal sebelum digunakan pada lingkungan publik.
