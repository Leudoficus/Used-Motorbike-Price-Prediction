# Used-Motorbike-Price-Prediction
Di portofolio kali ini saya mencoba memprediksi harga jual motor bekas menggunakan dataset Used Price Honda 2016. Dataset ini merupakan daftar stock unit konsumen gagal bayar yang sudah diakuisisi perusahaan pembiayaan keuangan. Singkat cerita, akhirnya unit-unit ini akan di distribusi di kemudian hari untuk mengurangi kerugian perusahaan.
Untuk itu, saya mencoba untuk memprediksi harga jual motor bekas menggunakan dataset ini menggunakan metode Linier regression sebagai baseline modelnya. Selanjutnya menggunakan beberapa metode lainnya seperti Lasso, Ridge, Decision Tree Regressor, Random Forest Regressor, Gradient Boosting Regressor, K-Neighbors Regressor. Dan pada akhirnya mendapatkan model terbaik menggunakan metode Gradient Boosting Regressor untuk memprediksi harga jual motor bekas.

## **Exploratory Data Analisys**
saya menganalisa ada beberapa point penting sebelum di lakukan modelling. diantaranya adalah :
1. Fitur CATEGORY, BRAND MODEL TYPE, MODEL, TYPE, CODE ENGINE ternyata sudah terwakili oleh fitur **GROUP MODEL TYPE**, sehingga pada bagian selanjutnya pada fitur CATEGORY, BRAND MODEL TYPE, MODEL, TYPE, CODE ENGINE akan saya buang.
2. **DOCUMENT** dengan **STNK Y** memiliki average SOLD PRICE lebih tinggi daripada STNK N walaupun perbedaan tidak terlalu signifikan. baik itu di CONDITION GRADE A,B,C,D.
3. pada **CONDITION GRADE 'D'** di tahun 2011-2013 tidak ada perbedaan **SOLD PRICE** yang signifikan. Dan usia kendaraan di tahun ke-5 & ke-6 (tahun 2010-2011), perbedaan **SOLD PRICE** antara **CONDITION GRADE 'C' & 'D'** juga tidak signifikan. Kemungkinan besar dikarenakan tingkat kerusakan yang tinggi. Sehingga pembeli tidak memperhitungkan harga pasar, tetapi lebih banyak memperhitungkan harga spare part, dan biaya jasa perbaikan yang tinggi.
4. sebaliknya untuk usia kendaraan belum 1 tahun (tahun 2016), **CONDITION GRADE** tidak terlalu mempengaruhi **SOLD PRICE** kecuali unit yang kondisinya sangat jelek (CONDITION GRADE 'D').
5. Pada scatter plot yang saya buat, **CONDITION GRADE 'A'** memiliki karakter **LOST PART** yang lebih kecil dibandingkan Grade B selanjutnya grade C dan D, selain itu juga memiliki **SOLD PRICE** yang cenderung lebih tinggi dibandingkan condition grade B selanjutnya C dan D.
6. fitur **MARKET PRICE, NEW PRICE, SOLD PRICE MINIMUM** memiliki karakter yang sama terhadap fitur **SOLD PRICE**. Secara linier, semakin tinggi MARKET PRICE, NEW PRICE, SOLD PRICE MINIMUM semakin tinggi pula SOLD PRICE yang terbentuk sesuai dengan kondisi motor dengan grade A cenderung berada pada posisi SOLD PRICE lebih tinggi, grade B cenderung lebih rendah dari pada grade B dan seterusnya pada grade C & D.

## Kesimpulan
### 1. Insight :
Berdasarkan model Analysis,
- fitur **NEW PRICE** menjadi fitur yang paling berpengaruh terhadap prediksi **SOLD PRICE**.
- fitur **YEAR** menjadi fitur berpengaruh kedua terhadap prediksi **SOLD PRICE**.
- fitur **LOST PART, GROUP MODEL TYPE, CONDITION GRADE** masih berpengaruh terhadap prediksi **SOLD PRICE** tapi tidak terlalu signifikan jika dibandingkan dengan fitur NEW PRICE dan YEAR.
- sedangkan fitur **DOCUMENT** sedikit sekali pengaruhnya terhadap fitur **SOLD PRICE**.
- hasil tuning hyperparameter dengan model **Gradient Boosting Regressor** memiliki nilai **Mean Average Error** sebesar **709166.0635159286**. yang artinya terdapat margin error sebesar +- 709.166,06 poin terhadap hasil prediksi.
- sedangkan nilai **R2 Score** sebesar **0.9159404231650905**. yang artinya prediksi SOLD PRICE menggunakan model Gradient Boosting Regressor bisa diprediksi dengan akurasi hingga 91,59%.

### 2 Recomendations :
- untuk memprediksi **SOLD PRICE** motor bekas, stake holder wajib memperhatikan dan wajib memiliki referensi Harga Baru (**NEW PRICE**) model dan tipe motor yang akan dijual.
- setelah itu, Tahun Produksi (**YEAR**) menjadi parameter kedua yang harus diperhatikan pada saat memprediksi **SOLD PRICE** motor bekas.
- sedangkan Kondisi motor (**CONDITION GRADE**) dan **model tipe** motor hanya menjadi faktor pendukung untuk memprediksi **SOLD PRICE**.
