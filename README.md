# Toko App - Aplikasi Manajemen Produk Toko

Aplikasi Android native (Java) untuk UAS Mobile Programming.

## Fitur
1. **Autentikasi** — Login & Register (data user disimpan permanen di SQLite)
2. **Dashboard** — Menampilkan daftar produk (RecyclerView) + fitur pencarian
3. **Detail Data** — Lihat detail produk, tombol Edit & Hapus
4. **Fitur tambahan**:
   - Tambah produk baru (CRUD - Create)
   - Edit produk (CRUD - Update)
   - Hapus produk dengan konfirmasi (CRUD - Delete)
   - Pencarian produk secara real-time
   - Session login dengan **SharedPreferences** (tetap login walau app ditutup)
   - Logout dengan konfirmasi dialog
   - Penyimpanan permanen dengan **SQLite** (tabel `users` dan `produk`)

## Struktur Project
```
TokoApp/
├── app/
│   ├── build.gradle
│   └── src/main/
│       ├── AndroidManifest.xml
│       ├── java/com/example/tokoapp/
│       │   ├── SplashActivity.java        -> Cek session, redirect Login/Dashboard
│       │   ├── LoginActivity.java         -> Form login
│       │   ├── RegisterActivity.java      -> Form registrasi
│       │   ├── DashboardActivity.java     -> List produk + search + logout
│       │   ├── DetailProdukActivity.java  -> Detail + edit + hapus
│       │   ├── TambahEditProdukActivity.java -> Form tambah/edit produk
│       │   ├── DatabaseHelper.java        -> SQLite (CRUD users & produk)
│       │   ├── SessionManager.java        -> SharedPreferences session
│       │   ├── Produk.java                -> Model data produk
│       │   └── ProdukAdapter.java         -> RecyclerView Adapter
│       └── res/
│           ├── layout/   (semua file XML tampilan)
│           ├── drawable/ (icon & background)
│           ├── values/   (colors, strings, themes)
│           └── menu/     (menu toolbar dashboard)
├── build.gradle
└── settings.gradle
```

## Cara Membuka di Android Studio
1. Buka **Android Studio**
2. Pilih **File > Open**
3. Arahkan ke folder `TokoApp` (folder yang berisi `build.gradle` dan `settings.gradle`)
4. Tunggu proses **Gradle Sync** selesai (Android Studio otomatis mengunduh Gradle wrapper)
5. Jalankan dengan tombol **Run ▶** (pilih emulator atau device fisik)

## Cara Membuat APK (Build Release)
1. Di Android Studio, pilih menu **Build > Build Bundle(s) / APK(s) > Build APK(s)**
2. Tunggu proses build selesai
3. Klik notifikasi **locate** untuk menemukan file APK (biasanya di `app/build/outputs/apk/debug/app-debug.apk`)
4. Untuk APK release (sudah dikompilasi optimal), pilih **Build > Generate Signed Bundle / APK** lalu pilih APK dan ikuti wizard (buat keystore baru jika belum ada)

## Cara Test Aplikasi
1. Jalankan app → akan muncul **Splash Screen** lalu ke halaman **Login**
2. Klik "Belum punya akun? Daftar di sini" → isi username & password → **Daftar**
3. Login dengan akun yang baru dibuat
4. Di **Dashboard**, klik tombol **+ (FAB)** di kanan bawah untuk menambah produk
5. Isi nama, harga, stok, deskripsi → **Simpan**
6. Klik salah satu produk di list untuk melihat **Detail**
7. Di halaman Detail, bisa **Edit** atau **Hapus** produk
8. Gunakan kolom pencarian di Dashboard untuk mencari produk
9. Klik menu (pojok kanan atas) → **Logout** untuk keluar

## Catatan Teknis
- Database: SQLite manual (menggunakan `SQLiteOpenHelper`), 2 tabel: `users` dan `produk`
- Session login disimpan di `SharedPreferences` (tetap login setelah app ditutup, sampai logout manual)
- Minimum SDK: 21 (Android 5.0)
- Tidak memerlukan koneksi internet (semua data lokal)

## Upload ke GitHub
```bash
cd TokoApp
git init
git add .
git commit -m "UAS Mobile Programming - Toko App"
git branch -M main
git remote add origin <URL_REPO_GITHUB_ANDA>
git push -u origin main
```
