# Kedai Kopi Karsa

Link GitHub Pages: https://github.com/arinafazal/kedai_kopi.git

Website kedai kopi sederhana pakai HTML dan CSS, terdiri dari 3 halaman (beranda, menu, pemesanan).

---

## Jawaban Minggu 3

### 1. Sebutkan satu bagian yang kamu susun dengan Flexbox dan satu bagian dengan Grid. Kenapa pilihan itu cocok?

**Flexbox** saya pakai di bagian header, buat nyusun nama kedai sama link navigasi. Di HP keduanya numpuk ke bawah, tapi di layar lebar nama kedai ada di kiri dan nav di kanan. Flexbox cocok disini karena cuma perlu ngatur satu arah aja (horizontal di desktop, vertikal di HP), jadi ga perlu Grid yang lebih ribet.

**Grid** saya pakai di halaman menu buat nyusun card-card menu. Pakai Grid karena butuh layout 2 dimensi yang bisa berubah jumlah kolomnya: 1 kolom di HP, 2 kolom di tablet (600px), dan 3 kolom di desktop (960px). Kalau pakai Flexbox bisa sih tapi ngatur wrap dan lebar tiap card-nya lebih ribet, pakai Grid tinggal ganti `grid-template-columns` di media query.

### 2. Ceritakan satu aturan CSS yang awalnya tidak berlaku. Apa yang kamu lihat di panel Styles, dan bagaimana kamu memperbaikinya?

Waktu pertama kali bikin, saya coba kasih `width: 100%` ke input form tapi ga ngefek karena ternyata input-nya ga ada di dalam kontainer yang lebarnya jelas. Di panel Styles, properti `width: 100%` keliatan ada tapi pas dicek Computed ternyata lebarnya tetep kecil kayak default.

Setelah saya bungkus input-input itu pake div class `form-group` dan kasih form-nya `max-width: 500px`, baru deh `width: 100%` pada input jadi berfungsi karena sekarang 100% itu ngikutin lebar parent-nya yang udah jelas.

---

## Jawaban Minggu 2

### 1. Apa yang muncul di address bar setelah form dikirim dan kenapa datanya bisa muncul disitu?

Setelah klik tombol kirim, URL di address bar berubah jadi kayak gini:

```
pesan.html?nama=Budi&whatsapp=08123456&menu=latte&jumlah=2&cara_ambil=Ambil+di+tempat&catatan=
```

Ini terjadi karena di form kita pakai `method="get"`. Kalau pakai method GET, data yang diisi di form bakal ditempel langsung di URL sebagai query string. Query string itu dimulai dari tanda `?`, terus tiap data dipisah pakai tanda `&`. Formatnya `nama_field=nilai`. Kalau ada spasi, otomatis diganti jadi tanda `+`.

Beda sama method POST yang datanya dikirim lewat body request jadi ga keliatan di URL. Kalau GET keliatan semua di address bar karena emang nempel di URL-nya.

### 2. Pilih satu bagian yang pakai elemen semantik, jelaskan kenapa pilih elemen itu dan bukan div?

Saya pakai elemen `<nav>` buat bagian navigasi di semua halaman:

```html
<nav>
  <a href="index.html">Beranda</a>
  <a href="menu.html">Menu</a>
  <a href="pesan.html">Pesan</a>
</nav>
```

Alasan pakai `<nav>` dan bukan `<div>`:

- `<nav>` itu langsung ngasih tau ke browser dan screen reader kalau bagian ini adalah navigasi utama website. Kalau pakai `<div>` biasa, browser ga tau itu fungsinya buat apa.
- Buat orang yang pakai screen reader, mereka bisa langsung loncat ke bagian navigasi tanpa harus dengerin semua konten dari atas.
- Search engine juga lebih gampang ngerti struktur website kita kalau pakai elemen semantik yang tepat.
- Kode jadi lebih gampang dibaca sama developer lain karena langsung keliatan mana bagian navigasinya tanpa harus cek class atau id.
