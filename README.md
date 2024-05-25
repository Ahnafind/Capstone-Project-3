# Capstone-Project-3
## **Bank Marketing Campaign**

**Context**

Bank merupaka sebuah lembaga intermediasi keuangan umumnya didirikan dengan kewenangan menerima simpanan uang, meminjamkan uang, dan menerbitkan promes atau yang dikenal sebagai banknote. Kata bank berasal dari bahasa Italia banca yang berarti tempat penukaran uang.

Di era yang berkembang sepeti saat ini, Bank harus bisa bersaing dengan kompetitor-kompetitor lainnya. Slah satu caranya dengan strategi pemasaran.

**Problem Statement**

Dalam menaikan profit bank, maka bank memerlukan strategy dalam meningkatkan profit. Salah satunya dengan melakukan kampanye pemasaran. Saat ingin melakukan kampanye pemasaran bank memerlukan targa kepada semua nasabahnya. Cara itu membuat expense perusahaan melonjak. Oleh karena itu saat dilakukan pemasaran, bank harus bisa melakukan target yang tepat sasaran.

Untuk meningkatkan ketepatan dan efesiensi yang maksimal dalam kampanye pemasaran, perusahaan juga harus mencari peluang target yang tinggi.

**Goals**

Banyaknya nasabah yang dimiliki bank sangat menghabiskan waktu dan memerlukan biaya tambahan jika perusahaan menggunakan vendor atau jasa dalam menyaring nasabah yang memiliki tepat sasaran. Oleh sebab itu perusahaan bank harus bisa mem-forcasting nasabah dengan karakter seperti apa yang bisa menjadi target dalam melakukan kampanye pemasaran.

Setelah itu perusahaan dapat mengetahui profile atau segmen mana saja yang membuat nasabah ingin atau tidak melakukan deposit. Sehingga perusahaan bisa membuat semacam Business Plan berdasarkan pengelompokan target nasabah yang sudah dibuat.

**Analytic Approach**

Dalam melakukan analisa yang akan dibuat, maka kita didorong untuk melihat pattern apa yang akan membedakan nasabah yang ingin deposit atau tidak ingin melakukan deposit.
Setelah itu kita membuat pengelompokan yang menunjang dalam mem-forcasting hal tersebut. Menmaksimalkan sumber data yang kita miliki.

Lalu kita juga bisa melihat keakuratan dari setiap pattern nasabah saat kita melakukan pengolahan data.

**Metric Evaluation**

Target :
* 0 : Nasabah tidak deposit
* 1 : Nasabah deposit

Type Error:
* FP (False Positive): Nasabah diprediksi akan melakukan deposit, tetapi kenyataannya tidak.
Konsekuensi FP: Waktu dan sumber daya yang dialokasikan untuk nasabah tersebut akan terbuang percuma.

* FN (False Negative): Nasabah diprediksi tidak akan melakukan deposit, tetapi kenyataannya melakukan deposit.
Konsekuensi FN: Bank akan kehilangan peluang untuk mendapatkan keuntungan dari nasabah yang sebenarnya melakukan deposit.

Mempertimbangkan konsekuensi ini, baik recall maupun presisi sangat krusial dalam kasus ini, sehingga kita akan menerapkan metrik F-Score. Perlu dicatat bahwa tujuan utama kampanye pemasaran bank ini adalah untuk menarik lebih banyak nasabah agar melakukan deposit. Oleh karena itu, kita akan merancang model yang dapat mengidentifikasi sebanyak mungkin kelas positif yang benar serta meminimalkan prediksi false positive dan false negative.

Selain itu, prioritas kita adalah mengurangi False Negative agar bank tidak kehilangan kesempatan mendapatkan nasabah yang melakukan deposit. Karena False Negative menjadi prioritas utama, recall dari model akan lebih diutamakan untuk ditingkatkan. Oleh sebab itu, metrik F-Score yang digunakan adalah F2-Score.

## *Data Understanding and Cleaning*

Sebelum memulai analisis, penting untuk melakukan pemahaman yang mendalam terhadap dataset yang akan digunakan dalam tahap data understanding. Dengan melakukan ini, kita dapat mengidentifikasi anomali atau ketidaknormalan dalam dataset yang memerlukan penanganan selama tahap data cleaning. Setiap tindakan penanganan anomali yang diambil harus didukung dengan justifikasi yang kuat, baik berdasarkan pengetahuan domain maupun analisis statistik, untuk memastikan integritas dan kualitas data yang optimal.

| *Attribute* | *Data Type* | *Description* |
| ---       | ---       | ---        
| age       | Integer   | Usia  |
| job       | Object    | Pekerjaan  |
| balance   | Integer   | Saldo  |
| housing   | Object    | Mempunyai kredit Rumah atau tidak |
| loan      | Object    | Mempunyai pinjaman atau tidak |
| contact   | Object    | Tindakan komunikasi terbaru yang dilakukan terhadap nasabah.|
| month     | Object    | Bulan terakhir  berhubungan dengan nasabah. |
| campaign  | Integer   | Total interaksi yang dilakukan dengan nasabah selama kampanye.e |
| pdays     | Integer   | Total hari setelah nasabah dihubungi sejak kampanye terakhir |
| poutcome  | Object    | Hasil dari kampanye terakhir |
| deposit   | Object    | Melakukan deposit atau tidak |

## **Tujuan**


Berdasarkan analisis terhadap confusion matrix dari model akhir, berikut adalah beberapa kesimpulan yang dapat diambil:

* Performa Keseluruhan Model:
Dengan tingkat akurasi sebesar 60,3%, dapat disimpulkan bahwa model yang dibuat masih belum cukup baik dalam memprediksi kedua kelas, yaitu nasabah yang melakukan deposit dan yang tidak. Hal ini disebabkan oleh adanya trade-off antara recall dan presisi. Meskipun fokus utama adalah meningkatkan prediksi yang benar untuk nasabah yang akan deposit, namun prediksi yang benar untuk nasabah yang tidak deposit menjadi berkurang. Error rate pada model tersebut mencapai 39,7%.

* Fokus pada Kelas Positif:
Dengan F2-Score sekitar 80,2%, model terbilang cukup baik dalam memprediksi nasabah yang akan melakukan deposit. F2-Score memberikan bobot yang lebih besar pada recall, sehingga lebih memprioritaskan prediksi yang benar untuk kelas positif.


* Kualitas Prediksi untuk Kelas Negatif:
Spesifisitas model, yang mengukur kemampuan model dalam memprediksi nasabah yang tidak akan deposit, hanya mencapai sekitar 31,7%, menandakan bahwa model memiliki kinerja yang buruk dalam memprediksi kelas negatif.

* Kualitas Prediksi untuk Kelas Positif:
Sensitivitas model, yang mengukur kemampuan model dalam memprediksi nasabah yang akan deposit, mencapai sekitar 89,9%, menunjukkan kualitas yang baik dalam memprediksi kelas positif.

* Feature Penting dalam Klasifikasi:
Feature yang paling penting dalam klasifikasi nasabah yang akan deposit dan tidak deposit adalah contact_other, yang menunjukkan jenis komunikasi terakhir selain cellular dan telephone. Selanjutnya, feature poutcome_success, yang menandakan hasil sukses dari kampanye pemasaran terakhir, juga memiliki kontribusi yang signifikan dalam klasifikasi.*

### Saran dan Rekomendasi

Untuk mengembangkan proyek ini lebih lanjut dan meningkatkan kualitas modelnya, beberapa langkah yang dapat diambil adalah:

* Menggunakan Hyperparameter yang lebih baik:
Melakukan pengoptimalan lebih lanjut terhadap hyperparameter model, baik melalui metode grid search atau teknik optimasi lainnya, untuk memastikan bahwa model mencapai performa optimalnya.

* Penambahan Fitur Baru:
Menambahkan fitur-fitur baru seperti kisaran gaji, status perkawinan, dan jumlah anak dapat memberikan informasi tambahan yang relevan dalam memprediksi minat calon nasabah untuk melakukan deposit. Fitur-fitur ini dapat memberikan pemahaman yang lebih baik tentang kondisi keuangan dan tanggung jawab keuangan calon nasabah, sehingga memungkinkan model untuk membuat prediksi yang lebih akurat.

* Analisis Lebih Lanjut terhadap Data:
Melakukan analisis lebih lanjut terhadap data untuk memahami lebih dalam pola-pola dan insight-insight yang terkandung di dalamnya. Hal ini dapat dilakukan melalui eksplorasi data yang lebih mendalam, visualisasi data yang lebih kompleks, atau penggunaan teknik analisis statistik yang lebih canggih.
