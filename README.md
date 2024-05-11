# PCD_UTS_202231085_2024_ITPLN
PENJELASAN CODINGAN:
import cv2: Ini adalah modul OpenCV (Open Source Computer Vision Library) yang digunakan untuk bekerja dengan citra dan video. OpenCV menyediakan berbagai fungsi untuk memanipulasi gambar, seperti membaca, menulis, dan melakukan operasi pengolahan citra.

import matplotlib.pyplot as plt: Ini mengimpor modul pyplot dari paket Matplotlib, yang digunakan untuk membuat visualisasi data. Dengan Matplotlib, Anda dapat membuat grafik, plot, dan visualisasi data dalam berbagai bentuk.

import numpy as np: Ini mengimpor modul NumPy, yang merupakan paket dasar untuk komputasi ilmiah di Python. NumPy menyediakan array multidimensi dan berbagai fungsi matematika yang kuat untuk bekerja dengan data numerik.
Baris kode img = cv2.imread("AnugerahKrisnaldi.jpg") membaca gambar "AnugerahKrisnaldi.jpg" dari direktori tempat skrip Python berjalan dan menyimpannya dalam variabel img menggunakan fungsi cv2.imread() dari OpenCV.

Baris kode rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB) mengonversi gambar yang telah dibaca sebelumnya (img) dari format warna BGR (Blue-Green-Red) menjadi format warna RGB (Red-Green-Blue).

Pada umumnya, OpenCV menggunakan format warna BGR untuk merepresentasikan gambar, sedangkan format warna yang lebih umum digunakan di banyak platform lain adalah RGB.

Fungsi cv2.cvtColor() dari OpenCV digunakan untuk melakukan konversi warna. Parameter kedua (cv2.COLOR_BGR2RGB) menentukan jenis konversi yang ingin dilakukan, yaitu dari BGR ke RGB.
Baris kode plt.imshow(rgb) digunakan untuk menampilkan gambar yang telah dikonversi ke format RGB menggunakan Matplotlib.
Baris kode gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY) mengonversi gambar yang telah dibaca sebelumnya (img) dari format warna BGR ke skala abu-abu (grayscale).

Format skala abu-abu menggunakan hanya satu saluran warna untuk merepresentasikan intensitas keabuan dari setiap piksel dalam gambar, sehingga gambar menjadi lebih mudah diolah untuk beberapa tujuan analisis atau pemrosesan citra.

Fungsi cv2.cvtColor() dari OpenCV digunakan untuk melakukan konversi warna. Parameter kedua (cv2.COLOR_BGR2GRAY) menentukan jenis konversi yang ingin dilakukan, yaitu dari BGR ke skala abu-abu.
Baris kode adjusted = cv2.convertScaleAbs(img, alpha=alpha, beta=beta) menghasilkan penyesuaian kontras dan kecerahan pada gambar yang telah dibaca sebelumnya (img).
p.figlture(figsize=(10, 5)): Ini merupakan typo, sepertinya maksudnya adalah plt.figure(figsize=(10, 5)). Baris ini membuat objek plot baru dengan ukuran (lebar, tinggi) yang ditentukan oleh figsize, dalam hal ini (10, 5).

plt.subplot(1, 2, 1): Ini menunjukkan bahwa akan ada 1 baris, 2 kolom, dan gambar pertama (indeks 1) yang akan ditampilkan.

plt.title('Original Image'): Memberikan judul untuk subplot yang sedang ditampilkan.

plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB)): Menampilkan gambar asli. Perlu dicatat bahwa kita menggunakan cv2.cvtColor() untuk mengonversi gambar dari format BGR (yang digunakan oleh OpenCV) menjadi format RGB agar sesuai dengan kebutuhan Matplotlib.

plt.axis('off'): Ini menghilangkan sumbu x dan y dari gambar.

plt.subplot(1, 2, 2): Menunjukkan bahwa akan ada 1 baris, 2 kolom, dan gambar kedua (indeks 2) yang akan ditampilkan.

plt.title('Brightened Image'): Memberikan judul untuk subplot yang sedang ditampilkan.

plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)): Menampilkan gambar yang telah disesuaikan kecerahannya.

plt.axis('off'): Ini menghilangkan sumbu x dan y dari gambar.

plt.show(): Ini menampilkan plot yang telah dibuat dengan semua subplot yang telah ditentukan sebelumnya.
plt.subplot(2, 1, 1): Menunjukkan bahwa akan ada 2 baris, 1 kolom, dan gambar pertama (indeks 1) yang akan ditampilkan.

plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)): Menampilkan gambar asli yang telah disesuaikan kecerahannya.

plt.title('Original Image'): Memberikan judul untuk subplot yang sedang ditampilkan.

plt.subplot(2, 2, 2): Menunjukkan bahwa akan ada 2 baris, 2 kolom, dan subplot kedua (indeks 2) yang akan menampilkan saluran warna merah.

plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0], cmap="gray"): Menampilkan saluran warna merah dari gambar asli. Dengan mengambil slice [:,:,0], kita hanya menampilkan piksel-piksel pada saluran merah saja.

plt.title('Red'): Memberikan judul untuk subplot yang menampilkan saluran warna merah.

plt.subplot(2, 2, 3) dan plt.subplot(2, 2, 4): Menampilkan subplot yang akan menampilkan saluran warna hijau dan biru secara berurutan.

Sama seperti langkah 5 dan 6, kita menampilkan saluran warna hijau dan biru dengan mengambil slice yang sesuai dari gambar asli.

cmap="gray": Menentukan bahwa gambar akan ditampilkan dalam skala abu-abu, karena saluran warna dalam gambar tidak memiliki warna yang sesuai dalam konteks ini.

plt.show(): Menampilkan plot yang telah dibuat dengan semua subplot yang telah ditentukan sebelumnya.
hijau = cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1]: Ini mengambil saluran warna hijau (indeks 1) dari gambar yang telah disesuaikan kecerahannya, dan menyimpannya dalam variabel hijau.

fig, axs = plt.subplots(1, 2, figsize=(15, 5)): Ini membuat sebuah subplot dengan satu baris dan dua kolom, dengan ukuran total gambar 15x5.

axs[0].imshow(hijau, cmap='gray'): Ini menampilkan gambar saluran warna hijau di subplot pertama dan menentukan bahwa akan menggunakan colormap 'gray' untuk menampilkan gambar dalam skala abu-abu.

axs[0].set_title('Green Channel'): Memberikan judul untuk subplot yang menampilkan saluran warna hijau.

hist = cv2.calcHist([hijau], [0], None, [256], [0, 256]): Ini menghitung histogram dari saluran warna hijau menggunakan fungsi cv2.calcHist() dari OpenCV. Histogram akan memiliki 256 bin dan rentang nilai 0 hingga 256.

axs[1].plot(hist): Ini menampilkan histogram di subplot kedua menggunakan plt.plot().

axs[1].set_title('Histogram of Green Channel'): Memberikan judul untuk subplot yang menampilkan histogram saluran warna hijau.

plt.show(): Ini menampilkan plot yang telah dibuat dengan semua subplot yang telah ditentukan sebelumnya.
merah = cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0]: Ini mengambil saluran warna merah (indeks 0) dari gambar yang telah disesuaikan kecerahannya, dan menyimpannya dalam variabel merah.

fig, axs = plt.subplots(1, 2, figsize=(15, 5)): Ini membuat sebuah subplot dengan satu baris dan dua kolom, dengan ukuran total gambar 15x5.

axs[0].imshow(merah, cmap='gray'): Ini menampilkan gambar saluran warna merah di subplot pertama dan menentukan bahwa akan menggunakan colormap 'gray' untuk menampilkan gambar dalam skala abu-abu.

axs[0].set_title('Red Channel'): Memberikan judul untuk subplot yang menampilkan saluran warna merah.

hist = cv2.calcHist([merah], [0], None, [256], [0, 256]): Ini menghitung histogram dari saluran warna merah menggunakan fungsi cv2.calcHist() dari OpenCV. Histogram akan memiliki 256 bin dan rentang nilai 0 hingga 256.

axs[1].plot(hist): Ini menampilkan histogram di subplot kedua menggunakan plt.plot().

axs[1].set_title('Histogram of Red Channel'): Memberikan judul untuk subplot yang menampilkan histogram saluran warna merah.

plt.show(): Ini menampilkan plot yang telah dibuat dengan semua subplot yang telah ditentukan sebelumnya.
biru = cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2]: Ini mengambil saluran warna biru (indeks 2) dari gambar yang telah disesuaikan kecerahannya, dan menyimpannya dalam variabel biru.

fig, axs = plt.subplots(1, 2, figsize=(15, 5)): Ini membuat sebuah subplot dengan satu baris dan dua kolom, dengan ukuran total gambar 15x5.

axs[0].imshow(biru, cmap='gray'): Ini menampilkan gambar saluran warna biru di subplot pertama dan menentukan bahwa akan menggunakan colormap 'gray' untuk menampilkan gambar dalam skala abu-abu.

axs[0].set_title('Blue Channel'): Memberikan judul untuk subplot yang menampilkan saluran warna biru.

hist = cv2.calcHist([biru], [0], None, [256], [0, 256]): Ini menghitung histogram dari saluran warna biru menggunakan fungsi cv2.calcHist() dari OpenCV. Histogram akan memiliki 256 bin dan rentang nilai 0 hingga 256.

axs[1].plot(hist): Ini menampilkan histogram di subplot kedua menggunakan plt.plot().

axs[1].set_title('Histogram of Blue Channel'): Memberikan judul untuk subplot yang menampilkan histogram saluran warna biru.

plt.show(): Ini menampilkan plot yang telah dibuat dengan semua subplot yang telah ditentukan sebelumnya.
import cv2: Modul OpenCV (Open Source Computer Vision Library) digunakan untuk bekerja dengan citra dan video. OpenCV menyediakan berbagai fungsi untuk memanipulasi gambar, seperti membaca, menulis, dan melakukan operasi pengolahan citra.

import numpy as np: Modul NumPy digunakan untuk komputasi ilmiah di Python. NumPy menyediakan array multidimensi dan berbagai fungsi matematika yang kuat untuk bekerja dengan data numerik. Hal ini sangat berguna dalam pengolahan citra karena citra dapat direpresentasikan sebagai array NumPy.

import matplotlib.pyplot as plt: Modul pyplot dari paket Matplotlib digunakan untuk membuat visualisasi data. Dengan Matplotlib, Anda dapat membuat grafik, plot, dan visualisasi data dalam berbagai bentuk. Ini sangat berguna untuk menampilkan gambar dan histogram, serta untuk melakukan visualisasi hasil dari pemrosesan citra.
Membaca gambar: Baris pertama img = cv2.imread('AnugerahKrisnaldi.jpg') membaca gambar dengan nama file "AnugerahKrisnaldi.jpg" dan menyimpannya dalam variabel img.

Konversi ke grayscale: Baris kedua gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY) mengonversi gambar ke skala keabu-abuan (grayscale) menggunakan fungsi cv2.cvtColor(). Hasilnya disimpan dalam variabel gray.

Inisialisasi subplot: Baris ketiga fig, axs = plt.subplots(2, 2, figsize=(10,10)) menginisialisasi subplot dengan ukuran 2x2, dengan ukuran total gambar 10x10.

Ambang batas untuk mendapatkan citra biner: Baris keempat (thresh, binary1) = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY) menggunakan fungsi cv2.threshold() untuk menghasilkan citra biner dari gambar grayscale. Nilai ambang batas ditentukan secara otomatis (none) karena diatur ke 0. Citra biner hasilnya disimpan dalam variabel binary1 dan ditampilkan dalam subplot pertama dengan judul "NONE".

Konversi ke HSV dan definisi range warna biru: Baris keenam image_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV) mengonversi gambar dari format BGR ke ruang warna HSV. Kemudian, di baris selanjutnya, kita mendefinisikan range warna biru dalam ruang warna HSV menggunakan array NumPy blue_lower dan blue_upper.

Membuat mask untuk warna biru: Baris terakhir yang diberikan di codingan ini sebelumnya, yang tidak lengkap, akan membuat mask untuk mendeteksi warna biru dalam gambar. Namun, karena tidak ada kode yang diberikan di sini, saya tidak bisa memberikan penjelasan lengkapnya. Biasanya, langkah ini melibatkan penggunaan fungsi seperti cv2.inRange() untuk membuat mask dengan memasukkan batas bawah dan batas atas warna biru yang telah ditentukan sebelumnya.



