# Spam Email Classification
## Domain Proyek
Email telah menjadi alat komunikasi yang sangat penting dalam kehidupan sehari-hari, baik untuk keperluan pribadi maupun profesional. Namun, dengan meningkatnya penggunaan email, spam—email yang tidak diinginkan dan dikirim secara massal—juga semakin banyak. Spam ini sering kali berisi iklan yang mengganggu, penawaran palsu, atau bahkan konten berbahaya seperti phishing dan malware, yang dapat membahayakan keamanan pengguna.

Permasalahan spam tidak hanya mengganggu pengguna dengan memenuhi kotak masuk mereka, tetapi juga membawa risiko keamanan yang serius, seperti pencurian data pribadi dan serangan siber. Oleh karena itu, penting untuk memiliki sistem yang dapat secara otomatis mengidentifikasi dan menyaring email spam sebelum mencapai pengguna.

Klasifikasi email spam dengan menggunakan machine learning adalah salah satu metode yang paling efektif untuk menangani masalah ini. Dengan melatih model pada data historis yang mencakup email spam dan non-spam (ham), algoritma dapat mempelajari pola dan karakteristik spesifik dari spam. Fitur seperti subjek, isi pesan, dan metadata pengirim digunakan untuk memprediksi apakah sebuah email termasuk spam atau tidak.
## Business Understanding
### Problem Statements
1. Spam email mengganggu produktivitas dan pengalaman pengguna dengan memenuhi kotak masuk mereka dengan pesan-pesan yang tidak relevan. Pengguna sering kali harus menghabiskan waktu untuk menyortir dan menghapus email spam secara manual
2. Spam email tidak hanya mengganggu, tetapi juga menimbulkan risiko keamanan yang serius. Banyak spam mengandung konten berbahaya seperti phishing, malware, atau penipuan yang dapat mengekspos pengguna terhadap serangan siber, pencurian identitas, dan kerugian finansial.
3. Meningkatnya volume spam email juga membebani infrastruktur jaringan dan server email, meningkatkan biaya operasional dan sumber daya yang diperlukan untuk menyaring dan memproses email.
### Goals
1. Dengan menerapkan model klasifikasi email spam yang akurat, diharapkan email spam dapat dipisahkan secara otomatis dari email yang sah, sehingga kotak masuk pengguna tetap bersih dan relevan.
2. Dengan mendeteksi dan memfilter email yang berisi konten berbahaya secara efektif, model klasifikasi spam dapat melindungi pengguna dari potensi serangan siber dan kerugian finansial.
3. Dengan meningkatkan akurasi sistem klasifikasi spam, volume email spam yang masuk ke server email akan berkurang.
###  Solution Statement
1. Menggunakan model machine learning SVM  
2. Melakukan hyperparameter tuning untuk meningkatkan performa model yang dipilih.
3. Menerapkan teknik feature engineering untuk meningkatkan kemampuan model dalam mengenali spam, seperti menggunakan metode untuk representasi teks TF-IDF, serta menambahkan fitur tambahan seperti panjang email dan jumlah tautan.
## Data Understanding
Dataset yang digunakan pada proyek ini dapat diunduh pada tautan berikut: [Spam Email Dataset](https://www.kaggle.com/datasets/ashfakyeafi/spam-email-classification)

Variabel pada dataset:
- Message: Berisikan text message pada email
- Category: Indikasi text termasuk ke kategori 'spam' atau 'ham' (email asli)

Karakteristik data:
- Dataset terdiri dari 5573 data dengan dua variabel 'Message' dan 'Category' dan keduanya bertipe text
- Distribusi banyaknya data pada category 'spam' dan 'ham' adalah sebagai berikut
![gambar distribusi](https://github.com/user-attachments/assets/bdbd4e41-b234-4934-b877-fa2cc0f84efe)

- Tidak terdapat data yang null
- Melalui proses feature engineering dengan membuat fitur panjang kata dan jumlah tautan didapatkan karateristik data adalah sebagai berikut
  
  ![Screenshot 2024-08-19 152543](https://github.com/user-attachments/assets/da89f7fe-2c01-4704-a234-b97dd9517029)

- Hasil worldcloud pada text seperti berikut, dapat dilihat terdapat kata-kata umum, seperti 'sorry', 'love', 'come', yang terdapat pada pesan sehari-hari

![download](https://github.com/user-attachments/assets/39142049-789b-41a3-8f08-375ad938d8c3)

## Data Preparation
- Dilakukan proses split data menjadi data train dan data test dengan rasio pembagian 80:20. Sehingga jumlah data train sebesar 4457 data dan test sebesar 1115 data.
- Menggunakan fungsi TF-IDF pada atribut 'Message' untuk menentukan pentingnya kata dalam konteks pesan tertentu dengan memperhitungkan keunikan kata tersebut di seluruh corpus. Misalnya, kata-kata umum seperti "dan", "adalah", "atau" sering muncul di hampir setiap pesan dan tidak banyak membantu dalam membedakan antara spam dan non-spam. TF-IDF memberikan bobot yang lebih rendah untuk kata-kata ini. Sebaliknya, kata-kata yang lebih jarang dan lebih spesifik yang mungkin mengindikasikan spam, seperti "penawaran", "gratis", atau "diskon", akan diberi bobot lebih tinggi oleh TF-IDF, membantu model untuk fokus pada kata-kata ini.
- Menggabungkan hasil TF-IDF dengan fitur lain seperti panjang kata dan banyaknya tautan yang nantinya digunakan sebagai fitur untuk melatih model.

## Model
Model yang digunakan pada proyek ini adalah model SVM (Support Vector Machine) karena SVM sangat efektif dalam bekerja dengan data yang memiliki banyak fitur, seperti teks yang telah diolah dengan TF-IDF. Ini karena SVM mencoba menemukan hyperplane terbaik yang memisahkan kelas-kelas dalam ruang fitur berdimensi tinggi.

## Evaluasi
Model berperforma sangat baik seperti pada gambar di bawah

![image](https://github.com/user-attachments/assets/3c78d447-872a-4171-8607-1c3a88637784)
Hasil inferensi menggunakan text inputan, model dapat mengklasifikasikan email dengan baik

![image](https://github.com/user-attachments/assets/bc721ba7-20ec-4f1c-bbc4-8e3fea19da57)


