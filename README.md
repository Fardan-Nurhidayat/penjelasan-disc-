## Kosa Kata 
most = paling menggambarkan / most

least = paling tidak menggambarkan / least


Malam kak, di sini aku izin jelasin kenapa pada section profil kepribadian, managerial, kepemimpinan, dimensi/tipe kepemimpinan, kesimpulan, dan saran pekerjaan berpotensi memiliki jawaban atau hasil yang sama.

Perlu diketahui bahwa setiap soal memiliki 4 pernyataan. Setiap pernyataan mengandung satu kode, yaitu D (Dominance), I (Influence), S (Steadiness), atau C (Conscientiousness). Pada setiap soal, peserta diminta memilih:

1. Pernyataan yang paling menggambarkan atau paling mendekati dirinya (paling menggambarkan / **most**).
2. Pernyataan yang paling tidak menggambarkan atau paling tidak mendekati dirinya (paling tidak menggambarkan / **least**).

Kalau sudah paham penjelasan di atas, kita lanjut ke contoh perhitungannya.

Ketika peserta memilih satu pernyataan sebagai yang paling menggambarkan dirinya, sistem akan menambahkan skor **most** pada kode pernyataan tersebut. Begitu juga ketika peserta memilih satu pernyataan sebagai yang paling tidak menggambarkan dirinya, sistem akan menambahkan skor **least** pada kode pernyataan tersebut.

Misalnya: 

Soal pertama, peserta memilih pernyataan dengan kode D sebagai yang paling menggambarkan dan kode S sebagai yang paling tidak menggambarkan.

Di sistem akan tersimpan:

```text
D paling menggambarkan (most)       +1
S paling tidak menggambarkan (least) +1
```

Soal kedua, peserta memilih pernyataan dengan kode I sebagai yang paling menggambarkan dan kode C sebagai yang paling tidak menggambarkan.

Di sistem akan tersimpan:

```text
I paling menggambarkan (most)       +1
C paling tidak menggambarkan (least) +1
```

Dengan cara yang sama, misalnya hasil pilihan dari seluruh 8 soal adalah sebagai berikut:

```text
Pilihan paling menggambarkan (most):
D = 6
I = 13
S = 2
C = 7

Pilihan paling tidak menggambarkan (least):
D = 4
I = 2
S = 10
C = 9
```

Jadi, angka tersebut bukan berarti peserta mendapatkan nilai benar atau salah. Angka tersebut menunjukkan berapa kali kode D, I, S, dan C dipilih sebagai yang paling menggambarkan dan paling tidak menggambarkan dirinya. Selain ada most dan least , ada juga NETRAL

## Apa yang dimaksud dengan nilai netral?

Setelah nilai **most** dan **least** terkumpul, sistem menghitung nilai **netral** untuk setiap kode dengan rumus:

```text
nilai netral = most - least
```

Berdasarkan contoh di atas:

```text
D netral = 6 - 4  =  2
I netral = 13 - 2 = 11
S netral = 2 - 10  = -8
C netral = 7 - 9  = -2
```

Artinya:

- Nilai netral positif berarti kode tersebut lebih sering dipilih sebagai yang paling menggambarkan.
- Nilai netral negatif berarti kode tersebut lebih sering dipilih sebagai yang paling tidak menggambarkan.
- Nilai netral 0 berarti jumlah pilihan most dan least untuk kode tersebut sama.
- Nilai netral bukan pilihan baru dari peserta, tetapi hasil pengurangan antara nilai most dan least.

Pada contoh ini, nilai netralnya adalah:

```text
D = 2
I = 11
S = -8
C = -2
```

Nilai inilah yang kemudian digunakan sistem untuk menentukan kode kombinasi dan teks interpretasi utama pada report. Untuk grafik, sistem tetap menyimpan dan memakai nilai most, least, dan netral secara terpisah.

## Kenapa beberapa section bisa menghasilkan interpretasi yang sama?

Untuk menentukan kode interpretasi utama, sistem tidak langsung memakai angka most atau least satu per satu. Sistem memeriksa nilai netral D, I, S, dan C menggunakan batas tertentu. Secara sederhana, kode akan masuk apabila memenuhi batas berikut:

```text
D >= -5
I >= 2
S >= 5
C >= -1
```

Pada contoh di atas:

```text
D =  2  -> masuk
I = 11  -> masuk
S = -8  -> tidak masuk
C = -2  -> tidak masuk
```

Maka kode kombinasi yang terbentuk adalah:

```text
DI
```

Misalnya ada peserta lain dengan hasil netral:

```text
D = 3
I = 3
S = -3
C = -2
```

Hasilnya tetap:

```text
D =  3  -> masuk
I =  3  -> masuk
S = -3  -> tidak masuk
C = -2  -> tidak masuk

Kode kombinasi = DI
```

Walaupun angka dan pola jawaban peserta tidak persis sama, keduanya menghasilkan kode kombinasi `DI`. Sistem kemudian mengambil data interpretasi yang tersimpan untuk kode `DI` tersebut.

Karena beberapa section menggunakan kode yang sama, isi yang diambil juga dapat sama. Section yang berpotensi menggunakan kode interpretasi netral yang sama adalah:

- **Managerial**
- **Kepemimpinan**
- **Dimensi atau tipe kepemimpinan**
- **Kesimpulan**
- **Saran pekerjaan / Job Match**

Jadi, bukan berarti jawaban peserta diduplikasi secara tidak sengaja. Section-section tersebut memang membaca hasil kode interpretasi yang sama. Selama kode yang terbentuk sama-sama `DI`, sistem akan mengambil data interpretasi untuk `DI`.

Untuk **profil kepribadian**, sumbernya sedikit berbeda. Section ini menggunakan personality dari tiga kode grafik, yaitu kode grafik most, least, dan netral. Karena itu, profil kepribadian masih dapat berbeda meskipun section managerial, kepemimpinan, kesimpulan, dan saran pekerjaan sama-sama mengambil interpretasi dari kode `DI`.

## Bagaimana grafik DISC dibuat?

Selain menghitung nilai netral, sistem juga membuat 3 grafik berdasarkan tiga jenis nilai:

1. **Grafik most** menggunakan nilai yang paling menggambarkan.
2. **Grafik least** menggunakan nilai yang paling tidak menggambarkan.
3. **Grafik netral** menggunakan hasil `most - least`.

Untuk setiap grafik, nilai D, I, S, dan C dikonversi ke angka grafik berdasarkan rentang nilai yang sudah disiapkan di sistem. Urutan kodenya adalah D, I, S, C. Contohnya, hasil konversi bisa berbentuk:

```text
Grafik most   = 4567
Grafik least  = 3214
Grafik netral = 5672
```

Setiap angka tersebut kemudian digunakan untuk menentukan posisi titik D, I, S, dan C pada gambar. Sistem menghubungkan titik-titik tersebut sehingga terbentuk pola grafik DISC, lalu menampilkan nama personality yang sesuai dengan kode grafik apabila datanya tersedia.

Karena grafik most, least, dan netral memakai sumber nilai yang berbeda, bentuk ketiga grafik tersebut tidak harus sama. Begitu juga dengan section **profil kepribadian** yang mengambil personality dari kode grafik most, least, dan netral. Section ini dapat menampilkan sampai 3 deskripsi personality, sehingga hasilnya bisa berbeda walaupun section lain menghasilkan interpretasi yang sama.

## Ringkasan sumber nilai setiap section

```text
Grafik most       -> nilai most yang dikonversi
Grafik least      -> nilai least yang dikonversi
Grafik netral     -> nilai netral yang dikonversi
Profil kepribadian -> personality dari kode grafik most, least, dan netral

Managerial        -> kode kombinasi dari nilai netral
Kepemimpinan      -> kode kepemimpinan dari nilai netral
Dimensi/tipe kepemimpinan -> hasil interpretasi kepemimpinan dari kode tersebut
Kesimpulan        -> data conclusion pada kode kombinasi
Saran pekerjaan   -> data job match pada kode kombinasi
```

Jadi kesimpulannya, perbedaan jawaban pada setiap soal tetap dihitung dan disimpan sebagai nilai **most**, **least**, dan **netral**. Namun, untuk section interpretasi seperti managerial, kepemimpinan, kesimpulan, dan saran pekerjaan, sistem menggunakan kode hasil klasifikasi. Beberapa nilai yang berbeda dapat masuk ke kode yang sama, sehingga teks interpretasinya juga berpotensi sama. Perbedaan yang lebih detail terutama dapat terlihat pada nilai dan pola grafik most, least, netral, serta deskripsi personality yang berasal dari ketiga grafik tersebut.
