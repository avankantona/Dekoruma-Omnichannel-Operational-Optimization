# Dekoruma-Omnichannel-Operational-Optimization

🛋️ Dekoruma O2O Optimization & Omnichannel Attribution

## 1. Project Overview
Proyek ini menganalisis histori transaksi dan data operasional **Dekoruma** periode tahun 2023 untuk mengidentifikasi celah operasional yang menguras margin, mengevaluasi sinkronisasi logistik pengiriman dan perakitan *Bulky Goods*, serta mengungkap fenomena atribusi penjualan *omnichannel* (*showrooming*).
Fokus utamanya adalah bagaimana pemahaman terhadap perilaku konsumen dan siklus rantai pasok (*supply chain*) dapat dimanfaatkan untuk menekan biaya retur logistik yang tinggi serta meningkatkan kepuasan pelanggan secara signifikan.

🎯 **Key Objectives:**
*   **Objective 1:** Menganalisis *lead time* (selisih waktu) antara barang tiba di rumah pelanggan dan kedatangan tim perakit (*installer*).
*   **Objective 2:** Mengidentifikasi kategori furnitur dan *supplier* yang paling sering mengalami kegagalan perakitan (*Failed Installation*) akibat komponen hilang atau rusak.
*   **Objective 3:** Mengungkap fenomena *showrooming* antara Dekoruma Experience Center (DEC) fisik dan aplikasi digital untuk atribusi komisi penjualan yang adil.

---

## 2. Data Sources
*   **Dataset 1 (`dekoruma_stores`):** Data dimensi saluran penjualan (*Physical Store, Mobile App, Web*).
*   **Dataset 2 (`dekoruma_products`):** Data dimensi produk, mencakup kategori dan syarat perakitan furnitur.
*   **Dataset 3 (`dekoruma_orders`):** Data fakta transaksi sebanyak 300.000 baris, memuat ID tukang, tanggal kirim & rakit, status kegagalan, hingga biaya perakitan (*assembly fee*).

---

## 3. Technologies Used
*   **Programming Language:** Python (Pandas, NumPy)
*   **Database & Query:** MySQL, SQLAlchemy, PyMySQL
*   **Visualization:** Matplotlib, Seaborn, Tableau
*   **Environment:** Jupyter Notebook

---

## 4. Project Structure
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

📊 **5. Summary of Findings**

💡 **5.1 Business Insights**
*Note: Analisis dilakukan berdasarkan 300.000 data transaksi histori pesanan dengan fokus pada efisiensi operasional dan sinkronisasi logistik.*

| Aspek | Temuan Utama | Dampak Bisnis |
| :--- | :--- | :--- |
| **Waktu Tunggu (Lead Time)** | **Jeda Waktu ~2.5 Hari:** Rata-rata pelanggan harus menunggu selama **2.51 hari** sejak barang tiba hingga dirakit oleh *installer*. | Rumah pelanggan dipenuhi tumpukan kardus *flat-pack*, memicu komplain dan tingginya risiko pembatalan pesanan (*post-purchase trauma*). |
| **Kualitas Supplier (QC)** | **Dominasi Kategori Lemari:** Kategori *Wardrobe/Lemari* mencatatkan angka kegagalan instalasi tertinggi, didominasi alasan *Missing Parts* (baut/komponen kurang dari pabrik). | Perusahaan menanggung biaya retur logistik *bulky goods* yang sangat mahal akibat kelalaian *quality control* pihak *supplier*. |
| **Atribusi Omnichannel** | **Kontribusi DEC Fisik:** Toko fisik secara individual mencatatkan volume transaksi yang sangat kuat, bersaing ketat dengan kanal digital. | Indikasi kuat adanya fenomena *showrooming* (pelanggan melihat produk fisik di DEC namun melakukan *checkout* via aplikasi). |
| **Integritas Data** | **Logical Error & Outliers:** Ditemukan 4.570 data pesanan yang tercatat dirakit sebelum barang dikirim, serta 909 *outliers* pada biaya perakitan. | Kesalahan input manual (*human error*) dan inkonsistensi kategori produk dapat menyesatkan arah kebijakan manajemen jika tidak dibersihkan. |

---

🚀 **5.2 Actionable Recommendations**

📈 **Strategi Operasional & Logistik**
*   **SLA Sync Maksimal 24 Jam:** Membangun *rules* sistem IT yang mewajibkan penjadwalan truk pengiriman (*Delivery*) dan tukang rakit (*Installer*) terjadi di hari yang sama atau maksimal selisih $H+1$.
*   **Supplier Penalty & Double QC:** Menerbitkan penalti finansial kepada *supplier* kategori lemari dengan tingkat *Missing Parts* tertinggi, serta mewajibkan *Double QC* di gudang sebelum barang dikirim.

📱 **Transformasi Digital & Atribusi**
*   **O2O Promo Code Integration:** Menyediakan *Promo Code* atau *QR Code* khusus di setiap DEC fisik. Jika pelanggan mencoba produk di toko lalu *checkout* di rumah saat *Flash Sale*, sistem tetap mengatribusikan komisi penjualan kepada *Sales Consultant* terkait.

---

## 6. Contact
*   **Nama:** Avan Kantona Wongso
*   **E-Mail:** avanwongso@gmail.com
*   **Presentation Link:** https://drive.google.com/drive/folders/16rUi7tyszwvpeMQFsabav9z1Ix2V97bY?usp=drive_link
*   **Tableau Link:** https://public.tableau.com/views/DekorumaOmnichannelOperationalOptimization/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
