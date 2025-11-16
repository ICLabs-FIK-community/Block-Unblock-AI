# Panduan Skrip Blokir AI


---

## Deskripsi File

Semua file ini harus berada di dalam satu folder yang sama.

### File Skrip Inti (PowerShell)

* `1-BlokAI.ps1`
    * Skrip utama untuk **MEMBLOKIR** situs AI.
    * Secara otomatis meminta hak Administrator (UAC).
    * Mencadangkan file `hosts` asli ke `hosts.backup_ai_ps` sebelum memodifikasi.
    * Menambahkan daftar domain AI ke file `hosts` untuk memblokirnya.
    * Membersihkan DNS cache.

* `2-unBlokAI.ps1`
    * Skrip utama untuk **MEMBUKA BLOKIR** situs AI.
    * Secara otomatis meminta hak Administrator (UAC).
    * Memulihkan (restore) file `hosts` asli dari backup `hosts.backup_ai_ps`.
    * Membersihkan DNS cache.

### File Penyembunyi Folder

* Folder hidden:
* `Run.ps1`
    * Skrip untuk membuat folder `BlokAI` ini menjadi tersembunyi dari file sistem.
* `Back.ps1`
    * Skrip untuk **Menampilkan Kembali** folder ini agar terlihat normal.

---

## ⚙️ Instruksi Setup (Wajib)

Lakukan ini **satu kali** di setiap komputer lab.

1.  **Salin Folder:** Salin seluruh folder `BlokAI` ini ke lokasi yang konsisten di setiap komputer. Lokasi yang disarankan adalah:
    `C:\Users\<NamaUser>\Documents\`
    (Skrip ini dirancang untuk bekerja dari path `%USERPROFILE%\Documents\SkripBlokirAI`)

2.  **Jalankan Skrip Penyembunyi:**
    * Akses folder documents/hidden
    * Klik kanan file `Run.ps1`.
    * Pilih **"Run with PowerShell"**.
    * Folder ini sekarang akan hilang dari File Explorer.

Setelah disembunyikan, folder dan skrip di dalamnya tetap dapat dieksekusi melalui NetSupport atau Command Prompt.

---

## Cara Penggunaan di NetSupport

Ini adalah cara tercepat untuk menjalankan skrip di banyak komputer sekaligus dari konsol NetSupport Anda. Gunakan fitur "Run", "Execute", atau "Remote Command".

### Untuk MEMBLOKIR AI:

Salin dan jalankan perintah ini di NetSupport:

```cmd
powershell.exe -ExecutionPolicy Bypass -File "%USERPROFILE%\Documents\blokAI\blokAI.ps1"
