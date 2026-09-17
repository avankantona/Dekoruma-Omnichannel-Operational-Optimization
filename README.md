# Dekoruma-Omnichannel-Operational-Optimization

🛋️ Dekoruma O2O Optimization & Omnichannel Attribution

## 1. Project Overview & Business Context
Perjalanan Dekoruma berekspansi menjadi raksasa *omnichannel* Home & Living lewat puluhan Dekoruma Experience Center (DEC) sukses menaikkan konversi penjualan. Namun, ada celah operasional yang menguras margin saat menangani pengiriman furnitur berdimensi besar (*Bulky Goods*).

Pengiriman dan perakitan furnitur sering kali tidak sinkron. Banyak kasus di mana barang tiba di rumah pelanggan, tetapi tim perakit (*Installer*) baru datang beberapa hari kemudian. Masalah semakin memburuk ketika tim perakit menemukan bahwa komponen furnitur tersebut kurang (*Missing Parts*) dari pabrik, yang berujung pada batalnya perakitan (*Failed Installation*) dan memaksa perusahaan menanggung biaya retur logistik yang sangat mahal. Di sisi lain, dominasi transaksi di *Mobile App* membuat DEC fisik terlihat *underperform* di sistem, memunculkan dugaan kuat adanya fenomena *showrooming* yang tidak teratribusi dengan baik.

🎯 **Key Objectives & Business Questions:**
*   **Objective 1 (Logistics Sync):** Berapa rata-rata *lead time* (selisih hari) pelanggan menunggu dari barang tiba hingga dirakit?
*   **Objective 2 (Supplier QC):** Kategori furnitur apa yang paling sering gagal dirakit, dan apa alasan utamanya?
*   **Objective 3 (Omnichannel Attribution):** Sejauh mana fenomena *showrooming* terjadi antara DEC fisik dan Aplikasi Digital?
*   **Data Cleansing & Integrity:** Menangani standardisasi kategori produk yang tumpang tindih, anomali *Logical Error* (tanggal rakit mendahului tanggal kirim), serta *Outliers* pada biaya perakitan.

---

## 2. Goals & Stakeholders
*   **Tujuan Analisis (Goals):**
    *   **Logistics Sync:** Membangun dasar *rules* sistem untuk menyelaraskan jadwal truk (*Delivery*) dan tukang rakit (*Installer*).
    *   **Supplier QC:** Menemukan kategori produk dan *supplier* yang paling banyak merugikan perusahaan untuk diberikan penalti terukur.
    *   **Omnichannel Attribution:** Mengungkap angka 'Hidden Sales' agar komisi *Sales Consultant* di toko fisik tetap teratribusi dengan adil.
    *   **Data Cleansing:** Menutup celah *bug* anomali pencatatan waktu di sistem kasir.
*   **Stakeholders:** Tim Logistik, Tim *Quality Control* (QC), dan Manajemen *Retail Omnichannel*.

---

## 3. Data Sources & Dictionary
Analisis ini menggunakan 3 tabel relasional yang memuat 300.000 baris data histori pesanan:
*   **`dekoruma_stores`:** Data dimensi saluran penjualan (*Physical Store, Mobile App, Web*).
*   **`dekoruma_products`:** Data dimensi produk, mencakup kategori dan syarat perakitan.
*   **`dekoruma_orders`:** Data fakta transaksi, memuat ID tukang, tanggal kirim & rakit, status kegagalan, hingga biaya perakitan.

---

## 4. Technologies Used
*   **Programming Language:** Python (Pandas, NumPy)
*   **Database & Query:** MySQL, SQLAlchemy, PyMySQL
*   **Visualization:** Matplotlib, Seaborn, Tableau
*   **Environment:** Jupyter Notebook

---

## 5. Project Structure
```
📂 dekoruma-operations-analysis
├── 📄 README.md (Summary & Temuan)
├── 📁 data
│   ├── 📥 raw (Dataset Asli)
│   └── 🧹 clean (Data Bersih CSV)
├── 📓 notebooks (001_avan_capstone.ipynb)
├── 📊 dashboards (Tableau .twbx)
├── 📈 presentations (Dekoruma_Business_Pitch.pptx)
└── ⚙️ requirements.txt (Library)
```
---

📊 **6. Summary of Findings**

💡 **6.1 Business Insights**
*Note: Analisis dilakukan berdasarkan 300.000 data transaksi histori pesanan dengan fokus pada efisiensi operasional dan sinkronisasi logistik.*

| Aspek | Temuan Utama | Dampak Bisnis |
| :--- | :--- | :--- |
| **Waktu Tunggu (Lead Time)** | **Jeda Waktu ~2.5 Hari:** Rata-rata pelanggan harus menunggu selama **2.51 hari** sejak barang tiba hingga dirakit oleh *installer*. | Rumah pelanggan dipenuhi tumpukan kardus *flat-pack*, memicu komplain dan tingginya risiko pembatalan pesanan (*post-purchase trauma*). |
| **Kualitas Supplier (QC)** | **Dominasi Kategori Lemari:** Kategori *Wardrobe/Lemari* mencatatkan angka kegagalan instalasi tertinggi, didominasi alasan *Missing Parts* (baut/komponen kurang dari pabrik). | Perusahaan menanggung biaya retur logistik *bulky goods* yang sangat mahal akibat kelalaian *quality control* pihak *supplier*. |
| **Atribusi Omnichannel** | **Kontribusi DEC Fisik:** Toko fisik secara individual mencatatkan volume transaksi yang sangat kuat, bersaing ketat dengan kanal digital. | Indikasi kuat adanya fenomena *showrooming* (pelanggan melihat produk fisik di DEC namun melakukan *checkout* via aplikasi). |
| **Integritas Data** | **Logical Error & Outliers:** Ditemukan 4.570 data pesanan yang tercatat dirakit sebelum barang dikirim, serta 909 *outliers* pada biaya perakitan. | Kesalahan input manual (*human error*) dan inkonsistensi kategori produk dapat menyesatkan arah kebijakan manajemen jika tidak dibersihkan. |

---

🚀 **6.2 Actionable Recommendations**

📈 **Strategi Operasional & Logistik**
*   **SLA Sync Maksimal 24 Jam:** Membangun *rules* sistem IT yang mewajibkan penjadwalan truk pengiriman (*Delivery*) dan tukang rakit (*Installer*) terjadi di hari yang sama atau maksimal selisih $H+1$.
*   **Supplier Penalty & Double QC:** Menerbitkan penalti finansial kepada *supplier* kategori lemari dengan tingkat *Missing Parts* tertinggi, serta mewajibkan *Double QC* di gudang sebelum barang dikirim.

📱 **Transformasi Digital & Atribusi**
*   **O2O Promo Code Integration:** Menyediakan *Promo Code* atau *QR Code* khusus di setiap DEC fisik. Jika pelanggan mencoba produk di toko lalu *checkout* di rumah saat *Flash Sale*, sistem tetap mengatribusikan komisi penjualan kepada *Sales Consultant* terkait.

---

## 7. Contact
*   **Nama:** Avan Kantona Wongso
*   **E-Mail:** avanwongso@gmail.com
*   **Presentation Link:** https://drive.google.com/drive/folders/16rUi7tyszwvpeMQFsabav9z1Ix2V97bY?usp=drive_link
*   **Tableau Link:** https://public.tableau.com/views/DekorumaOmnichannelOperationalOptimization/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
