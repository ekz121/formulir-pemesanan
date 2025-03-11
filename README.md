# formulir-pemesanan

Selamat datang di proyek Formulir Pemesanan Produk! Ini adalah aplikasi web yang memungkinkan pengguna untuk mengisi formulir pemesanan produk secara interaktif dan mengirimkan pesanan melalui email. Proyek ini dibangun menggunakan HTML, CSS, JavaScript, dan memanfaatkan layanan EmailJS untuk pengiriman email tanpa backend server.

Deskripsi Proyek
Proyek ini adalah formulir pemesanan produk yang dirancang dengan antarmuka modern dan responsif. Pengguna dapat mengisi data seperti nama lengkap, email, alamat pengiriman, produk yang dipilih, dan jumlah produk, lalu mengirimkan pesanan melalui email. Formulir ini dilengkapi dengan validasi input, animasi, dan desain futuristik yang menarik.

Fitur Utama
Formulir Interaktif: Pengguna dapat mengisi formulir dengan validasi langsung untuk memastikan data yang dimasukkan valid.
Pengiriman Pesan via Email: Menggunakan layanan EmailJS untuk mengirimkan pesanan ke email tanpa memerlukan backend server.
Desain Responsif: Formulir menyesuaikan diri dengan berbagai ukuran layar, dari desktop hingga perangkat seluler.
Validasi Input: Memastikan semua data yang dimasukkan pengguna valid sebelum pengiriman.
Animasi Visual: Efek animasi seperti fade-in pada header dan slide-up pada formulir untuk pengalaman pengguna yang lebih baik.
Desain Futuristik: Menggunakan palet warna neon (cyan dan hitam) dengan font Poppins untuk kesan modern.

================================================================================================================================
Dependensi
Proyek ini bergantung pada layanan dan sumber daya eksternal berikut:

Google Fonts: Menggunakan font Poppins untuk tampilan modern. Font ini diambil melalui CDN, sehingga memerlukan koneksi internet. Jika Anda ingin menjalankan aplikasi offline, unduh font Poppins dan integrasikan secara lokal.
EmailJS: Menggunakan EmailJS SDK untuk mengirim email tanpa backend server. SDK ini diambil melalui CDN:
html

Ciutkan

Wrap

Salin
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
Catatan tentang Error <DOCUMENT>
Pesan error berikut muncul di kode Anda:

text

Ciutkan

Wrap

Salin
<DOCUMENT>
Couldn't find the requested file /dist/email.min.js"></script in @emailjs/browser.</DOCUMENT>
Error ini menunjukkan bahwa ada masalah dengan penutupan tag <script> atau penulisan path saat memuat EmailJS SDK. Dalam kode yang Anda berikan, tag <script> sudah benar:

html

Ciutkan

Wrap

Salin
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
Pastikan tidak ada kesalahan pengetikan atau tag yang tidak tertutup dengan benar di kode Anda. Jika error ini tetap muncul, periksa koneksi internet Anda atau coba gunakan versi terbaru dari EmailJS SDK dengan mengganti @3 ke versi spesifik (misalnya, @3.10.0).

Fitur Responsif
Formulir ini dirancang untuk menjadi responsif, artinya tampilan dan fungsionalitasnya menyesuaikan dengan berbagai ukuran layar, termasuk desktop, tablet, dan perangkat seluler. Berikut adalah elemen responsif yang diimplementasikan:

Media Query CSS:
Pada layar kecil (lebar maksimum 480px), padding pada container formulir dikurangi, ukuran font header diperkecil, dan padding tombol disesuaikan untuk menghemat ruang:
css

Ciutkan

Wrap

Salin
@media (max-width: 480px) {
    .form-container {
        padding: 20px;
    }

    header h1 {
        font-size: 1.5em;
    }

    button {
        padding: 12px;
    }
}
Desain Fluida:
Elemen seperti input, select, dan tombol menggunakan width: 100% untuk memastikan elemen mengisi lebar container tanpa meluap.
Container utama (form-container) memiliki max-width: 600px untuk menjaga formulir tetap terpusat dan tidak terlalu lebar pada layar besar.
Viewport Meta Tag:
Tag berikut memastikan halaman menyesuaikan dengan lebar perangkat dan skala awal yang sesuai:
html

Ciutkan

Wrap

Salin
<meta name="viewport" content="width=device-width, initial-scale=1.0">
Pengiriman Pesan
Menggunakan Apa?
Pengiriman pesan dilakukan menggunakan EmailJS, sebuah layanan yang memungkinkan pengiriman email langsung dari sisi klien (frontend) tanpa memerlukan server backend. EmailJS mengintegrasikan JavaScript dengan layanan email pihak ketiga (seperti Gmail, SendGrid, dll.) yang telah Anda konfigurasi di dashboard EmailJS.

Cara Kerja Pengiriman Pesan:
Inisialisasi EmailJS:
EmailJS diinisialisasi dengan Public Key Anda:
javascript

Ciutkan

Wrap

Salin
emailjs.init("EO5oTo-thw3OIoZyy");
Public Key ini dapat ditemukan di dashboard EmailJS setelah Anda membuat akun.
Pengumpulan Data Formulir:
Data dari formulir dikumpulkan menggunakan JavaScript dan divalidasi sebelum pengiriman. Data yang dikumpulkan meliputi:
Nama lengkap (fullName)
Email (email)
Alamat pengiriman (address)
Produk yang dipilih (product)
Jumlah produk (quantity)
Pengiriman Email:
Data dikirim menggunakan fungsi emailjs.send, dengan parameter:
Service ID: 'service_n11rglg' (ID layanan email Anda di EmailJS).
Template ID: 'template_d0tf2nl' (ID template email yang telah Anda buat di EmailJS).
Parameter: Objek yang berisi data formulir (params).
Contoh kode pengiriman:
javascript

Ciutkan

Wrap

Salin
emailjs.send('service_n11rglg', 'template_d0tf2nl', params)
    .then(function(response) {
        alert('Pesanan berhasil dikirim! Anda akan diarahkan ke halaman terima kasih.');
        document.getElementById('orderForm').reset();
        window.location.href = 'thank-you.html';
    }, function(error) {
        alert('Gagal mengirim pesanan: ' + JSON.stringify(error));
    });
Template Email:
Anda harus membuat template email di dashboard EmailJS yang mendefinisikan format email yang akan dikirim. Template ini biasanya menggunakan placeholder seperti {{fullName}}, {{email}}, dll., yang akan diganti dengan data formulir.
Isi Formulir
Formulir berisi kolom berikut:

Nama Lengkap: Input teks untuk nama pengguna (wajib diisi).
Email: Input email dengan validasi format email (wajib diisi).
Alamat Pengiriman: Input teks untuk alamat pengiriman (wajib diisi).
Pilih Produk: Dropdown untuk memilih produk (opsi: Charger HP, Mouse Laptop, Lontong) (wajib diisi).
Jumlah Produk: Input angka untuk jumlah produk yang dipesan (minimal 1, wajib diisi).
Elemen-Elemen Coding
Berikut adalah penjelasan rinci tentang elemen-elemen utama dalam kode:

1. HTML
Struktur Dasar:
Menggunakan DOCTYPE HTML5 dan tag <html lang="id"> untuk mendefinisikan bahasa Indonesia.
Tag <meta charset="UTF-8"> memastikan karakter di-render dengan benar.
Tag <meta name="viewport"> memastikan responsivitas pada perangkat seluler.
Header:
Berisi logo perusahaan (<img src="img/1.jpg">) dan judul (<h1>Formulir Pemesanan Produk</h1>).
Diberi animasi fade-in melalui CSS.
Formulir:
Elemen <form id="orderForm"> dengan event onsubmit="return sendEmail(event)" untuk menangani pengiriman.
Setiap kolom formulir dikelompokkan dalam <div class="form-group"> untuk organisasi yang lebih baik.
Setiap input memiliki atribut required untuk validasi bawaan browser.
Pesan error ditampilkan dalam <div class="error"> yang awalnya disembunyikan (display: none).
Footer:
Berisi informasi hak cipta dengan desain sederhana.
Script Eksternal:
Memuat EmailJS SDK melalui CDN untuk fungsi pengiriman email.
2. CSS
Styling Umum:
Menggunakan box-sizing: border-box untuk memastikan padding dan border tidak memengaruhi ukuran elemen.
Menggunakan font Poppins dari Google Fonts untuk tampilan modern.
Desain Futuristik:
Warna latar belakang gelap (#1a1a1a, #2c2c2c) dengan teks putih (#fff) dan aksen neon cyan (#00ffcc).
Bayangan neon (box-shadow) untuk efek futuristik.
Input dan Tombol:
Input dan select memiliki latar belakang gelap (#3d3d3d) dan border radius untuk tampilan modern.
Efek fokus pada input/select dengan bayangan cyan (box-shadow: 0 0 5px #00ffcc).
Tombol memiliki efek hover dengan transformasi skala (transform: scale(1.05)) dan perubahan warna (background: #00e6b8).
Animasi:
Animasi fadeIn untuk header:
css

Ciutkan

Wrap

Salin
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}
Animasi slideUp untuk container formulir:
css

Ciutkan

Wrap

Salin
@keyframes slideUp {
    from { transform: translateY(50px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
}
Responsivitas:
Menggunakan media query untuk menyesuaikan padding, ukuran font, dan elemen lain pada layar kecil.
3. JavaScript
Inisialisasi EmailJS:
Menggunakan fungsi emailjs.init dengan Public Key untuk mengaktifkan layanan EmailJS.
Fungsi sendEmail:
Mencegah pengiriman form default dengan event.preventDefault().
Melakukan validasi input sebelum pengiriman:
Nama lengkap: Tidak boleh kosong.
Email: Harus valid menggunakan regex (/^[^\s@]+@[^\s@]+\.[^\s@]+$/).
Alamat: Tidak boleh kosong.
Produk: Harus dipilih.
Jumlah: Harus lebih dari 0.
Jika validasi gagal, menampilkan pesan error di bawah kolom yang bersangkutan.
Jika validasi berhasil, mengirim email menggunakan emailjs.send dengan parameter yang sesuai.
Menampilkan notifikasi sukses atau gagal, mereset formulir, dan mengarahkan ke halaman terima kasih.
