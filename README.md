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




