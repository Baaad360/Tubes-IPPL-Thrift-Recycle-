# Spesifikasi Kebutuhan Perangkat Lunak (SKPL)
**Aplikasi Marketplace Barang Bekas dan Daur Ulang (Thrift & Recycle)**
*Mendukung SDG 12: Konsumsi dan Produksi yang Bertanggung Jawab*

---

## 1. Pendahuluan

### 1.1 Tujuan
Dokumen Spesifikasi Kebutuhan Perangkat Lunak (SKPL) ini bertujuan untuk mendefinisikan kebutuhan fungsional dan non-fungsional dari pengembangan aplikasi **Thrift & Recycle**. Dokumen ini menjadi acuan utama bagi *Development Team* dalam menyusun *Product Backlog* dan *Sprint Backlog*, serta acuan bagi *Product Owner* untuk melakukan verifikasi hasil implementasi sistem.

### 1.2 Lingkup Masalah
Aplikasi **Thrift & Recycle** adalah platform digital berbasis *mobile* dan *web* yang memfasilitasi transaksi jual beli barang bekas layak pakai (*thrift*) serta pengumpulan barang tidak layak pakai untuk proses daur ulang (*recycle*). Sistem ini mendukung penerapan ekonomi sirkular dan pelacakan proses daur ulang secara transparan.

### 1.3 Definisi, Akronim, dan Singkatan
* **SKPL:** Spesifikasi Kebutuhan Perangkat Lunak.
* **FR (*Functional Requirement*):** Kebutuhan fungsional sistem.
* **NFR (*Non-Functional Requirement*):** Kebutuhan non-fungsional sistem.
* **Eco-Points:** Poin insentif/penghargaan yang diberikan kepada pengguna yang menjual atau menyumbangkan barang untuk didaur ulang.
* **Pick-up Service:** Layanan penjemputan barang daur ulang oleh kurir mitra.
* **Drop-off Point:** Titik lokasi pengumpulan barang daur ulang terdekat.

### 1.4 Deskripsi Umum Dokumen
Dokumen ini disusun berdasarkan standar IEEE Std 830 yang mencakup deskripsi umum sistem, kebutuhan spesifik fungsional (termasuk *User Stories*), kebutuhan non-fungsional, serta skenario penggunaan (*Use Case Description*).

---

## 2. Deskripsi Umum Sistem

### 2.1 Perspektif Produk
Sistem **Thrift & Recycle** beroperasi sebagai platform terintegrasi yang menghubungkan pengguna umum, mitra pengelola daur ulang (bank sampah, UMKM, pengrajin), dan admin. Sistem menyediakan antarmuka untuk transaksi jual-beli, pemindaian/verifikasi kelayakan barang, serta pelacakan penyaluran limbah.

### 2.2 Karakteristik Pengguna (*User Class*)

| ID Aktor | Kategori Aktor | Deskripsi Peran & Hak Akses |
| :--- | :--- | :--- |
| **ACT-01** | **Penjual** | Mengunggah barang bekas layak pakai ke *marketplace*. |
| **ACT-02** | **Pembeli** | Membeli barang bekas (*thrift*) atau produk hasil daur ulang (*Green Product*). |
| **ACT-03** | **Pengelola Daur Ulang** | Mengambil (*pick-up*), memilah, mengolah barang, serta mengunggah produk daur ulang. |
| **ACT-04** | **Admin** | Memverifikasi pengguna, mengonfirmasi kelayakan barang, dan memantau sistem. |

### 2.3 Batasan-Batasan Sistem
* Aplikasi diakses melalui perangkat Android, iOS, dan *web browser*.
* Pengiriman barang daur ulang dilakukan melalui opsi *Pick-up Service* atau *Drop-off Point*.

---

## 3. Kebutuhan Fungsional (*Functional Requirements*)

### 3.1 Daftar Spesifikasi Kebutuhan Fungsional

| Kode FR | Nama / Deskripsi Kebutuhan | Prioritas | Tipe |
| :--- | :--- | :--- | :--- |
| **SKPL-FR-001** | **Registrasi & Login:** Pengguna dapat membuat akun dan *login* menggunakan *email* atau nomor HP. | *Must Have* | *Core* |
| **SKPL-FR-002** | **Unggah Barang Thrift:** Penjual dapat mengunggah barang bekas lengkap dengan deskripsi, kondisi, dan foto. | *Must Have* | *Core* |
| **SKPL-FR-003** | **Klasifikasi & Verifikasi Barang:** Sistem/Admin menentukan apakah barang masuk kategori *Thrift* or *Recycle*. | *Must Have* | *Core* |
| **SKPL-FR-004** | **Layanan Daur Ulang:** Pengguna dapat mengajukan penjemputan (*pick-up*) atau pengantaran (*drop-off*) barang daur ulang. | *Must Have* | *Core* |
| **SKPL-FR-005** | **Fitur Edukasi:** Sistem menampilkan tips daur ulang dan konsumsi ramah lingkungan. | *Satisfy* | *Supporting* |
| **SKPL-FR-006** | **Sistem Poin Hijau (*Eco-Points*):** Sistem memberikan poin penghargaan bagi pengguna yang mendaur ulang/menjual barang. | *Delighter* | *Incentive* |

### 3.2 Pemetaan *User Story* (Persiapan *Product Backlog*)

1. **US-01 (Registrasi & Autentikasi):**
   * *As a* Pengguna, *I want to* membuat akun dan login dengan email/nomor HP, *So that* saya dapat mengakses fitur aplikasi secara aman.
2. **US-02 (Unggah Barang):**
   * *As a* Penjual, *I want to* mengunggah foto dan detail barang bekas, *So that* barang saya dapat ditinjau dan dijual.
3. **US-03 (Request Daur Ulang):**
   * *As a* Pengguna, *I want to* menjadwalkan penjemputan barang daur ulang, *So that* barang bekas saya dapat disalurkan ke mitra.
4. **US-04 (Konfirmasi & Unggah Produk Daur Ulang):**
   * *As a* Pengelola Daur Ulang, *I want to* mengonfirmasi penerimaan barang dan mengunggah produk daur ulang baru (*Green Product*), *So that* produk dapat dijual kembali di *marketplace*.
5. **US-05 (Penukaran Eco-Points):**
   * *As a* Pengguna, *I want to* mengumpulkan dan menukarkan *Eco-Points*, *So that* saya mendapatkan voucher/diskon atas kontribusi lingkungan saya.

### 3.3 Detail Skenario Use Case (*Use Case Description*)

#### **Use Case 1: SKPL-UC-001 (Unggah & Verifikasi Kelayakan Barang)**
* **Aktor Utama:** Penjual (Pengguna), Admin
* **Pre-condition:** Pengguna telah melakukan *login* ke aplikasi.
* **Main Flow:**
  1. Pengguna membuka menu "Upload Barang".
  2. Pengguna memasukkan nama barang, kategori, kondisi barang, dan mengunggah foto.
  3. Pengguna menekan tombol `[Kirim untuk Review]`.
  4. Admin/Sistem memverifikasi kondisi barang.
  5. Jika barang layak pakai (kondisi baik), sistem menetapkan status kategori sebagai **Thrift Item**.
* **Alternative Flow:**
  * **4a.** Jika kondisi barang rusak/tidak layak pakai, sistem menetapkan status kategori sebagai **Recycle Item** dan mengarahkan pengguna ke menu Layanan Daur Ulang.
* **Post-condition:** Barang terdaftar di katalog *Thrift* atau siap diproses untuk daur ulang.

#### **Use Case 2: SKPL-UC-002 (Request Penjemputan Daur Ulang)**
* **Aktor Utama:** Pengguna, Mitra Daur Ulang
* **Pre-condition:** Barang telah terverifikasi sebagai kategori *Recycle*.
* **Main Flow:**
  1. Pengguna memilih opsi *Pick-up Service*.
  2. Pengguna memilih Mitra Daur Ulang terdekat dan menentukan jadwal pengambilan.
  3. Pengguna menekan tombol `[Jadwalkan Pengambilan]`.
  4. Mitra menerima notifikasi dan mengonfirmasi jadwal penjemputan.
* **Post-condition:** Kurir mitra melakukan penjemputan, kode *tracking* aktif, dan *Eco-Points* ditambahkan ke akun pengguna setelah barang diterima.

---

## 4. Kebutuhan Non-Fungsional (*Non-Functional Requirements*)

| Kode NFR | Kategori | Spesifikasi Kebutuhan |
| :--- | :--- | :--- |
| **SKPL-NFR-001** | **Usability** | Antarmuka pengguna (*UI*) harus memiliki tata letak yang intuitif dan mudah dipahami oleh pengguna umum. |
| **SKPL-NFR-002** | **Security** | Seluruh data sensitif pengguna (kata sandi, informasi kontak) harus dilindungi menggunakan enkripsi. |
| **SKPL-NFR-003** | **Performance** | Sistem harus memberikan respon (*response time*) maksimal **3 detik** per permintaan (*request*). |
| **SKPL-NFR-004** | **Availability** | Sistem harus beroperasi **24/7** dengan standar *uptime* minimal **99%**. |
| **SKPL-NFR-005** | **Compatibility** | Aplikasi harus dapat diakses dan berjalan dengan baik pada sistem operasi Android, iOS, serta *web browser* utama. |