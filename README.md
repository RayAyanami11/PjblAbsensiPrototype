# Absensi Online XI.3 — Firebase

## Isi project
- `index.html`, `style.css`, `app.js`: website.
- `firebase-config.js`: konfigurasi web Firebase.
- `firestore.rules`, `storage.rules`: aturan keamanan.

## 1. Buat project Firebase
1. Buka https://console.firebase.google.com/ lalu buat project.
2. Tambahkan aplikasi Web (`</>`), salin konfigurasi Firebase ke `firebase-config.js`.
3. Authentication > Sign-in method > aktifkan Email/Password.
4. Firestore Database > Create database.
5. Storage > Get started.
6. Publish isi `firestore.rules` ke Firestore Rules dan `storage.rules` ke Storage Rules.

## 2. Aktifkan admin pertama
1. Daftarkan akun admin lewat form Daftar akun di website.
2. Buka Firestore > collection `users` > dokumen dengan ID UID akun admin.
3. Ubah field `role` dari `student` menjadi `admin` (string).
4. Keluar lalu masuk kembali. Tab Daftar siswa dan Admin akan muncul.

Jangan pernah memberikan role admin dari form pendaftaran. Role admin hanya diubah langsung oleh pengelola Firebase.

## 3. Jalankan dan deploy
Untuk uji lokal, gunakan Live Server atau server lokal yang mendukung ES modules.
Upload semua file project ke root repository GitHub, bukan hanya index.html.
Aktifkan GitHub Pages: Settings > Pages > Deploy from a branch > main > /(root).

## Catatan penting
- Setiap siswa membuat akun sendiri dengan email dan password. Setelah itu profil awal muncul di daftar siswa.
- Nomor absen diisi siswa pada profil; admin perlu memeriksa kecocokannya dengan daftar resmi kelas.
- Siswa hanya dapat membaca profil/absensinya sendiri. Admin dapat melihat data kelas.
- Firebase config di browser bukan password; keamanan bergantung pada Authentication dan Security Rules.
- Jangan masukkan NIK, alamat rumah, nomor telepon pribadi, atau data sensitif yang tidak diperlukan.
- Gunakan data uji dahulu. Minta izin guru/sekolah sebelum mengunggah data siswa sungguhan.
- Aturan ini adalah fondasi awal; sebelum dipakai resmi, sebaiknya tambahkan verifikasi identitas siswa dan pembatasan tanggal/periode absensi.


## Akun guru
- Guru juga membuat akun lewat form Daftar akun (pakai email sekolah/guru yang disetujui).
- Pendaftaran publik otomatis memberi role `student`; tidak ada pilihan role guru di halaman daftar.
- Setelah akun guru dibuat, admin project harus membuka Firestore > `users` > dokumen UID akun guru, lalu mengubah field `role` menjadi string `teacher`.
- Guru logout lalu login kembali. Menu Daftar siswa dan Admin akan muncul.
- Guru dapat melihat data siswa XI.3, membaca riwayat absensi kelas dan menandai pengajuan sakit/izin sebagai `ditinjau`.
- Guru tidak dapat mengubah role akun, menghapus catatan, atau mengubah data absensi lain. Hak admin tetap lebih tinggi.
- Jangan membagikan akses Firebase Console kepada guru jika tidak diperlukan; cukup berikan akun aplikasi dengan role `teacher`.
