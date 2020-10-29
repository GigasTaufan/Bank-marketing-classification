# Bank Marketing Campaign Classification

Tugas Minggu-5 Digital Talent Incubator - Telkom

Nama: Gigas Taufan Arvyanto (DS0210)

Source Code: [Classification](https://colab.research.google.com/drive/1q_zy0LK2mbEw3FOZx5nu_t6x17n2YZ6V?usp=sharing)

## 1. Identifikasi Masalah 

Diberikan sebuah data milik suatu bank yang berisikan kampanye pemasaran. Data tersebut berisikan kampanye langsung melalui sambungan telepon kepada nasabah bank. Melalui data tersebut akan dilakukan prediksi apakah seseorang akan melakukan Deposit ke dalam bank.

Data terdiri dari 11162 baris dengan 17 kolom atribut. Berikut adalah atribut-atribut yang terdapat pada dataset:

1. age: usia calon nasabah 
2. job: pekerjaan calon nasabah 
3. marital: status pernikahan nasabah (married, single, divorce)
4. education: tingkat pendidikan nasabah (secondary, primary, tertiary,unknown)
5. default: apakah memiliki kredit secara default atau tidak? (yes, no)
6. balance: jumlah saldo 
7. housing: apakah memiliki cicilan rumah atau tidak? (yes, no)
8. loan: apakah memiliki pinjaman pribadi atau tidak? (yes, no)
9. contact: tipe kontak komunikasi yang digunakan (telephone, cellular, unknown)
10. day: terakhir dihubungi pada hari ke berapa
11. month: terakhir dihubungi pada bulan apa dalam satu tahun (januari - desember)
12. duration: lama durasi dihubungi dalam detik
13. campaign: jumlah kontak yang dilakukan selama kampanye ini dan untuk nasabah ini
14. pdays: jumlah hari yang berlalu setelah klien terakhir kali dihubungi dari kampanye sebelumnya
15. previous: jumlah kontak yang dilakukan sebelum kampanye ini dan untuk nasabah ini
16. poutcome: hasil dari kampanye pemasaran sebelumnya
17. deposit: atribut kelas dan untuk mengetahui apakah nasabah melakukan melakukan deposit atau tidak (yes, no)

![dataset](/img/1.png)


---


## 2. Exploratory Data Analysis

![info](/img/2.png)

Terdapat 2 tipe data yakni data bertipe objek dan numerik
- Bertipe numerik: age, balance, day, duration, campaign, pdays, previous
- Bertipe objek: job, marital, education, default, housing, loan, contact, month, poutcome, deposit

### 2.1. Hubungan Atribut Dengan Kelas
Atribut kategorikal dan numerik akan dilihat hubungannya dengan kelas. Tujuannya adalah untuk mendapat informasi 
lebih jauh dari data yang dimiliki. Berikut adalah grafik dari atribut deposit:

![yes&no](/img/3 deposit.png)

Deposit dengan kategori "yes" adalah nasabah yang melakukan deposit memiliki jumlah 5289, dan kategori "no" adalah nasabah yang tidak melakukan deposit dengan jumlah 5873 .

#### 2.1.1. Data Tipe Kategorikal
Berikut adalah hubungan dari setiap atribut yang memiliki tipe kategorikal dengan atribut deposit:

##### a. Job - Deposit

![jobdeposit](/img/4-job-deposit.png)

Atribut job memiliki data sebagai berikut:
- management       2566
- blue-collar      1944
- technician       1823
- admin.           1334
- services          923
- retired           778
- self-employed     405
- student           360
- unemployed        357
- entrepreneur      328
- housemaid         274
- unknown            70

![jobdeposit](/img/5-job-deposit-yes&no.png)

Dari data bidang pekerjaan yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Nasabah yang berprofesi management jumlah nasabah yang melakukan deposit paling tinggi di antara profesi lainnya, namun juga paling tinggi tidak melakukan deposit. 
- Nasabah yang berprofesi blue-colar, jumlah nasabah yang tidak melakukan deposit jauh lebih banyak darioada yang melakukan deposit. Dapat diasumsikan jika nasabah yang berprofesi blue-collar memiliki kecenderungan untuk tidak melakukan deposit atas kampanye marketing yang diadakan.
- Nasabah yang berprofesi retired, jumlah nasabah yang melakukan deposit lebih banyak daripada nasabah yang tidak melakukan deposit. Dapat diasumsikan jika nasabah yang berprofesi retired memiliki kecenderungan untuk akan melakukan deposit atas kampanye marketing yang diadakan.

##### b. Marital - Deposit

![maritaldeposit](/img/6-marital-deposit.png)

Aribut marital memiliki data sebagai berikut:
- married     6351
- single      3518
- divorced    1293

![maritaldeposit](/img/6-marital-deposit-yes&no.png)

Dari data status pernikahan yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Nasabah yang memiliki status menikah jumlah tidak melakukan deposit lebih tinggi dibanding yang melakukan. Dapat diasumsikan jika nasabah yang status pernikahannya married memiliki kecenderungan untuk tidak melakukan deposit atas kampanye marketing yang diadakan.

##### c. Education - Deposit

![educationdeposit](/img/7-education-deposit.png)

Atribut education memiliki data sebagai berikut:
- secondary    5476
- tertiary     3689
- primary      1500
- unknown       497

![educationdeposit](/img/7-education-deposit-yes&no.png)

Dari data tingkat pendidikan yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Selisih untuk yang melakukan dan tidak melakukan deposit pada setiap tingkat pendidikan tidak terlalu besar.
- Nasabah yang memiliki tingkat pendidikan secondary dan primary jumlah tidak melakukan deposit lebih tinggi daripada yang melakukan. 
- Nasabah yang memiliki tingkat pendidikan pendidikan tertiary jumlah yang melakukan deposit lebih tinggi daripada yang melakukan. 

##### d. Default - Deposit

![defaultdeposit](/img/8-default-deposit.png)

Atribut default memiliki data sebagai berikut:
- no     10994
- yes      168

![defaultdeposit](/img/8-default-deposit-yes&no.png)

Dari data atribut default yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Nasabah yang tidak memiliki kredit secara default memiliki jumlah lebih tinggi daripada yang memiliki kredit secara default. Selisih antara nasabah yang melakukan deposit dan tidak melakukan deposit juga tidak terlalu tinggi. Dengan yang tidak melakukan deposit lebih banyak daripada yang melakukan deposit.

##### e. Housing - Deposit

![housingdeposit](/img/9-housing-deposit.png)

Atribut housing memiliki data sebagai berikut: 
- no     5881
- yes    5281

![housingdeposit](/img/9-housing-deposit-yes&no.png)

##### f. Loan - Deposit

![loandeposit](/img/10-loan-deposit.png)

Atribut loan memiliki data sebagai berikut:
- no     9702
- yes    1460

![loandeposit](/img/10-loan-deposit-yes&no.png)

Dari data atribut loan yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Nasabah yang tidak mempunyai pinjaman pribadi jumlahnya lebih tinggi daripada yang memiliki pinjaman pribadi. Selisih antara nasabah yang melakukan deposit dan tidak melakukan deposit juga tidak terlalu tinggi. Dengan yang tidak melakukan deposit lebih banyak daripada yang melakukan deposit, walau tipis selisihnya.

##### g. Contact - Deposit

![contactdeposit](/img/11-contact-deposit.png)

Atribut contact memiliki data sebagai berikut:
- cellular     8042
- unknown      2346
- telephone     774

![contactdeposit](/img/11-contact-deposit-yes&no.png)

Dari data atribut contact yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:

- Nasabah yang dihubungi melalui seluler jauh lebih banyak daripada yang melalui telepon biasa.
- Nasabah yang tidak diketahui cara dihubunginya melalui jalur apa, jumlah yang tidak melakukan deposit lebih banyak daripada yang melakukan dengan selisih yang cukup banyak. Dapat diasumsikan jika nasabah yang tidak diketahui cara dihubunginya ini akan tidak melakukan deposit

##### h. Month - Deposit

![monthdeposit](/img/12-month-deposit.png)

Atribut month memiliki data sebagai berikut:
- may    2824
- aug    1519
- jul    1514
- jun    1222
- nov     943
- apr     923
- feb     776
- oct     392
- jan     344
- sep     319
- mar     276
- dec     110

![monthdeposit](/img/12-month-deposit-yes&no.png)

Dari data atribut month yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:

- Nasabah paling banyak dihubungi pada Mei. Nasabah juga paling banyak tidak melakukan deposit pada bulan Mei. 
- Pada bulan Mei, Agustus, Juli, Juni, November, dan Januari, nasabah lebih banyak yang tidak melakukan deposit
- Pada bulan April, Februaru, Oktober, September, Maret, dan Desember. 

##### i. Poutcome - Deposit

![poutcomedeposit](/img/13-poutcome-deposit.png)

Atribut poutcome memiliki data sebagai berikut:
- unknown    8326
- failure    1228
- success    1071
- other       537

![poutcomedeposit](/img/13-poutcome-deposit-yes&no.png)

Dari data atribut poutcome yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Nasabah yang tidak diketahui hasil dari kampanye sebelumnya (unknown) memiliki jumlah paling banyak. Dapat diasumsikan bahwa mayoritas data merupakan nasabah yang baru pertama kali dihubungi atas suatu kampanye dari bank.
- Nasabah yang berada pada kategori unknown memiliki jumlah yang tidak melakukan deposit lebih banyak daripada yang melakukan deposit, dengan selisih yang banyak.
- Nasabah yang pada kampanye sebelumnya sukses (success) memiliki jumlah yang melakukan deposit lebih banyak daripada yang tidak. Selisihnya juga cukup banyak dan dapat diasumsikan jika pada kampanye sebelumnya dia menerima penawaran maka pada kampanye selanjutnya akan menerima penawaran tersebut. 

#### 2.1.2. Data Tipe Numerik
Berikut adalah deskripsi dari setiap atribut yang memiliki tipe numerik:

![numerikstatistik](/img/14numerik-statistik.png)

Berdasarkan deskripsi data yang ditampilkan di atas, atribut pdyas memiliki nilai minimal quartil bawah dan median = -1. Atribut pdays seharusnya tidak memiliki nilai -1 karena berisikan jumlah hari. Bisa dianggap ada bahwa nilai -1 merupakan noise.
Jumlahnya mencapai 8324. Jumlah tersebut sama dengan 74% dari total data. Atribut pdays dapat dihapus karena noise yang terlalu besar.

##### a. Age - Deposit

Berikut adalah data terkait dengan age dan deposit: 

![agedeposit](/img/15-age-deposit.png)

![agedeposit](/img/15-age-deposit-yes&no.png)

Dari data atribut age yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Rata-rata usia dari nasabah yang dihubungi baik yang melakukan deposit ataupun yang tidak hampir sama di 40 tahunan. Usia termuda yang melakukan deposit sama-sama 18 tahun, dan untuk nasabah yang melakukan deposit tertua berusia 95 tahun, sedangkan yang tidak melakukan deposit tertua berusia 89 tahun.

##### b. Balance - Deposit
Berikut adalah data terkait dengan balance dan deposit: 
![balancedeposit](/img/16-balance-deposit.png)

![balancedeposit](/img/16-balance-deposit-yes&no.png)

Dari data atribut balance yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Terdapat nasabah yang memiliki balance atau jumlah saldo bernilai negatif, baik untuk yang tidak melakukan deposit ataupun yang melakukan. Dengan masing-masing bernilai -3058 untuk data nasabah yang melakukan deposit dan -6847 untuk yang tidak melakukan deposit.
- Rata-rata jumlah saldo untuk nasabah yang masuk dalam kategori melakukan deposit lebih besar daripada yang tidak melakukan yakni sebesar 1804.2679.
- Rata-rata jumlah saldo untuk nasabah yang masuk dalam kategori tidak melakukan deposit adalah sebesar 1280.2271.

##### c. Day - Deposit
Berikut adalah data terkait dengan day dan deposit: 

![daydeposit](/img/17-day-deposit.png)

![daydeposit](/img/17-day-deposit-yes&no.png)

Dari data atribut day yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Baik untuk golongan nasabah yang melakukan deposit dan tidak hampir sama datanya

##### d. Duration - Deposit
Berikut adalah data terkait dengan duration dan deposit: 
![durationdeposit](/img/18-duration-deposit.png)

![durationdeposit](/img/18-duration-deposit-yes&no.png)

Dari data atribut duration yang ditampilkan dapat dilihat beberapa informasi sebagai berikut:
- Rata-rata nasabah yang memiliki durasi lebih lama ketika dihubungi lebih banyak melakukan deposit daripada yang dihubungi tidak terlalu lama.

##### e. Campaign - Deposit
Berikut adalah data terkait dengan campaign dan deposit: 
![campaigndeposit](/img/19-campaign-deposit.png)

![campaigndeposit](/img/19-campaign-deposit-yes&no.png)
##### f. Previous - Deposit
Berikut adalah data terkait dengan previous dan deposit: 
![previousdeposit](/img/20-previous-deposit.png)

![previousdeposit](/img/20-previous-deposit-yes&no.png)

## 3. Data Preparation

###### 1. Drop atribut pdays
Berdasarkan analisis sebelumnya atribut pdays dapat di hapus

![droppdays](/img/21-dataset-tanpa-pdays.png)

###### 2. Encode Categorical Data
Atribut kategorikal yang memiliki nilai binary (no atau yes) akan diubah menjadi bentuk 0 dan 1, di mana **no = 0** dan **yes = 1**. Atribut-atribut tersebut adalah default, Housing, Loan, dan Deposit

![encode1](/img/22-dataset-kategorikal-yes&no.png)

Untuk atribut deposit akan digunakan kelas yes untuk menjadi acuan. Sehingga tabel akan menjadi seperti berikut:

![encode2](/img/23-dataset-kategorikal-deposit-yes.png)

Atribut kategorikal yang bukan binary juga perlu untuk dipreprocess.
Pada atribut seperti job, education, contact, dan poutcome terdapat nilai unknown. Untuk setiap atribut akan diubah sesuai dengan atribut masing-masing. unknown pada atribut job akan diubah nilainya menjadi unknown_job, begitu juga dengan yang lainnya.

![encode2](/img/24-dataset-kategorikal.png)

## 4. Set Feature & Target
X = atribut-atribut selain deposit

Y = atribut deposit

## 5. Set Training and Testing Data
Data akan dipecah menjadi training data dan testing data dengan perbandingan 70:30 dari total data.
Training data akan digunakan untuk melatih model agar dapat membuat prediksi. Testing data akan digunakan untuk melihat sebagus apa model yang telah dilatih dalam memprediksi target.

## 6. Machine Learning
Untuk menentukan kelas deposit akan digunakan 3 buah model machine learning yakni: 
### Decision Tree
Decision Tree adalah sebuah algoritma yang termasuk dalam supervised learning dan sering digunakan untuk melakukan klasifikasi dengan membentuk pohon keputusan berdasarkan True dan False. Setiap cabang pohon akan 
mewakili keputusan yang mungkin diambil. Dengan Decision Tree akan ditentukan apakah nasabah akan melakukan deposit atau tidak. Berikut adalah diagram yang dihasilkan:

![dct](/img/25-model-decision-tree.png)

### Naive Bayes
Naive Bayes adalah metode klasifikasi yang menggunakan metode probabilitas dan statistik. Algoritma naive bayes juga termasuk dalam supervised learning. Ciri utama dr Naïve Bayes Classifier ini adalah asumsi yg sangat kuat (naïf) akan independensi dari masing-masing kondisi / kejadian. Algoritma ini mengasumsikan bahwa atribut obyek adalah independen. Probabilitas yang terlibat dalam memproduksi perkiraan akhir dihitung sebagai jumlah frekuensi dr ” master ” tabel keputusan.

### Random Forest
 adalah kombinasi dari  masing – masing tree yang baik kemudian dikombinasikan  ke dalam satu model. Random Forest bergantung pada sebuah nilai vector random dengan distribusi yang sama pada semua 
 pohon yang masing masing decision tree memiliki kedalaman yang maksimal. Random forest adalah classifier yang terdiri dari classifier yang berbentuk pohon {h(x, θ k ), k = 1, . . .} 
 dimana θk adalah random vector yang diditribusikan secara independen dan masing masing tree pada sebuah unit kan memilih class yang paling popular pada input x. Berikut ini karakteristik akurasi pada random forest.
 
## 7. Model Comparison
Hasil perbandingan akan digunakan untuk menentukan meodel mana yang paling baik untuk menentukan apakah nasabah akan melakukan deposit atau tidak. Berikut adalah hasil dari masing-masing algoritma yang digunakan:

### ROC
![roc](/img/26-model-comparison.png)

### Confusion Matrix
![cm](/img/27-model-comparison-confusion-matrix.png)

### Classification Report
![cr](/img/28-model-comparison-classification-report.png)

### Performance
![cr](/img/29-model-comparison-performance.png)

## 8. Conclusion
Berdasarkan hasil perbandingan ketiga model didapat bahwa dengan menggunakan Random Forest memiliki tingkat prediksi yang lebih baik daripada Decision Tree dan Naive Bayes. 

Pada grafik ROC, Random Forest dan Decision Tree memiliki kurva yang hampir serupa, akan tetapi kurva milik Random Forest memperlihatkan bahwa ia lebih baik daripada Decision Tree. 
Begitu juga dengan hasil yang ditunjukkan oleh Confusion Matrix, Classification report, dan Performance menunjukkan bahwa Random Forest lebih baik untuk meprediksi apakah nasabah akan melakukan deposit pada bank atau tidak.



