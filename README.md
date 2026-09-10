# Web Code Editor

Web-based code ringan yang berjalan hanya dari **satu file `index.html`**. Dibuat untuk menempelkan (copy-paste) kode HTML, CSS, dan JavaScript — misalnya hasil dari AI — dan langsung melihat outputnya di browser tanpa perlu membuka VS Code atau menjalankan server lokal.

Terinspirasi dari CodePen / VS Code, tapi tanpa instalasi apa pun.

---

## ✨ Fitur

Fitur,Keterangan
🖥️ Editor kode,Menggunakan Monaco Editor (engine yang sama dengan VS Code)
🎨 Syntax highlighting,Tema kustom bergaya GitHub Light & Dark
💡 Autocomplete / IntelliSense,Muncul otomatis saat mengetik
⚡ Emmet / Auto-tag,Ketik div.box>ul>li*3 + Tab → langsung jadi struktur HTML lengkap
🔀 3 Tab (HTML/CSS/JS),Tiap bahasa punya area kode sendiri
▶️ Live Preview,"Output dirender di <iframe>, real-time (auto-run) atau manual (tombol Run)"
↔️ Splitter resizable,Batas antara panel editor & preview bisa digeser (mouse & touch)
🪟 Draggable Floating Navbar,Menu kontrol melayang yang posisinya bisa digeser bebas (drag & drop) di area layar
📁 Upload file,Upload atau drag & drop file .html / .css / .js dari laptop
💾 Save otomatis,"Kode tersimpan ke localStorage, aman dari refresh/tutup tab"
⬇️ Download per file,"Unduh index.html, style.css, atau script.js secara terpisah"
⚙️ Pengaturan,Ganti tema (Light/Dark) dan ukuran tab (2/4/8 spasi) lewat menu
📱 Responsif,Layout otomatis menjadi atas/bawah di layar kecil

## 🚀 Cara Menjalankan

1. Simpan file `index.html` di komputer.
2. Buka file tersebut langsung menggunakan browser (double-click atau klik kanan → *Open with browser*).
3. Selesai — tidak perlu `npm install`, server, atau build tool apa pun.

> ⚠️ **Wajib terhubung ke internet.** Semua library (Tailwind CSS, jQuery, Monaco Editor, Emmet) dimuat lewat CDN, bukan disertakan di dalam file.

---

## 🧩 Teknologi yang Digunakan

Semua dimuat via CDN, tanpa proses instalasi:

- **[Tailwind CSS](https://tailwindcss.com/)** — styling UI
- **[jQuery](https://jquery.com/)** — manipulasi DOM & event handling
- **[Monaco Editor](https://microsoft.github.io/monaco-editor/)** — komponen text editor (engine VS Code)
- **[emmet-monaco-es](https://github.com/Nyshuk-Studio/emmet-monaco-es)** — dukungan Emmet (auto-tag) di atas Monaco

---

## 📖 Panduan Penggunaan

### 1. Menulis / Menempel Kode
Klik tab **HTML**, **CSS**, atau **JavaScript** di panel kiri, lalu ketik atau tempel kode. Setiap tab menyimpan isinya masing-masing secara terpisah selama sesi berjalan.

### 2. Melihat Hasil
- **Auto-run** (aktif secara default): hasil di panel kanan otomatis diperbarui ±0.6 detik setelah kamu berhenti mengetik.
- **Tombol ▶ Run**: jalankan/refresh preview secara manual kapan saja, termasuk saat Auto-run dimatikan.

### 3. Menggunakan Emmet (Auto-tag)
Di tab **HTML**, ketik singkatan seperti:
```
ul.list>li.item*3
```
lalu tekan **Tab** → otomatis berubah menjadi struktur `<ul class="list"><li class="item"></li>...</ul>` lengkap. Berlaku juga untuk singkatan CSS di tab **CSS**.

### 4. Upload File dari Laptop
- Klik tombol **📁 Upload** → pilih satu atau beberapa file `.html`, `.css`, `.js`.
- Atau langsung **drag & drop** file ke area editor (akan muncul kotak biru putus-putus sebagai penanda area drop).
- File otomatis masuk ke tab yang sesuai berdasarkan ekstensinya.

### 5. Menyimpan Kode
- Kode **otomatis tersimpan** ke `localStorage` browser setiap kali kamu berhenti mengetik (debounced ±1 detik), dan juga saat menutup/refresh tab.
- Klik tombol **💾 Save** untuk menyimpan secara manual dan mendapat notifikasi konfirmasi.
- Jika penyimpanan browser penuh (`QuotaExceededError`), akan muncul notifikasi peringatan — kode di editor tidak hilang, hanya proses simpan otomatis yang gagal.
- Saat file `index.html` dibuka kembali, kode terakhir yang tersimpan akan otomatis dimuat.

### 6. Mengunduh Kode
Klik tombol **⬇ Download**, lalu pilih file yang ingin diunduh:
- `index.html` (isi tab HTML)
- `style.css` (isi tab CSS)
- `script.js` (isi tab JavaScript)

### 7. Pengaturan (⚙ Settings)
Klik tombol **⚙ Settings** untuk membuka panel pengaturan:
- **Tema**: Light ☀️ atau Dark 🌙 — memengaruhi tampilan editor sekaligus seluruh UI.
- **Ukuran Tab**: 2, 4, atau 8 spasi — langsung diterapkan ke editor.

Pengaturan ini juga tersimpan di `localStorage` sehingga tetap sama saat kamu membuka ulang file.

### 8. Mengubah Ukuran Panel
Arahkan kursor ke garis pemisah (splitter) di antara panel editor dan panel preview, lalu klik-tahan dan geser untuk memperlebar/mempersempit salah satu sisi. Mendukung mouse maupun sentuhan (touch).

### 8. Draggable Floating Navbar Mode
- Logika Mode OFF (Split-Screen View - Default):
Jika mode ini dimatikan, tampilan kembali ke desain standar saya: Layar terbagi dua (Kiri untuk Editor Kode, Kanan untuk Output Preview).
Draggable Floating Navbar disembunyikan (hidden).

- Logika Mode ON (Single-Screen View dengan Draggable Navbar):
Jika mode ini diaktifkan, layar tidak lagi terbagi dua, melainkan mengambil lebar penuh (100% width) untuk salah satu panel saja.
Draggable Floating Navbar akan muncul dan melayang di layar.
Di dalam navbar tersebut, terdapat 2 tombol navigasi: "Input" dan "Output".
Jika user mengklik tombol "Input", halaman akan menampilkan panel Editor Kode secara penuh (fullscreen/w-full), dan panel Output disembunyikan.
Jika user mengklik tombol "Output", halaman akan berpindah menampilkan panel Output Preview (iframe) secara penuh, dan panel Editor disembunyikan.
Syarat Kritis: Meskipun panel Output sedang disembunyikan (saat user di halaman "Input"), proses real-time rendering harus tetap berjalan di latar belakang. Jadi begitu user mengklik "Output", hasilnya sudah up-to-date tanpa perlu me-reload iframe.

---

## 🗂️ Struktur Data (localStorage)

| Key | Isi |
|---|---|
| `mini_playground_code_v1` | Objek JSON `{ html, css, javascript }` — isi kode tiap tab |
| `mini_playground_settings_v1` | Objek JSON `{ theme, tabSize }` — preferensi pengguna |

Untuk mereset seluruh data (kode & pengaturan) ke kondisi awal, hapus kedua key di atas lewat DevTools browser (Application → Local Storage) atau jalankan di Console:
```js
localStorage.removeItem('mini_playground_code_v1');
localStorage.removeItem('mini_playground_settings_v1');
```

---

## ⚠️ Batasan yang Perlu Diketahui

- **Butuh koneksi internet** karena seluruh library dimuat dari CDN.
- Kode JavaScript di preview dijalankan di dalam `<iframe sandbox="...">` dengan `try/catch` sederhana — error runtime akan tampil sebagai pesan merah di preview, bukan membuat halaman blank.
- Kapasitas `localStorage` terbatas (umumnya ±5MB per domain tergantung browser) — untuk kode yang sangat besar, gunakan fitur **Download** sebagai cadangan.
- Tidak ada dukungan preprocessor (SCSS/TypeScript) atau modul eksternal (`import`/`require`) di dalam kode JS yang dijalankan.

---

## 🛠️ Rencana Pengembangan Selanjutnya (opsional)
- Export/import seluruh project sebagai satu file `.html` gabungan.
- Multiple project slot (menyimpan beberapa playground berbeda).
- Dukungan library tambahan (React/Vue) via CDN di tab konfigurasi.