
#  **Airline Customer Value Analysis Case** 
---
## 📂 **Stage 0 : Problem Statement**
Sebuah perusahaan penerbangan sedang berupaya untuk mengidentifikasi karakteristik pelanggan melalui analisis dataset penerbangan yang komprehensif. Dari hasil analisis ini, perusahaan akan melakukan pengelolaan dan segmentasi pelanggan yang lebih efektif. Dengan segmentasi ini, perusahaan dapat memberikan layanan dan penawaran yang sesuai dengan masing-masing segmen pelanggan, guna mengoptimalkan bisnis penerbangan dan meningkatkan kepuasan pelanggan secara keseluruhan

<br>

---

## 📂 **Stage 1 : Exploratory Data Analysis**
### Dataset
<p align="center">
  Tabel 1 – Informasi Data <br>
</p>

<p align="center">
  
  ![data](https://github.com/user-attachments/assets/f71f80f1-9480-43fc-b8f4-1bdcc59c7ef4)

</p>

### Descriptive Statistics

<p align="center">
  Tabel 2  – Data Deskriptif Numerikal
</p>

<p align="center">
  
  ![data deskriptif numerikal](https://github.com/user-attachments/assets/84bb432c-5fa7-4590-a763-16261fef5cf3)

</p>

<br>

<p align="center">
   Tabel 3  – Data Deskriptive Kategori
</p> 

<p align="center">
  
  ![data deskriptif kategori](https://github.com/user-attachments/assets/a60a7f1b-c3f3-46b4-8617-e7c69ad38511)

</p>

<br>

### Insight Data Deskriptif : 

1. Dataset terdiri dari 22 kolom dan 62,988 baris. <br>
2. Terdapat nilai null pada 7 kolom. <br>
3. Tidak terdapat duplikat pada data. <br
4. MEMBER_NO dan avg_discount memiliki distribusi normal, sedangkan kolom lainnya menunjukkan distribusi positive skewed (Mean > Median). <br
5. Terdapat anomali pada kolom AGE dengan maksimal usia 110 tahun. <br>
6. GENDER didominasi oleh Male/laki-laki sebanyak 48,134.<br
7. WORK_COUNTRY didominasi oleh CN (Cina), WORK_PROVINCE terbanyak adalah Guangdong, dan WORK_CITY terbanyak adalah Guangzhou. <br>
8. Kolom FFP_DATE,FIRST_FLIGHT_DATE,LOAD_TIME,LAST_FLIGHT_DATE seharusnya tipe datanya adalah DateTime bukan Object. <br>
9. Terdapat terlalu banyak unique values pada fitur kategorikal WORK_CITY, WORK_PROVINCE, dan WORK_COUNTRY sehingga kemungkinan fitur-fitur ini bukan kandidat yang baik untuk clstering.  <br>
<br>

<br>

### Univariate Analisis : 
  
<p align="center">
  
![displot numerikal](https://github.com/user-attachments/assets/3fa855e3-6254-4582-be90-3e7c896d4318)
  Gambar 1 – Displot Numerikal 
</p>
<br>
<p align="center">
  
  ![violin numerikal](https://github.com/user-attachments/assets/ebfce3e3-08db-4ae0-b591-74176505d102)
  Gambar 2 – Violin Numerikal 
</p>
<br>
### Insight : 
1. MEMBER_NO memiliki unique values sebanyak jumlah baris sehingga kolom ini tidak akan dipakai selanjutnya. <br>
2. Distribusi pada kolom FFP_TIER mengindikasikan bahwa fitur ini merupakan fitur kategorikal. <br>
3. Kolom AGE dan avg_discount emmiliki distribusi data yang normal, sedangkan kolom lainya yang belum disebutkan diatas terlihat memiliki distribusi positive skewed.<br>
<br>

</p>
<p align="center">
  
  ![work kategori](https://github.com/user-attachments/assets/3c0a7abe-196e-4ab3-91ce-99f294bc3ec9)

  Gambar 3 - Region Work
</p>
<br>
<p align="center">
  
  ![flight date](https://github.com/user-attachments/assets/7d55735d-d97a-4758-b9e2-8b4ebc826202)

  Gambar 4 - Flight Date 
</p>
<br>
### Insight : 
1. Member mayoritas bekerja di CN (China), di provinsi Guang Dong, dan kota GuangZhou. <br>
1. Pada FIRST_FLIGHT_DATE terdapat value yang sangat jauh berbeda dengan values lainya yaitu tahun 1905. <br>
2. Total pendaftaran member terbanyak ada di tahun 2012. <br>
3. Penerbangan pertama dari member airlines juga ada di tahun 2012. <br>
<br>
</p>

### Multivariate Analisis : 
<p align="center">
  
 ![multivariate](https://github.com/user-attachments/assets/52491c66-1a52-4ccf-a623-705c26bf9794)

  Gambar 5 - Multivariate Numerikal
</p>
<br>
### Insight : 
### Insights:<br>
1. FFP_TIER memiliki korelasi positif kuat dengan Points_Sum, SEG_KM_SUM, SUM_YR_2, BP_SUM, dan FLIGHT_COUNT. <br>
2. AGE tidak memiliki korelasi kuat dengan fitur apapun. <br>
3. FLIGHT_COUNT memiliki korelasi positive kuat dengan Points_Sum, EXCHANGE_COUNT, SEG_KM_SUM, SUM_YR_1, SUM_YR_2, dan BP_SUM.<br>
4. Terdapat kemungkinan redundansi antara BP_SUM dengan Points_Sum dan SEG_KM_SUM. BP_SUM memiliki korelasi positive kuat dengan EXCHANGE_COUNT, SUM_YR_1, dan SUM_YR_2.<br>
5. SUM_YR_1 memiliki korelasi positive kuat dengan Points_Sum, SEG_KM_SUM, dan SUM_YR_2.<br>
6. SUM_YR_2 memiliki korelasi positive kuat dengan Points_Sum, dan SEG_KM_SUM. <br>
7. SEG_KM_SUM memiliki korelasi positif kuat dengan Points_Sum dan EXCHANGE_COUNT. <br>
8. AVG_INTERVAL memiliki korelasi positif kuat dengan MAX_INTERVAL. <br>
8. EXCHANGE_COUNT memiliki korelasi positif kuat dengan Points_Sum. <br>

<
<br>

## 📂 **Stage 2 : Data Pre-Processing**
<br>
1. Missing Value
   
  <p align="center">
    
    ![missing value](https://github.com/user-attachments/assets/f40bb826-6ffe-42fd-87f9-5153e41d2240)

   </p>
   <p align="center">
     Gambar 6- Handling missing values <br>
   </p>
<br>
<br>
2. Feature Engineering
       
    <p align="center">
    
    ![feature engineering](https://github.com/user-attachments/assets/764b2882-af4f-4556-a77b-0d9142ba3b42)

     </p>
   <p align="center">
     Gambar 7 - Feature Engineering <br>
   </p>
<br>
<br>
3. Feature Selection <br> 
</p>
Tujuan utama dalam mengklasifikasikan pelanggan berdasarkan karakteristik mereka dalam beberapa dimensi yang penting bagi bisnis untuk memahami dan mengelola interaksi dengan pelanggan. Dari landasan tersebut, berikut fitur yang dipilih untuk clustering: <br>

a. Fitur "LOYALTY" merepresentasikan Lenght: Jangka waktu keanggotaan pelanggan dari pertama kali mendaftar hingga periode observasi (semakin lama pelanggan menjadi anggota berarti pelanggan "loyal" atau semakin baik).<br>
b. Fitur "AVG_INTERVAL" merepresentasikan interval: Jangka waktu antara penerbangan (semakin kecil berarti pelanggan baru saja melakukan penerbangan, oleh karena itu semakin kecil semakin baik).<br>
c. Fitur "FLIGHT_COUNT" merepresentasikan Frequency: Jumlah penerbangan pelanggan dalam periode observasi (semakin besar semakin baik yang berarti pelanggan sering melakukan penerbangan).<br>
d. Fitur "SEG_KM_SUM" merepresentasikan jarak tempuh: Jumlah jarak yang ditempuh selama periode observasi (semakin jauh jarak tempuhnya maka akan semakin besar biaya yang dibayarkan oleh customer). <br>

<br>
<br>
4. Handling Outliers <br>

    Fitur 'FLIGHT_COUNT', 'SEG_KM_SUM', dan 'AVG_INTERVAL' terlihat memiliki outliers akan ditangani dengan metode IQR. 
<br>
 <p align="center">
   
   ![handling outlier](https://github.com/user-attachments/assets/ec5f5bf5-c665-4939-94eb-07486bd73d74)

   </p>
   <p align="center">
     Gambar 8 - Handling Outlier <br>
   </p>

<br>
5. Standardization <br>

  <p> 
  <p align="center">
    
    ![standardization](https://github.com/user-attachments/assets/713b4855-bdcd-4a9d-9faa-885d1ab55bca)

   </p>
   <p align="center">
     Gambar 9 - Handling Outlier <br>
   </p>
   </p>
<br>
 

## 📂 **Stage 3 : Modelling**

### **Elbow Method**

  <p> 
  <p align="center">
    
    ![Elbow](https://github.com/user-attachments/assets/242b2bfa-58be-4985-a53c-d9c8cd2bf409)

     </p>
   <p align="center">
     Gambar 10 - Elbow Method <br>
   </p>
   <br>
   Dari Elbow graph diatas terlihat bahwa setelah titik ke 4 (k=5), pengurangan inertia mulai kurang signifikan. <br>
   Oleh karena itu, k = 5 menjadi titik optimal untuk pengelompokan berdasarkan analisis diatas.
   <br>

### **K-Means Clustering**

  <p> 
  <p align="center">
    
    ![kmeans](https://github.com/user-attachments/assets/d76e4308-c6e1-40d6-ab6b-836725833c65)

   </p>
   <p align="center">
     Gambar 11 - Kmeans Clustering
   </p>
   </p>
<br>

### **Principal Component Analysis (PCA)**

  <p> 
  <p align="center">
    
    ![pca](https://github.com/user-attachments/assets/01a42676-37ee-4875-9507-c44622f8f9e7)

   </p>
   <p align="center">
     Gambar 12 - Principal Component Analysis (PCA)
   </p>
   </p>
<br>
Berdasarkan hasil PCA : <br>
1. Terdapat titik-titik dari kelas yang berbeda terpisah dengan jelas di plot, ini menunjukkan bahwa model dapat membedakan kelas-kelas tersebut dengan baik. <br>
2. Titik yang berdekatan menunjukkan kemiripan antara observasi, sedangkan titik yang jauh menunjukkan perbedaan signifikan antara observasi. <br>
<br>
<p>

### **Customer Count and Observe the Value of Feature in Cluster**
    
  <p align="center">
    
    ![total customer](https://github.com/user-attachments/assets/9e461e50-9fb1-41b5-b461-1eb46bf7c1c7)

   </p>
   <p align="center">
     Gambar 13 - Total Customer per Cluster
   </p>
   </p>
<br>
 <p align="center">
   
   ![clustering](https://github.com/user-attachments/assets/e4a762f0-b60a-4565-8729-0cda0a609688)

   </p>
   <p align="center">
     Gambar 
    14 - Value of Feature in each Cluster
   </p>
   </p>

### **Business Insight and Recomendations:**
<br>
1. **Cluster 0 (_Inexperienced Flyers_):**
   - Pelanggan dalam cluster ini adalah anggota baru dari program maskapai.
   - Mereka belum melakukan banyak penerbangan, meskipun interval rata-rata antar penerbangan mereka singkat.
   - Pelanggan dalam cluster ini mungkin termasuk individu yang baru mulai menjelajahi atau menggunakan layanan penerbangan, seperti mahasiswa atau orang-orang yang baru memulai karir profesional.

2. **Cluster 1 (_Rare Flyers_):**
   - Pelanggan dalam cluster ini sudah menjadi anggota lebih lama daripada Cluster 0, namun jumlah penerbangan dan jarak yang mereka tempuh masih sedikit.
   - Interval rata-rata antar penerbangan mereka paling tinggi di antara cluster lainnya, menunjukkan bahwa mereka jarang melakukan penerbangan.
   - Pelanggan dalam cluster ini mungkin terdiri dari individu yang hanya melakukan perjalanan pribadi atau liburan jangka panjang yang jarang terbang, atau mereka yang memilih untuk menggunakan moda transportasi lain.

3. **Cluster 2 (_Infrequent Flyers_):**
   - Pelanggan dalam cluster ini merupakan yang paling lama menjadi anggota dibandingkan dengan cluster lainnya.
   - Meskipun durasi keanggotaannya lama, mereka masih melakukan penerbangan dengan jumlah dan jarak yang tergolong sedikit.
   - Interval rata-rata antar penerbangan mereka moderat, menunjukkan bahwa mereka melakukan perjalanan secara sporadis atau hanya pada kesempatan tertentu.
   - Pelanggan dalam cluster ini mungkin terdiri dari individu yang lebih memilih untuk bepergian hanya pada waktu-waktu khusus, seperti liburan tahunan atau perjalanan bisnis yang jarang.

4. **Cluster 3 (_Regular Flyers_):**
   - Pelanggan dalam cluster ini adalah yang baru-baru ini menjadi anggota, tetapi mereka melakukan penerbangan dengan jumlah yang lebih banyak dibandingkan dengan rata-rata.
   - Total jarak yang mereka tempuh juga cukup signifikan.
   - Interval rata-rata antar penerbangan mereka moderat, menunjukkan bahwa mereka melakukan perjalanan secara teratur, mungkin untuk kepentingan bisnis atau pekerjaan.
   - Pelanggan dalam cluster ini mungkin terdiri dari pebisnis atau profesional yang melakukan perjalanan rutin untuk pertemuan bisnis atau pekerjaan.

5. **Cluster 4 (_Frequent Flyers_):**
   - Pelanggan dalam cluster ini adalah yang paling lama menjadi anggota kedua setelah Cluster 2.
   - Mereka melakukan jumlah penerbangan dan total jarak tempuh yang paling tinggi dibandingkan dengan cluster lainnya.
   - Interval rata-rata antar penerbangan mereka singkat, menunjukkan bahwa mereka sering melakukan perjalanan udara.
   - Pelanggan dalam cluster ini mungkin terdiri dari eksekutif bisnis yang sering melakukan perjalanan internasional atau nasional, atau mungkin pelancong yang sering bepergian untuk liburan atau kegiatan rekreasi lainnya.

<br>

### Rekomendasi Bisnis untuk Setiap Cluster:

1. **Cluster 0 (_Inexperienced Flyers_):**
   - **Rekomendasi Bisnis:** Berikan penawaran khusus untuk memikat pelanggan baru, seperti diskon untuk penerbangan pertama mereka atau poin bonus saat mendaftar. Fokuskan pada layanan yang mudah dipahami dan jangan terlalu rumit karena mereka baru mengenal layanan penerbangan.

2. **Cluster 1 (_Rare Flyers_):**
   - **Rekomendasi Bisnis:** Tawarkan paket liburan jangka panjang atau promosi spesial untuk destinasi tertentu yang jarang dikunjungi. Berikan fleksibilitas dalam reservasi dan penawaran istimewa untuk meningkatkan minat mereka dalam bepergian lebih sering.

3. **Cluster 2 (_Infrequent Flyers_):**
   - **Rekomendasi Bisnis:** Buat program loyalitas yang menarik dengan poin atau penghargaan yang dapat dikumpulkan dari setiap penerbangan. Tawarkan paket liburan atau kebijakan fleksibel yang memungkinkan mereka merencanakan perjalanan jangka panjang atau liburan secara efektif.

4. **Cluster 3 (_Regular Flyers_):**
   - **Rekomendasi Bisnis:** Fokuskan pada layanan premium dan keuntungan bisnis yang cepat, seperti akses prioritas, lounge bandara eksklusif, atau pelayanan pelanggan yang unggul. Tawarkan program loyalitas yang memberikan nilai tambah dan kenyamanan bagi pelanggan yang sering melakukan perjalanan.

5. **Cluster 4 (_Frequent Flyers_):**
   - **Rekomendasi Bisnis:** Tingkatkan layanan eksklusif untuk pelanggan yang sering terbang, seperti upgrade otomatis, akses lounge VIP global, atau kesempatan eksklusif untuk pengalaman perjalanan yang lebih mewah. Tawarkan kebijakan fleksibel yang mengakomodasi perjalanan sering mereka.

---

#### Sumber
Caruana, R. & Niculescu-Mizil, A., 2006. An empirical comparison of supervised learning algorithms. Proceedings of the 23rd International Conference on Machine Learning, pp.161-168. doi: 10.1145/1143844.1143865. <br>
Powers, D. M., 2011. Evaluation: From Precision, Recall and F-Measure to ROC, Informedness, Markedness & Correlation. [online] Available at: https://doi.org/10.48550/arXiv.2010.16061 [Accessed 16 July 2024].
