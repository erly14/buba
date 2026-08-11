# buba
 kegiatan penelitian dan pengabdian serta umkm

# Rangkuman Proses: Solusi Pengecekan Stok Barang Menipis

Dokumen ini merangkum seluruh proses berpikir dari identifikasi masalah sampai prototype dirilis ke sales, disusun mengikuti tahapan: Brief & Observe → Synthesize → Sharpen → Anchor → Diverge → Converge → Commit → Build Lean → Ship Early → Listen Deeply → Iterate Fast.

---

## 1. Brief & Observe

**Masalah awal**: Mengecek barang habis atau tidak di toko. Cara lama: mendatangi toko satu per satu, memakan waktu ±5 jam setiap akhir bulan per minggu.

**Bagaimana orang menyelesaikannya sekarang**:
- Kunjungan fisik terjadwal ke tiap toko, biasanya di akhir bulan.
- Verifikasi visual manual di rak/gudang, kemungkinan tanpa alat bantu digital terstandarisasi.
- Tidak ada checkpoint di antara kunjungan — kondisi stok "buta" sampai kunjungan berikutnya.
- Waktu proses berskala linear dengan jumlah toko.
- Sumber kebenaran adalah observasi langsung, bukan laporan — menandakan laporan dari toko (kalau ada) belum cukup dipercaya.

**Hal paling bikin frustrasi**:
- Waktu tersita dalam blok besar dan berulang (5 jam terkonsentrasi di akhir bulan).
- Delay antara kejadian (barang habis) dan deteksi (baru ketahuan di akhir bulan).
- Proses sulit didelegasikan — Anda jadi bottleneck karena akurasi bergantung verifikasi langsung.
- Tidak ada akumulasi data historis dari kunjungan sebelumnya.
- Beban fisik/logistik (waktu transportasi) di luar waktu cek stok murni.

---

## 2. Synthesize

**Tujuan tahap ini**: menantang keyakinan bahwa "saya sulit mendata barang habis atau tidak setiap bulannya" benar-benar masalah yang layak diselesaikan sekarang — menguji kekuatan argumen sebelum melangkah membangun sesuatu.

**Argumen 1: Ini Masalah Simtomatik, Bukan Masalah Inti**
"Sulit mendata barang habis" itu framing di level aktivitas, bukan di level dampak bisnis. Kalau ditanya "memangnya kenapa kalau telat tahu barang habis?", jawabannya mungkin: kehilangan penjualan (lost sales), pelanggan kecewa dan pindah ke toko lain, atau restock jadi tidak efisien. Kalau begitu, masalah "sebenarnya" adalah **kehilangan pendapatan akibat stockout yang tidak terdeteksi tepat waktu** — dan pendataan cuma salah satu cara untuk menyelesaikannya, bukan satu-satunya. Bisa saja dibangun sistem pendataan yang sempurna, tapi kalau ternyata stockout cuma terjadi di 2 dari 20 SKU dan dampaknya ke omzet kecil, itu artinya energi dihabiskan untuk membangun solusi bagi masalah yang secara ekonomi tidak signifikan.

*Pertanyaan balik*: Sudahkah dihitung, dari seluruh kejadian barang habis yang baru terdeteksi di akhir bulan, berapa besar kerugian riil (dalam rupiah)? Kalau belum pernah dihitung, klaim "layak diselesaikan" ini masih berupa asumsi, bukan fakta.

**Argumen 2: 5 Jam/Minggu Mungkin Bukan Masalah Besar Secara Relatif**
5 jam per minggu terdengar banyak, tapi perlu dibandingkan dengan konteks:
- Berapa total jam kerja per minggu? Kalau 40 jam, ini cuma 12.5%.
- Apakah 5 jam itu waktu yang "hilang", atau sebenarnya juga dipakai untuk hal lain yang berguna saat kunjungan toko (cek kondisi toko, ngobrol dengan staf, quality control visual)? Kalau begitu, menghilangkan aktivitas ini lewat sistem digital bisa jadi menghilangkan manfaat sampingan yang tidak disadari.
- Apakah ini masalah yang berulang dan akan tumbuh, atau beban tetap yang stabil? Kalau jumlah toko tidak bertambah, beban 5 jam ini tidak akan membesar — artinya urgensinya tidak meningkat seiring waktu, dan menunda solusi tidak menimbulkan kerugian eksponensial.

**Argumen 3: Mungkin Sedang Terjebak "Solution Bias"**
Ada pola umum: orang yang sudah lama menjalani proses manual yang melelahkan cenderung ingin "menyelesaikan" proses itu — bukan karena analisis biaya-manfaat, tapi karena rasa frustrasi personal terhadap rutinitas yang membosankan. Ini valid sebagai motivasi manusiawi, tapi bukan validasi bisnis.

*Tes untuk membedakan*: Kalau 5 jam ini digantikan dengan tugas administratif lain yang sama membosankannya tapi tidak berhubungan dengan stok, apakah masih akan dibilang "ini masalah yang layak diselesaikan"? Kalau jawabannya "ya, karena buang waktu", berarti masalah sebenarnya adalah efisiensi waktu secara umum, bukan spesifik soal stok barang.

**Argumen 4: Ada Kemungkinan Solusi Ini Sudah "Cukup Baik"**
Datang langsung ke toko punya keunggulan yang sistem digital sering tidak punya: akurasi *ground-truth*. Kondisi rak dilihat sendiri, bukan mempercayai laporan orang lain yang bisa salah input, malas lapor, atau punya insentif untuk memanipulasi data (misalnya menyembunyikan kekurangan stok karena takut ditegur).

Kalau diganti dengan sistem pendataan digital, ada risiko menukar masalah "menghabiskan waktu tapi akurat" dengan masalah baru "hemat waktu tapi data tidak bisa dipercaya" — yang justru bisa membutuhkan waktu lebih lama untuk diperbaiki di kemudian hari (audit ulang, investigasi selisih stok, dsb).

**Pertanyaan Penutup untuk Menguji Keyakinan**:
1. Apakah ada angka kerugian riil (bukan estimasi kasar) dari keterlambatan deteksi stok habis?
2. Apakah 5 jam ini murni "waktu terbuang", atau ada nilai tersembunyi (relasi dengan staf toko, quality control) yang akan hilang kalau diotomasi?
3. Kalau proyek ini ditunda 6 bulan lagi, apa konsekuensi konkretnya — atau justru tidak ada bedanya?

Kalau setelah menjawab ini keyakinan tetap kuat bahwa masalah ini layak diselesaikan sekarang, keyakinan itu jadi jauh lebih valid karena sudah teruji. Kalau ada yang goyah, mungkin ada masalah lain yang lebih layak diprioritaskan.

---

## 3. Sharpen

**Tujuan tahap ini**: mempertajam definisi masalah lebih dalam — mencari akar masalah di balik gejala permukaan, memetakan siapa saja yang terlibat, dan mengenali pola yang mungkin terlewat karena terlalu dekat dengan masalah ini sehari-hari.

**Kemungkinan akar masalah** (bukan cuma gejala di permukaan):
- Tidak ada sumber data stok yang bisa dipercaya tanpa verifikasi fisik — kalau ada sistem yang akurat, tidak perlu datang langsung. Ini menunjukkan ada gap antara data yang dilaporkan (jika ada) dan kondisi riil di lapangan.
- Proses pencatatan stok di tiap toko tidak seragam — mungkin tiap toko punya cara sendiri (buku, Excel, ingatan kasir), sehingga tidak bisa dibandingkan atau digabung tanpa turun langsung.
- Tidak ada pemicu (trigger) otomatis saat stok menipis — pengecekan baru terjadi karena jadwal rutin (akhir bulan), bukan karena sistem memberi sinyal. Kalau ada barang habis di tanggal 5, itu baru diketahui di tanggal 28.
- Kurangnya akuntabilitas di level toko — bisa jadi staf toko tidak merasa bertanggung jawab melaporkan stok, sehingga tugas itu jatuh ke pemilik/pengelola untuk verifikasi manual.

*Pertanyaan reflektif*: apakah masalah utamanya "cara mengecek stok", atau sebenarnya "cara mendapatkan kepercayaan terhadap data stok"? Ini dua masalah yang solusinya beda jauh.

**Pihak yang terlibat atau terdampak**:
- **Pemilik/pengelola** — pihak yang menanggung beban waktu (5 jam/minggu).
- **Staf/kasir toko** — sumber data primer, tapi mungkin tidak dilibatkan dalam desain sistem pelaporan.
- **Pemilik/manajer tiap cabang** — punya kepentingan atas akurasi stok tokonya.
- **Bagian pembelian/purchasing** — butuh data stok untuk restock tepat waktu.
- **Pelanggan** — terdampak langsung kalau barang habis tidak terdeteksi cepat.
- **Supplier** — bisa terdampak kalau pola order jadi tidak teratur karena keterlambatan deteksi stok.

*Catatan*: perlu dicek apakah staf toko tahu bahwa 5 jam dihabiskan untuk proses ini — kadang orang yang paling dekat dengan sumber masalah tidak sadar dampaknya ke pihak lain.

**Pola yang mungkin terlewat karena terlalu dekat dengan masalah ini**:
- **Bias frekuensi**: karena sudah terbiasa cek bulanan, mungkin tidak lagi dipertanyakan kenapa harus bulanan — padahal bisa jadi masalah stok sebenarnya butuh deteksi mingguan atau bahkan harian untuk kategori barang tertentu.
- **Toko "bermasalah" yang berulang**: apakah semua toko sama-sama butuh porsi waktu yang sama dari 5 jam itu, atau sebenarnya sebagian besar waktu habis di 1-2 toko tertentu yang datanya selalu tidak akurat? Kalau iya, itu masalah spesifik di toko tersebut, bukan masalah sistemik semua toko.
- **Solusi yang pernah dicoba tapi gagal**: kalau pernah ada usaha digitalisasi (spreadsheet bersama, aplikasi) yang akhirnya ditinggalkan, alasan kegagalannya sering lebih informatif daripada mencari solusi baru dari nol.
- **Definisi "habis" yang tidak konsisten**: mungkin tiap toko punya ambang batas berbeda soal kapan barang dianggap "hampir habis" vs "habis", sehingga perbandingan antar toko jadi tidak apple-to-apple.

---

## 4. Anchor

**Constraint yang ditetapkan sebagai jangkar solusi**: mengecek jumlah pelanggan tetap (repeat customers) — solusi yang dibangun harus tetap kompatibel/relevan dengan kebutuhan memantau pelanggan tetap, bukan hanya fokus stok semata.

Ini menjadi batasan yang membingkai opsi solusi di tahap berikutnya, khususnya mengarahkan eksplorasi ke arah yang menggabungkan data stok dengan data perilaku pelanggan.

---

## 5. Diverge

Lima bentuk solusi yang dieksplorasi (berbeda secara mendasar satu sama lain):

| # | Solusi | Kelemahan Utama |
|---|--------|------------------|
| 1 | Pelaporan manual via WhatsApp terstruktur | Sangat bergantung pada kedisiplinan staf |
| 2 | Barcode/QR scan dengan aplikasi inventory off-the-shelf | Butuh investasi awal & training staf, risiko resistensi teknologi |
| 3 | Sistem sampling statistik (bukan cek semua barang) | Risiko barang di luar sampel habis tanpa terdeteksi |
| 4 | Kombinasi kunjungan fisik + wawancara cepat staf/pelanggan | Data subjektif, tidak presisi untuk keputusan restock |
| 5 | Insentif terbalik — toko melapor sendiri karena ada reward | Butuh waktu membentuk kebiasaan, risiko manipulasi laporan |

---

## 6. Converge

**Solusi terpilih**: Menggunakan skala pembelian terbanyak, jangka pembelian kembali (repeat purchase interval), dan jumlah yang dibeli sebagai proxy untuk menyimpulkan status stok.

**Kelemahan/celah yang ditemukan (kritik tajam)**:
1. **Blind spot fatal**: barang yang sudah habis tidak menghasilkan data pembelian — justru di momen paling krusial, metode ini paling buta (survivorship bias).
2. Tidak memperhitungkan restock, barang rusak, atau kehilangan — model ini menangkap demand, bukan stok riil.
3. Masalah *cold start* untuk barang/pelanggan baru — butuh histori panjang sebelum bisa dipercaya.
4. Asumsi keteraturan perilaku pelanggan terlalu kuat — banyak faktor eksternal bisa merusak pola tanpa hubungan dengan stok.
5. Menjawab pertanyaan yang berbeda dari masalah asli — ini model demand forecasting, bukan model status stok.
6. Bias terhadap barang fast-moving, blind spot terhadap barang long-tail.
7. Butuh infrastruktur data transaksi granular yang belum tentu sudah ada dan rapi.

**Kesimpulan tajam**: pendekatan ini menjawab pertanyaan tentang stok menggunakan data perilaku beli pelanggan — dua variabel yang berkorelasi tapi tidak identik, dan paling lemah persis saat barang benar-benar habis.

---

## 7. Commit

**Keputusan MVP**:
- **Fitur wajib**: kode barcode tercatat.
- **Fitur yang sengaja ditunda**: laporan pembelian dan penjualan.
- Fokus MVP murni pada pencatatan transaksi via barcode + 3 kalkulasi dasar (skala pembelian, jangka beli ulang, jumlah dibeli), tanpa dashboard/visualisasi.

---

## 8. Build Lean

**Langkah teknis membangun MVP dengan Claude Code**:

1. **Tentukan struktur data inti** sebelum coding — tabel Barang (barcode, nama, toko) dan tabel Transaksi (barcode, id_pelanggan, jumlah, tanggal).
2. **Setup proyek** dengan Claude Code (`mkdir` → `cd` → `claude`), gunakan SQLite untuk kesederhanaan MVP.
3. **Bangun fitur input barcode** — opsi input manual/scanner USB (berperilaku seperti keyboard) atau integrasi kamera (`pyzbar`/`quagga.js`).
4. **Bangun 3 fungsi kalkulasi inti**: total kuantitas dibeli per barcode, rata-rata selisih hari antar transaksi per kombinasi pelanggan-barcode, jumlah dibeli per transaksi — tanpa fitur laporan/dashboard.
5. **Uji dengan data dummy** (20 transaksi acak) untuk validasi logika sebelum pakai data toko asli.
6. **Jalankan dan validasi manual** dengan input barcode riil, bandingkan hasil kalkulasi dengan perhitungan manual.

---

## 9. Ship Early

Prototype **"web aplikasi stok barang yang sudah menipis"** dirilis ke tim sales untuk dicoba langsung — sebagai langkah validasi awal sebelum menambah fitur lanjutan (termasuk laporan yang sengaja ditunda di tahap Commit).

---

## 10. Listen Deeply

**5 pertanyaan untuk menggali feedback jujur dari sales** (dirancang untuk menangkap kebingungan di 10 detik pertama, bukan basa-basi):

1. *"Coba buka aplikasinya sekarang, tanpa saya jelaskan apa-apa. Hal pertama yang mau kamu klik itu apa, dan kenapa?"* — menangkap first impression murni.
2. *"Coba cari tahu barang apa yang paling mendesak untuk direstock, sambil kamu ceritakan apa yang kamu pikirkan."* — teknik think-aloud saat mengerjakan tugas nyata.
3. *"Kalau kamu harus jelasin ke sales lain cara pakai aplikasi ini dalam satu kalimat, kalimatnya apa?"* — uji kejelasan konsep/mental model.
4. *"Di titik mana tadi kamu sempat mikir 'ini maksudnya apa ya' — meskipun cuma sebentar?"* — memancing momen keraguan kecil yang sering tidak diakui spontan.
5. *"Kalau aplikasi ini hilang besok dan kamu balik ke cara lama, apa yang paling kamu rindukan — dan apa yang justru bikin lega karena gak perlu lagi?"* — menangkap value riil vs beban baru.

Tips: ajukan pertanyaan #1–#2 saat sesi berlangsung (real-time), pertanyaan #3–#5 setelah sesi selesai sebagai refleksi.

---

## 11. Iterate Fast

Tahap ini adalah langkah **berikutnya** yang belum dijalankan — hasil dari sesi Listen Deeply di atas akan menjadi input utamanya. Beberapa hal yang perlu disiapkan begitu feedback dari sales masuk:

- **Kelompokkan feedback** berdasarkan jenis: kebingungan navigasi (dari Q1–Q2), kejelasan konsep (Q3–Q4), atau value gap (Q5).
- **Prioritaskan perbaikan** berdasarkan seberapa sering pola yang sama muncul di beberapa sales, bukan dari satu orang saja.
- **Putuskan siklus berikutnya**: apakah perbaikan berikutnya masih dalam scope "barcode tercatat" (bug/UX fix), atau sudah waktunya mempertimbangkan fitur yang sebelumnya ditunda (laporan pembelian/penjualan) berdasarkan kebutuhan riil yang terungkap dari sesi Listen Deeply.
- **Ingat kembali kritik dari tahap Converge**: kalau feedback sales menunjukkan mereka butuh tahu *status stok* secara langsung (bukan cuma pola pembelian), ini sinyal kuat bahwa asumsi di tahap Converge perlu direvisi sebelum iterasi berikutnya dibangun.

*(Bagian ini akan terisi lebih lengkap setelah sesi feedback dengan sales benar-benar dilakukan.)*
