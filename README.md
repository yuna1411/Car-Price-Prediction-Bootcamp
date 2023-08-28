# Car-Price-Prediction-Bootcamp

Final project Bootcamp Data Scientist Rakamin Academy  
Dataset : Used Car Auction Price  
Latar belakang :  
- Kami adalah sebuah platform jual beli mobil online yang telah menganalisa bahwa terjadi ketidakseimbangan antara pertumbuhan revenue dan penjualan  
- Lebih dari separuh harga jual mobil berada di bawah standar MMR (acuan harga jual wholesale mobil bekas), mengakibatkan profit penjualan yang kurang optimal  
- Dibutuhkan standardisasi penentuan margin jual beli untuk meningkatkan profit perusahaan dan tetap memberikan harga yang fair kepada pelanggan  
- Solusinya adalah dengan mengembangkan model Machine Learning (ML) yang mampu menentukan harga rekomendasi yang dapat meningkatkan margin keuntungan yang adil, sehingga mendukung retensi pelanggan dan pertumbuhan bisnis.

-----
List fitur pada dataset adalah sebagai berikut :

Year : Tanggal produksi dari mobil.  
Make : Merk dari mobil.  
Model : Edisi dari tiap merk mobil.  
Trim : Versi trim dari mobil.  
Body : Tipe bentuk dari mobil.  
Transmission : Transmisi yang digunakan pada mobil.  
VIN : Vehicle Identification Number.  
State : Negara bagian tempat mobil dijual.  
Condition : Kondisi dari mobil pada saat dijual.  
Odometer : Jarak tempuh mobil semenjak tanggal manufacture.  
Color : Warna eksterior dari mobil.  
Interior : Warna interior dari mobil.  
Seller : Penjual dari mobil (Car dealers).   
**MMR : Manhiem Market Report, market yang memprediksi harga mobil.**  
Sellingprice : Nilai jual mobil.  
Saledate : Tanggal mobil dijual.  

## Summary Insight  

### Data Exploration  
1. Total dari data ada 558811 entries.  
2. Tipe dari data int, float dan object, dan terlihat sudah sesuai dengan kolomnya. Namun, untuk kolom 'saledate' tipe data yang awalnya 'object', dirasa perlu diubah ke date time.  
3. Terdapat 9 fitur yang memiliki null value, yaitu make, model, trim, body, transmission, condition, odometer, color, interior. 
4. Dataset tidak memiliki data duplikat sehingga tidak diperlukan penanganan.  
5. Nilai dari odometer terlihat memiliki jarak yang jauh antara min dan max dimana nilai min nya adalah 1 dan max nya hampir 1 juta. Tentu ini adalah hal yang terkesan janggal. Selain itu, nilai mean dan median nya juga terhitung sangat jauh yaitu 16000.  
6. Secara keseluruhan, nilai MMR dan sellingprice tidak terlalu berbeda. Namun, nilai min-max dan mean-median nya sangat jauh, sehingga perlu diperhatikan lebih lanjut untuk tahap berikutnya.


### EDA (Univariate Analysis)  
1. Beberapa kolom dari fitur numerical adalah right-skewed, terdapat juga kolom yang left-skewed.  
2. Banyak outliers dari fitur numerical sehingga akan perlu penanganan.  
3. Secara keseluruhan, untuk fitur kategorikal tidak memiliki masalah yang terlalu berat, hanya perlu melakukan simplify terhadap kategori yang terlalu banyak dan menyamaratakan upper/lower case untuk kategori yang sama.


### EDA (Multivariate Analysis)  
1. Fitur target (label) nya adalah MMR.  
2. Korelasi fitur numerik sangat bagus dan secara keseluruhan data, fitur numerik termasuk fitur-fitur yang paling penting dan relevan.
3. Selling price dan MMR menunjukkan korelasi yang paling tinggi. Kami juga sudah memvisualisasikan bagaimana memberikan pembanding antara selling price dari dataset asli yang menjadi goals kami dalam menciptakan selling price baru yang lebih baik. Sehingga, setelah model selesai dibuat harapannya adalah persentase ataupun visualisasi grafik dari selling price yang baru bisa lebih baik dari selling price yang lama.

![image](https://github.com/yuna1411/Car-Price-Prediction-Bootcamp/assets/89563587/9d3e2dac-5421-4e59-9b2e-935d0e9027d3)


### Data Cleansing  
**A. Dropping**
      1. Rows with extreme values  
          Menghapus baris-baris data yang memiliki extreme value seperti yang sudah ditemukan pada tahap EDA sebelumnya. Fitur-fitur tersebut adalah fitur odometer yang memiliki nilai 1 dan 999999 yang memiliki perbedaan yang sangat jauh, nilai selling price $1, dan nilai mmr $25 yang tidak masuk akal untuk ukuran harga sebuah mobil.  
      2. Irrelevant features  
          Menghapus fitur-fitur yang dianggap tidak memiliki korelasi dalam penentuan harga mobil.  
**B. Handle Unique Values**  
      Menyamaratakan penulisan string fitur-fitur kategorikal agar tidak memiliki value yang terduplikat.  
**C. Handle Missing Values**  
      1. Mengisi fitur kategorikal dengan nilai modus.  
      2. Mengisi fitur numerikal dengan nilai mean.  
      3. Menghapus baris yang mengandung sedikit null value. 
**D. Handle Outliers**  
      Menghapus outliers dikarenakan hanya kurang dari 3% dari keseluruhan dataset.  


### Data Preparation (Feature Engineering)  
**A. Feature Extraction**  
      1. Made in 
          Mengekstraksi fitur 'make' yaitu fitur yang mengandung merk atau brand mobil menjadi kategori berdasarkan asal negara pembuatnya.  
      2. Body type  
          Mengekstraksi fitur 'body' dengan menyederhanakan kategori body mobil menjadi lebih sederhana sesuai dengan tipe nya masing-masing. 
      3. Is Auto  
          Mengekstraksi fitur 'transmission' menjadi tipe data boolean dimana memberikan nilai True or False terhadap transmission berjenis automatic.  
      4. Model clusters  
          Mengekstraksi fitur 'model' menjadi beberapa macam klaster dengan menggunakan K-Modes.  
      5. Trim clusters  
          Mengekstraksi fitur 'trim' menjadi beberapa macam klaster dengan menggunakan K-Modes.  

**B. Feature Encoding**  
      1. One-Hot Encoding terhadap fitur Made in karena bukan termasuk data ordinal.  
      2. One-Hot Encoding terhadap fitur Body type karena bukan termasuk data ordinal.  

**C. Feature Selection**  
      Memilih fitur-fitur yang pada akhirnya akan digunakan untuk pemodelan.

