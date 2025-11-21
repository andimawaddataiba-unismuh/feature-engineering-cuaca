Tugas Feature Engineering – Dataset Cuaca (Open-Meteo)

Repository ini dibuat sebagai dokumentasi pengerjaan tugas Feature Engineering pada mata kuliah Applied Machine Learning EHPT2. Seluruh proses mulai dari membaca dataset, melakukan preprocessing, hingga membuat fitur-fitur baru dicatat dalam notebook dan dijelaskan secara ringkas pada halaman ini.

📌 1. Deskripsi Dataset

Dataset yang digunakan berjudul Dataset Cuaca.xlsx, yang berisi data hasil pengambilan dari layanan Open-Meteo. Data tersebut memuat informasi cuaca per jam dengan beberapa variabel utama, yaitu:

temperature_2m – suhu udara

relative_humidity_2m – kelembapan relatif

precipitation – curah hujan

wind_speed_10m – kecepatan angin

cloud_cover – tutupan awan

time – waktu pengamatan

Dataset ini menjadi dasar untuk proses feature engineering, karena variabel-variabel tersebut mewakili kondisi cuaca yang dapat dianalisis maupun diprediksi.

📌 2. Tahap Preprocessing (Ringkasan)

Sebelum masuk ke feature engineering, dataset terlebih dahulu dibersihkan untuk memastikan datanya layak untuk dipakai. Tahap preprocessing yang dilakukan meliputi:

• Pengecekan Missing Value

Semua kolom dicek menggunakan fungsi df.isnull().sum(). Berdasarkan hasilnya, tidak ditemukan nilai kosong pada dataset.

• Penanganan Missing Value

Karena tidak ada data yang hilang, tahap imputasi tidak diperlukan. Namun metode median tetap disiapkan apabila suatu saat dataset diperluas.

• Penanganan Outlier (IQR/Winsorization)

Beberapa variabel numerik memiliki nilai ekstrem. Outlier ditangani menggunakan metode IQR dengan cara melakukan capping nilai maksimum dan minimum agar distribusi data lebih stabil.

• Scaling Fitur Numerik

Fitur-fitur seperti suhu, kelembapan, curah hujan, kecepatan angin, dan tutupan awan dinormalisasi menggunakan StandardScaler. Tujuannya agar seluruh fitur berada pada skala yang sebanding dan siap masuk ke tahap pemodelan.

Seluruh proses detailnya ada pada file:
➡ preprocessing_feature_engineering.ipynb

📌 3. Tahap Feature Engineering (Fokus Tugas Minggu Ini)

Pada tahap ini dilakukan pembuatan beberapa fitur baru dari data cuaca yang sudah bersih. Fitur-fitur ini dirancang agar model machine learning lebih mudah menemukan pola dari data.

✔ 1. Fitur rain_status

Fitur ini dibuat untuk mengubah curah hujan menjadi informasi biner:

1 = hujan

0 = tidak hujan
Fitur ini nantinya dapat dipakai sebagai label atau menjadi variabel tambahan dalam prediksi cuaca.

✔ 2. Ekstraksi Fitur Waktu

Kolom waktu dipecah menjadi beberapa informasi yang lebih detail:

jam (hour)

tanggal (day)

bulan (month)

hari ke berapa dalam seminggu (weekday)

Pemecahan ini membantu dalam melihat pola cuaca berdasarkan waktu, misalnya perubahan kelembapan di pagi hari atau peningkatan curah hujan pada bulan tertentu.

✔ 3. Fitur heat_index

Heat index digunakan untuk mengukur seberapa panas kondisi udara berdasarkan kombinasi suhu dan kelembapan. Fitur ini lebih menggambarkan “panas yang dirasakan manusia” dibandingkan hanya melihat suhu.

✔ 4. Fitur wind_pressure

Fitur ini merupakan turunan dari kecepatan angin. Tekanan angin dihitung secara sederhana sebagai indikator kondisi angin yang lebih informatif daripada kecepatan saja.

✔ 5. Fitur Interaksi (temperature × humidity)

Interaksi antara suhu dan kelembapan dapat memengaruhi kenyamanan dan juga kondisi cuaca. Fitur ini dibuat untuk membantu model memahami hubungan antar variabel.

✔ 6. Scaling Fitur Baru

Semua fitur baru dinormalisasi menggunakan StandardScaler agar skala datanya seragam dengan fitur lama.

📌 4. Screenshot Proses Feature Engineering

Seluruh screenshot hasil menjalankan kode (df.head, missing value, outlier, scaling, rain_status, heat_index, dst.) terdapat dalam laporan tugas yang dikumpulkan terpisah.

📌 5. Notebook Kode Lengkap

Proses lengkap dari awal hingga akhir dapat dilihat di file berikut:

➡ Data_Feature_Engginering_Notebook.ipynb

📌 6. Hasil Akhir

Dataset akhir dengan seluruh fitur baru telah disimpan dalam file:

dataset_feature_engineering.xlsx

File ini siap digunakan untuk tahap analisis atau pemodelan machine learning berikutnya.
