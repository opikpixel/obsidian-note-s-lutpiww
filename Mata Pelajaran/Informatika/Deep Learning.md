# **Pengenalan TensorFlow dan Keras untuk Deep Learning**
TensorFlow dan Keras merupakan framework yang sangat terkenal di kalangan praktisi machine learning, tetapi hal ini bukan berarti framework lainnya kurang bagus, ya. Hasil ini merupakan riset yang dilakukan oleh Jeff Hale pada tahun 2018 mengenai deep learning. Riset tersebut menggunakan 11 sumber data pada 7 kategori yang berbeda untuk mengukur popularitas framework berdasarkan ketertarikan pengguna. Hasilnya TensorFlow menang telak, bukan? Hal ini terjadi karena kedua framework ini memiliki beberapa kelebihan, seperti Open-source, mudah untuk debugging, compatibility yang baik, scalability yang fleksibel, komunitas yang luas dan masih banyak lagi. 

Dengan demikian, tentu Anda semakin bersemangat dan penasaran untuk mempelajari materi ini. Supaya tidak makin penasaran, mari kita mulai perjalanan yang romantis dengan TensorFlow dan Keras.

TensorFlow 
TensorFlow (TF) adalah end-to-end open source platform yang dikembangkan oleh Google Brain dan sangat populer untuk pengembangan machine learning berskala besar. TensorFlow memiliki ekosistem tools, library, dan sumber daya komunitas yang komprehensif dan fleksibel, sehingga memungkinkan para peneliti dan pengembang membangun serta menerapkan aplikasi machine learning dengan mudah.

Secara umum, TensorFlow memiliki banyak kelebihan seperti yang sudah disebutkan di atas. Tentunya Anda penasaran terkait kelebihan tersebut, bukan? Mari kita bahas kelebihan TensorFlow satu per satu agar Anda lebih terpacu untuk menyelesaikan misi menjadi praktisi machine learning yang andal.

Open-source
Sebagai sebuah frameworkopen-source tentunya penggunaan TensorFlow tidak mengeluarkan biaya dan bisa digunakan oleh semua orang mulai dari pelajar, guru, dosen, peneliti, data scientist, machine learning engineer, dan lainnya. Selain itu, hal ini juga memungkinkan untuk menggunakan TensorFlow kapan saja serta di mana saja sesuai kebutuhan pengguna tanpa harus memikirkan pengeluaran sedikit pun.
Scalability
Hingga saat ini, TensorFlow tidak terbatas hanya pada satu platform saja. Kelebihan ini tentu menguntungkan bagi pengguna karena kita dapat membangun sebuah sistem AI menggunakan TensorFlow di berbagai platform dengan komputasi atau performa yang sama. Selain itu, model yang dihasilkan TensorFlow juga dapat menyesuaikan komputasi yang digunakan berdasarkan jumlah requests. Sangat menarik, bukan? 
Compatibility
Saat ini, kompatibilitas/kecocokan merupakan salah satu faktor yang paling penting. Nah, pada kasus ini, TensorFlow kompatibel dengan berbagai macam bahasa pemrograman, seperti Python, C++, JavaScript, Kotlin, dan lain sebagainya.
Parallelism
Hal krusial lainnya yang mampu ditangani TensorFlow adalah hardware acceleration Mungkin sebagian dari Anda bertanya, “Apa itu hardware acceleration?” Ini merupakan sebuah library yang memberikan TensorFlow kemampuan untuk membagikan ketersediaan hardware seperti CPU atau GPU pada proses pelatihan maupun prediksi.
Graph
Untuk meningkatkan pengalaman developer ketika membangun sebuah machine learning, tentunya kita juga memerlukan pengukuran yang lebih mudah dengan menggunakan visualisasi. Hal itu akan meringankan beban kognitif yang dibebankan kepada otak kita. Setelah memikirkan banyak hal pada setiap tahapan pembangunan machine learning, tentunya kita juga memerlukan sebuah alat yang dapat mempermudah perhitungan performa model.
Architectural Support
TensorFlow didukung oleh beberapa hardware yang dapat melakukan proses pelatihan, mulai dari CPU, GPU, hingga TPU. Pada tahap eksplorasi, CPU dapat dikatakan sangat cukup untuk melakukan pelatihan machine learning maupun deep learning. Namun, untuk beberapa kasus seperti dataset yang sangat besar atau data unstructured (gambar, suara, video, dan lain sebagainya), GPU akan memproses pelatihan dengan lebih cepat. Hal ini dikarenakan GPU memiliki sebuah arsitektur yang dapat melakukan proses yang sangat banyak secara bersamaan.
Library Management
Sebagai salah satu framework yang dikembangkan oleh Google, tentunya TensorFlow memiliki update yang sangat baik. TensorFlow sendiri melakukan pembaruan dalam waktu yang sangat cepat agar dapat memberikan pengalaman yang maksimal kepada seluruh developernya. Hingga saat ini, pembaruan TensorFlow masih terus dikembangkan. Hal ini dibuktikan dengan rilisnya versi 2.16.1 pada 8 Maret 2024. Tentunya dengan pembaruan ini membuat para praktisi machine learning tidak perlu merasa takut dengan framework yang deprecated sehingga kreatifitas developer bisa tetap tersalurkan..
Kelebihan di atas merupakan highlight yang perlu kita perhatikan. Selain itu, masih ada banyak sekali kelebihan TensorFlow yang akan Anda rasakan ketika membangun model machine learning menggunakan framework tersebut. Sampai di sini tentunya Anda sudah paham alasan TensorFlow menjadi sangat populer di kalangan praktisi machine learning, ‘kan?

 

Keras
Keras adalah API untuk mengembangkan jaringan saraf tiruan. Dengan Keras, kita akan lebih mudah dalam membuat sebuah multi layer perceptron dan convolutional neural network. Aplikasi dari Keras sangat luas dan memungkinkan kita untuk membangun jaringan saraf tiruan dengan tujuan klasifikasi gambar, pemrosesan bahasa alami, pengenalan suara, dan prediksi time series.

Komponen inti pembangun sebuah jaringan saraf tiruan dalam Keras adalah layer. Sebuah layer pada Keras, sama dengan sebuah layer pada MLP yang memiliki beberapa perceptron. Terdengar sangat kompleks, bukan? Namun, penggunaan Keras saat ini sangatlah mudah.



Pra-pemrosesan Data untuk Model
Tahap pemrosesan data merupakan perubahan dari data mentah yang dibersihkan dan diatur untuk tahap pemrosesan berikutnya. Selama tahapan pemrosesan data, data mentah harus diperiksa dengan sangat cermat agar kita dapat memahami karakteristik dataset yang akan dilatih.

Dataset untuk setiap masalah tentunya berbeda. Contohnya pada dataset untuk klasifikasi gambar dan dataset untuk pemrosesan bahasa alami atau NLP. Pada dataset untuk klasifikasi gambar, sampelnya berupa kumpulan gambar atau matriks hasil representasi sebuah gambar seperti gambar berikut. 



Berbeda dengan dataset NLP, sampelnya tentu berupa kalimat-kalimat yang terdiri dari sejumlah kata tertentu seperti gambar di bawah.



Tidak seperti manusia yang bisa mengenali gambar atau memahami kalimat secara langsung, kita perlu melakukan pemrosesan dahulu agar data tersebut siap diterima oleh model. 

Secara umum, ada empat tahapan yang perlu kita lakukan dalam memproses data.

Ubah dataset ke dalam bentuk larik/array. Yup, larik berisi angka-angka adalah format data yang dapat diterima oleh model kita. Sama seperti pada kelas Belajar Machine Learning untuk Pemula, model kita menerima gambar sebagai matriks atau larik 2 dimensi.
Pisahkan atribut dan label pada data. Model kita akan mempelajari korelasi antara atribut dan label pada dataset.
Ubah skala data dalam skala yang seragam. Nama teknik ini adalah normalization. Normalization dilakukan karena NN akan memproses nilai yang berada di antara 0 dan 1  sehingga membuat komputasi lebih optimal.
Terakhir, pisahkan dataset ke dalam data latih dan data uji. Betul, kita memerlukan data uji untuk mengevaluasi kinerja dari model yang telah kita latih.


Menggunakan Model untuk Melakukan Prediksi
Anda dapat melakukan prediksi dengan menggunakan kode berikut.

model.predict([4, 5])
Ketika kita menjalankan kode di atas, hasil yang kita dapat seharusnya adalah 13 dan 14 di mana f(4) = 4 + 9 dan f(5) = 5 + 9. Namun, ketika kita menjalankan kode tersebut, output yang dihasilkan adalah seperti di bawah ini.

1/1 [==============================] - 0s 40ms/step

array([[12.999903],

       [13.999887]], dtype=float32)

Jika Anda amati secara saksama, nilai yang dihasilkan ketika menjalankan fungsi prediksi hanya mendekati angka 13 dan 14 tidak 100% presisi. Kenapa demikian? Karena neural  network tidak memprediksi kepastian melainkan menghitung probabilitas yang terjadi. Pada kasus kita, neural network mempelajari bahwa pola yang terdapat pada dataset kemungkinan adalah x + 9 sehingga prediksi yang dihasilkan adalah probabilitas yang mendekati angka 13 dan 14. Semakin banyak data yang dilatih maka tingkat error training juga semakin rendah sehingga prediksi dari neural network akan semakin mendekati 13 dan 14.

Karena kita memiliki nilai loss yang sangat kecil, Anda dapat menggunakan fungsi .round() agar mengembalikan nilai dengan lebih presisi. Namun, tentunya ini akan menjadi resiko ketika kita memiliki loss function yang besar karena akan menjadi noise pada hasil prediksi yang kita lakukan sehingga hasilnya akan mengembalikan nilai sesuai dengan input yang sebelumnya kita latih.

model.predict([4, 5]).round()
######################
Output
1/1 [==============================] - 0s 41ms/step
array([[13.],
       [14.]], dtype=float32)
Hasil yang diberikan pada kode di atas sangat membuat developer lega karena dapat menghitung fungsi dengan sangat baik. Ke depannya, ketika Anda mendapatkan soal yang sama dengan jumlah yang sangat banyak, cukup panggil fungsi predict, lalumodel machine learning akan mengembalikan nilai sesuai dengan jawabannya. 



Model Sekuensial dengan Beberapa Layer
Pada kode di bawah, kita memanggil fungsi dense sebanyak empat kali yang menunjukkan bahwa model kita memiliki empat buah layer. Layer pertama hanya memiliki 20 buah perceptron, layer kedua memiliki 15 buah perceptron, layer ketiga memiliki tiga buah perceptron, dan layer terakhir memiliki satu buah perceptron. Ingat, layer pertama dari model sequential harus memiliki parameter input_shape agar model bisa mengenali bentuk input yang akan diterimanya.

model = tf.keras.Sequential([
    tf.keras.layers.Dense(units=20, input_shape=[1]),
    tf.keras.layers.Dense(units=15),
    tf.keras.layers.Dense(units=10),
    tf.keras.layers.Dense(units=1)
    ])
Selanjutnya, mari kita lakukan pelatihan sesuai dengan materi sebelumnya sehingga menghasilkan loss seperti berikut.



Silakan coba kode di atas pada latihan yang telah kita kerjakan pada materi sebelumnya dan lihat perbedaannya. Lalu, mari kita bandingkan loss yang dihasilkan ketika menggunakan satu buah layer dan empat buah layer pada tabel berikut.

 	
Satu Layer

Empat Layer

Loss

2.6231e-07

2.0464e-13

Loss

0.00000026231

0.00000000000020464

Perhatikan tabel di atas, tentunya dengan cepat kita dapat melihat perbedaan loss dari kedua kasus tersebut. Sekarang, Anda dapat membuat sebuah model neural network dengan jumlah layer lebih dari satu. Selanjutnya, lakukanlah eksplorasi mandiri untuk melihat hasil lainnya dari perbedaan jumlah layer dan parameter di dalamnya.



Plot Loss dan Akurasi dari Trained Model
Untuk melihat bagaimana plot bekerja mari kita kerjakan latihan berikut. Kita akan menggunakan dataset dan model yang sama dengan latihan sebelumnya. Anda dapat menggunakan latihan sebelumnya dan menambahkan kode-kode berikut di bawah latihan sebelumnya.

import matplotlib.pyplot as plt
Matplotlib.pyplot merupakan sebuah modul dalam library Matplotlib yang menyediakan antarmuka untuk membuat visualisasi data dalam bentuk grafik atau plot. Pada latihan ini kita akan membuat sebuah plot dari objek history. Objek history menampung informasi dari akurasi dan loss model pada setiap epoch di proses pelatihan dengan tipe data dictionary sehingga kita bisa membuat plot akurasi atau loss. 

Masih ingatkan cara memanggil key pada dictionary? Untuk mengakses loss kita bisa memanggil fungsi history pada objek history dan menentukan metrik loss yang akan diambil.

plt.plot(hist.history['loss'])
plt.title('Model loss')
plt.ylabel('Loss')
plt.xlabel('Epoch')
plt.legend(['Train'], loc='upper right')
plt.show()


Dari hasil plot loss di atas, Anda dapat melihat bahwa loss model berkurang sangat signifikan dari epoch pertama sampai epoch ke-100. Lalu, bagaimana dengan plot akurasi? Karena kita sudah menampung akurasi pada model history, kita bisa memilih metrik accuracy pada fungsi history dengan kode yang sama.

plt.plot(hist.history['accuracy'])
plt.title('Model accuracy')
plt.ylabel('Accuracy')
plt.xlabel('Epoch')
plt.legend(['Train'], loc='lower right')
plt.show()


Dari hasil plot di atas, Anda dapat melihat bahwa akurasi model stagnan pada epoch di sekitar 20 dan juga kembali stagnan pada epoch di atas 80. Dengan menyimpan informasi pada tahap pelatihan model, kita dapat melihat performa model dengan jauh lebih nyaman bukan? Mari bandingkan jika kita tidak menggunakan plot sebagai visualisasi performa model.



Seperti yang dapat Anda lihat pada gambar di atas, kita perlu melihat setiap epochs dan membandingkan satu demi satu metrik yang ada. Tentunya ini akan sangat melelahkan dan menghabiskan waktu. Oleh karena itu, plot hadir untuk meminimalisasi hal tersebut dan mempermudah pekerjaan kita sebagai engineer untuk melakukan evaluasi pada model yang dibangun.



Mencegah Overfitting dengan Dropout dan Batch Normalization.
Overfitting pada machine learning dapat terjadi ketika data pelatihan yang kita miliki terlalu sedikit dan tidak merepresentasikan semua kemungkinan dari nilai sesungguhnya. Kondisi lainnya adalah ketika kita memiliki data pelatihan yang sangat banyak, tetapi memiliki informasi yang tidak relevan dengan data di lapangan. Hal ini menyebabkan model harus mempelajari data yang kompleks tetapi tidak memiliki pola yang berguna.

Penyebab di atas juga berlaku pada jaringan saraf tiruan. Terus, apa solusinya dan bagaimana kita mengetahui kualitas dari model neural network? Tenang saja, Anda sudah berada di jalur yang tepat. Pada latihan sebelumnya, kita sudah memisahkan data latih dan data uji sehingga kualitas model melalui evaluasi yang sudah dilakukan dapat terlihat.

Dropout
Salah satu cara mencegah overfitting adalah dengan menggunakan dropout. Dropout adalah fungsi standar yang umum digunakan industri untuk mencegah overfitting. Seperti yang kita ketahui, semakin kompleks sebuah model machine learning, semakin tinggi kemungkinan model tersebut mengalami overfitting. Dropout bekerja dengan cara mengurangi kompleksitas model neural network tanpa mengubah arsitektur model tersebut.

Untuk mengimplementasikan dropout sendiri sangatlah mudah jika menggunakan Keras. Anda cukup menambahkan layer dropout pada hidden layer di model yang sedang dibuat. Agar lebih jelas perhatikan contoh berikut.

from keras.layers import Dense, Dropout
model = Sequential([
                    Dense(64, activation='relu', input_shape=(4,)),
                    Dense(64, activation='relu'),
                    Dropout(0,5),
                    Dense(3, activation='softmax')])
Untuk menggunakan dropout, kita cukup menambahkan fungsi layer tf.keras.layers.Dropout() dan mengisi parameter berupa persentase yang kita inginkan seperti di atas. Dropout akan otomatis menghilangkan jumlah neuron yang aktif pada layer sebelumnya.



Batch Normalization
BatchNormalization adalah layer yang digunakan dalam jaringan saraf tiruan (neural network) untuk mempercepat konvergensi pelatihan dan mengurangi sensitivitas terhadap inisialisasi parameter. Layer ini bekerja dengan melakukan normalisasi input dari layer sebelumnya pada setiap batch sehingga memungkinkan pelatihan yang lebih stabil dan cepat.

Untuk mengimplementasikan BatchNormalization sendiri sangatlah mudah dengan menggunakan Keras. Anda cukup menambahkan layer BatchNormalization pada model neural network. Agar lebih jelas lihatlah contoh di bawah.

from keras.layers import Dense, Dropout, BatchNormalization
model = Sequential([
                    Dense(64, activation='relu', input_shape=(4,)),
                    Dense(64, activation='relu'),
                    Dropout(0,5),
                    BatchNormalization(momentum=0.99),
                    Dense(3, activation='softmax')])
Pada contoh di atas, kita menggunakan salah satu parameter yaitu momentum. Momentum pada BatchNormalization mengacu pada parameter yang dapat mengontrol perhitungan nilai rata-rata dan varians yang dihitung pada setiap batch selama proses pelatihan model. Dengan menggunakan momentum, nilai rata-rata dan varians dihitung berdasarkan gabungan dari nilai-nilai rata-rata dan varians dari mini-batch saat ini dan nilai-nilai sebelumnya yang telah disesuaikan.

Ketika melakukan normalisasi, kita tidak hanya menggunakan nilai dari satu batch saja, tetapi juga mempertimbangkan nilai beberapa batch sebelumnya untuk mendapatkan estimasi yang lebih stabil dari rata-rata dan varians. Ini membantu mengurangi fluktuasi yang mungkin terjadi dalam statistik batch dan meningkatkan konsistensi normalisasi.

Nilai momentum ini sering kali disetel di antara 0,1 dan 0,999. Nilai yang lebih tinggi menunjukkan bahwa kita lebih bergantung pada nilai sebelumnya daripada nilai dari batch saat ini. Sebagai contoh, jika momentum diatur ke 0,9, 90% informasi dari batch sebelumnya akan digunakan dan hanya 10% dari statistik batch saat ini yang akan dipertimbangkan.

Penggunaan momentum pada BatchNormalization membantu menghasilkan data yang lebih stabil dan dapat meningkatkan kinerja pelatihan pada model jaringan saraf tiruan. 

Meskipun BatchNormalization dapat membantu mengurangi overfitting, ini bukan jaminan bahwa model tidak akan mengalami overfitting. Overfitting masih dapat terjadi jika model terlalu kompleks untuk jumlah data pelatihan yang sedikit. Selain itu, ada kemungkinan juga terdapat banyak noise pada data, atau jika ada masalah lainnya dengan proses pelatihan.



Optimasi Pelatihan menggunakan Callbacks
Fungsi callbacks membantu kita untuk memberi tahu model agar berhenti melakukan pelatihan ketika sudah mencapai target tertentu. Nah, langsung saja kita praktik menggunakan callbacks. Kita masih menggunakan dataset dan model dari latihan klasifikasi iris pada materi sebelumnya. Kode utuhnya seperti di bawah ini.

import pandas as pd
from sklearn import preprocessing
from sklearn.model_selection import train_test_split
from keras.models import Sequential
from keras.layers import Dense, Dropout, BatchNormalization
import tensorflow as tf
df = pd.read_csv('https://drive.google.com/uc?id=1roJ83AbgzDcvRr0Gwud0BmdUQx-oSG-w')
df = df.drop(columns='Id')
category = pd.get_dummies(df.Species, dtype=int)
new_df = pd.concat([df, category], axis=1)
new_df = new_df.drop(columns='Species')
dataset = new_df.values
# Pilih 4 kolom pertama untuk dijadikan sebagai atribut
X = dataset[:,0:4]
# Pilih 3 kolom terakhir sebagai label
y = dataset[:,4:7]
# Normalisasi
min_max_scaler = preprocessing.MinMaxScaler()
X_scale = min_max_scaler.fit_transform(X)
X_scale
X_train, X_test, Y_train, Y_test = train_test_split(X_scale, y, test_size=0.3)
from keras.layers import Dense, Dropout, BatchNormalization
model = Sequential([
                    Dense(64, activation='relu', input_shape=(4,)),
                    Dense(64, activation='relu'),
                    Dropout(0,5),
                    BatchNormalization(momentum=0.99),
                    Dense(3, activation='softmax')])
model.compile(optimizer='Adam',
              loss='categorical_crossentropy',
              metrics=['accuracy'])
hist = model.fit(X_train, Y_train, epochs=100)
Setelah semuanya siap, kita perlu membuat sebuah kelas bernama myCallback(). Perhatikan baik-baik. Parameter pertama pada kelas callbacks di atas harus memiliki sifat inherit tf.keras.callbacks.Callback. Selanjutnya, kita buat fungsi yang paling penting yaitu on_epoch_end(). Fungsi inilah yang akan berperan untuk memberi tahu model agar berhenti melakukan pelatihan ketika telah mencapai target.

Kode if(logs.get(‘accuracy’)>0.9) sangat intuitif menunjukkan kalau kode itu memiliki arti “jika akurasi lebih besar dari 0.9, maka eksekusi perintah berikutnya”. Kita juga dapat menulis kode print(“\nAkurasi telah mencapai >90%!”) untuk ditampilkan ketika callbacks aktif.

Kode self.model.stop_training = True adalah kode yang memberi tahu model untuk menghentikan pelatihan. Setelah kelas ini dibuat, buatlah objek dari kelas tersebut. Berikut kode lengkap untuk membuat callbacks.

class myCallback(tf.keras.callbacks.Callback):
  def on_epoch_end(self, epoch, logs={}):
    if(logs.get('accuracy')>0.9):
      print("\nAkurasi telah mencapai >90%!")
      self.model.stop_training = True
callbacks = myCallback()
Setelah membuat sebuah objek callbacks, selanjutnya kita harus menambahkan hyperparameter tersebut pada saat melakukan proses pelatihan. Untuk menggunakan callbacks sangat gampang, kita hanya perlu menambahkan parameter callbacks dan mengisi objek callbacks yang telah kita buat pada parameter tersebut.

hist = model.fit(X_train, Y_train, epochs=100, callbacks = [callbacks])
Hasil dari menjalankan kode tersebut pada model sederhana dapat dilihat pada gambar di bawah ini.



Dari latihan di atas dapat dilihat model berhasil menghentikan pelatihan ketika telah mencapai akurasi yang kita tentukan pada epoch ke 5 dari 100. Kita telah menghemat waktu eksekusi sebanyak 96 epoch. Keren, bukan?



Menggunakan Dataset dari TensorFlow
Seperti yang telah kita lakukan pada materi sebelumnya, TensorFlow juga menyediakan dataset yang siap dipakai yang dapat digunakan untuk belajar/eksplorasi. Anda dapat mengunjungi tautan TensorFlow Datasets untuk melihat dataset apa saja yang tersedia dari library TensorFlow. 

Ada dua cara untuk mengakses dataset yang sudah disediakan TensorFlow yaitu melalui tf.data.Datasets dan juga TensorFlow Datasets. Keduanya memiliki fungsi yang sangat mudah digunakan tetapi memiliki variasi data yang berbeda.

Menggunakan tf.data.Datasets
As usual, hal pertama yang kita lakukan adalah melakukan impor library TensorFlow agar dapat mengakses seluruh fungsi yang ada.

import tensorflow as tf
Kemudian kita buat objek untuk menampung dataset kita dan masukkan fungsi tf.keras.datasets.<nama_dataset> pada objek tersebut. Karena pada kasus ini menggunakan dataset mnist, kode yang digunakan sebagai berikut.

mnist = tf.keras.datasets.mnist
Selanjutnya, kita perlu membagi dataset yang sudah ada menjadi dua bagian yaitu pelatihan dan uji menggunakan fungsi load_data(). Fungsi load_data() dari objek dataset mengembalikan bentuk dataset yang telah dibagi menjadi atribut latih, label latih, atribut uji, dan label uji. Sangat gampang, bukan? Hanya dengan beberapa baris kode kita sudah memiliki data latih dan data uji yang siap dipakai.

(gambar_latih, label_latih), (gambar_testing, label_testing) = mnist.load_data()




Menggunakan TensorFlow Datasets
TensorFlow menyediakan kumpulan dataset siap pakai untuk dilatih dengan TensorFlow, Jax, dan framework machine learning lainnya. TensorFlow Dataset (TFDS) bertugas untuk melakukan pengunduhan dan menyiapkan data secara deterministik dengan menggunakan tf.data.Dataset (atau np.array).

Sebelumnya, kita sudah mempelajari tf.data.Datasets, sekarang kita mengenal rivalnya yaitu TFDS. Namanya, cukup mirip, ya? Jangan bingung antara TFDS (library ini) dengan tf.data.Datasets (API dari TensorFlow). 

TFDS adalah wrapper tingkat tinggi di sekitar tf.data. Jika Anda tidak terbiasa dengan API ini, kami menyarankan Anda untuk membaca panduan resmi dari TensorFlow pada tautan berikut: tf.data.

Di sisi lain, TFDS juga menyediakan lebih banyak datasets yang siap digunakan. Tanpa berlama-lama, mari kita mulai perjalanan ini dengan melakukan impor library yang akan digunakan.

import matplotlib.pyplot as plt
import numpy as np
import tensorflow as tf
import tensorflow_datasets as tfds
Setelah berhasil menginstal library TFDS, kita dapat melihat list atau daftar dari dataset yang tersedia pada TFDS. Untuk melihat seluruh dataset yang tersedia, kita bisa menggunakan fungsi tfds.list_builders() atau dapat dilihat pada katalog TensorFlow Datasets.

tfds.list_builders()


Seperti yang Anda lihat pada gambar di atas, ada banyak sekali dataset yang tersedia ketika kita menggunakan TFDS, baik itu untuk pembelajaran maupun eksplorasi mandiri. Setelah melihat banyak sekali dataset, tentunya kita harus menentukan dataset mana yang akan digunakan, bukan? Tenang saja, caranya sangat mudah. Kita hanya perlu menggunakan fungsi tfds.load() seperti berikut.

ds = tfds.load('mnist', split='train', shuffle_files=True)
assert isinstance(ds, tf.data.Dataset)
Kode di atas memuat dataset MNIST menggunakan TensorFlow Datasets. Mari kita jelaskan satu per satu detail dari kode di atas.

Fungsi load() memungkinkan Anda untuk menggunakan dataset yang telah disediakan oleh TensorFlow Datasets. 
Parameter pertama ('mnist') menunjukkan nama dataset yang ingin dimuat. 
Parameter kedua ('split='train'') menunjukkan bahwa kita hanya memuat bagian pelatihan dari dataset MNIST. 
Parameter ketiga ('shuffle_files=True') mengindikasikan bahwa file-file dataset akan diacak sebelum dimuat, sehingga urutan data tidak akan tetap sama setiap kali dataset dimuat ulang. 
Pada hakikatnya masih ada argumen umum yang sering digunakan ketika melakukan load dataset menggunakan tfds. Untuk mengetahui lebih detail, Anda dapat melihat pada website resminya TensorFlow Loads, ya.



Penggunaan Batch Loading
Batch loading adalah proses pelatihan ketika neural network melakukan pembaruan parameternya (weight) setelah membaca sejumlah sampel data tertentu. Misal dataset kita berisi 800 buah gambar pizza. Tanpa batch size, proses pembaruan parameter terjadi untuk seluruh sampel pada dataset. Sehingga, ketika tanpa menggunakan batch size, pada 1 epoch terdapat 800 kali pembaruan weight. Ketika 1 ukuran batch adalah 32 buah gambar pizza, terdapat 25 buah batch pada dataset. Pada batch loading, model baru melakukan pembaruan parameter setelah membaca satu batch atau 32 buah gambar pizza. Sehingga, proses pembaruan parameter pada 1 epoch hanya sebanyak 25 kali.



Apakah Anda sudah menyadari apa fungsi dari batch loading? Yup benar, dengan batch loading proses pelatihan data akan menjadi lebih cepat. Kita akan melihat langsung kegunaan dari batch loading pada latihan berikut.

Untuk dataset, kita akan menggunakan dataset mnist dan model yang sama dengan materi sebelumnya.  

import tensorflow as tf
mnist = tf.keras.datasets.mnist
(training_images, training_labels), (test_images, test_labels) = mnist.load_data()
training_images  = training_images / 255.0
test_images = test_images / 255.0
model = tf.keras.models.Sequential([tf.keras.layers.Flatten(input_shape=(28,28)), 
                                    tf.keras.layers.Dense(128, activation=tf.nn.relu), 
                                    tf.keras.layers.Dense(10, activation=tf.nn.softmax)])
model.compile(optimizer = tf.optimizers.Adam(),
              loss = 'sparse_categorical_crossentropy',
              metrics=['accuracy'])
Selanjutnya, buatlah fungsi fit() untuk melakukan pelatihan. Perlu Anda perhatikan, di sini kita mulai menggunakan batch loading. Untuk menggunakan batch loading, kita hanya menambahkan satu parameter ‘batch_size’ pada fungsi fit(). 

Tahukah Anda bahwa fungsi fit() secara default menggunakan batch loading dengan batch size sebesar 32. Sehingga, ketika kita tidak mendefinisikan nilai parameter batch_size, ukuran batch akan diisi sebesar 32 secara default. Perhatikan bahwa pada setiap epoch memakan waktu selama sekitar 3 atau 4 detik.

model.fit(training_images, training_labels, batch_size=32, epochs=5)


Agar lebih paham, sekarang kita akan menggunakan batch_size yang lebih besar yaitu 128. Dapat kita lihat bahwa semakin besar batch size, waktu eksekusi tiap epoch akan semakin cepat. 

model.fit(training_images, training_labels, batch_size=128, epochs=5)


Seperti yang Anda lihat di atas, waktu pelatihan yang dilakukan memakan waktu yang lebih singkat. Silakan Anda bereksperimen menggunakan batch size yang lain untuk pengalaman belajar yang lebih maksimal. Bagaimana hasilnya? Silakan beri kesimpulan sendiri, ya. 

Pada latihan ini, kita telah memahami bahwa dengan menggunakan batch loading dapat mempercepat pelatihan. Untuk pemilihan batch size sendiri tidak ada aturan bakunya, tetapi yang umum dipakai adalah 32, 64, dan 128. Anda harus bereksperimen sendiri guna menemukan batch size yang cocok dengan masalah atau model yang sedang dibangun.

Berikut adalah penyatuan materi dari ketiga dokumen (_Convolutional Neural Network (CNN)_, _Recurrent Neural Network (RNN)_, dan _Glosarium Deep Learning_) yang telah disusun secara runut, terstruktur, dan rapi:

# Modul Pembelajaran: Arsitektur Deep Learning dan Glosarium

## 1. Arsitektur Jaringan Berbasis Visual: Convolutional Neural Network (CNN)

_Convolutional Neural Network_ (CNN) adalah arsitektur _deep learning_ yang dirancang secara khusus untuk memproses data visual dan gambar secara efisien. Arsitektur ini bekerja dengan mengekstrak hierarki fitur visual dari tingkat rendah hingga tingkat tinggi secara bertahap.

### Karakteristik Utama Lapisan CNN

- **Lapisan Konvolusi (_Convolutional Layer_)**: Lapisan inti yang menggunakan filter/kernel konvolusi untuk memindai gambar dan mengekstrak fitur lokal seperti sudut, tepi, atau tekstur, yang kemudian menghasilkan peta fitur (_feature map_).
    
- **Lapisan Pooling (_Pooling Layer_)**: Lapisan yang bertugas mereduksi dimensi spasial dari peta fitur guna meringankan beban komputasi serta mencegah _overfitting_, baik melalui metode nilai maksimum (_max pooling_) maupun rata-rata (_average pooling_).
    
- **Lapisan Aktivasi (_Activation Layer_)**: Menggunakan fungsi aktivasi nonlinier, umumnya ReLU (_Rectified Linear Unit_), untuk memungkinkan model mempelajari pola-pola nonlinier yang kompleks.
    
- **Lapisan Terhubung Penuh (_Fully Connected / Dense Layer_)**: Lapisan saraf di bagian akhir jaringan yang meratakan fitur dan melakukan klasifikasi akhir berdasarkan representasi visual yang telah diekstraksi.
    

### Penggunaan Umum CNN

- **Klasifikasi Citra**: Mengelompokkan gambar ke dalam kategori tertentu, misalnya pengenalan angka tulisan tangan.
    
- **Pengenalan Objek dan Wajah**: Mendeteksi dan mengidentifikasi keberadaan objek atau wajah pada bidang gambar.
    
- **Segmentasi Citra**: Memisahkan batas objek spesifik dari latar belakang gambar.
    

## 2. Arsitektur Jaringan Berbasis Sekuensial: Recurrent Neural Network (RNN) dan Variannya

_Recurrent Neural Network_ (RNN) adalah kelas arsitektur jaringan saraf yang dirancang khusus untuk memproses data berurutan (_sequential_) dan deret waktu (_time series_), di mana urutan data memiliki konteks temporal atau saling ketergantungan. Keunggulan utamanya terletak pada loop rekursif yang memungkinkannya mempertahankan memori atau konteks historis dari urutan data sebelumnya.

### Tipe-Tipe Aliran Data RNN (Berdasarkan Panjang Input-Output)

1. **One-to-One**: Jaringan standar dengan satu input dan satu output.
    
2. **One-to-Many**: Menerima satu input dan menghasilkan serangkaian output, contohnya pada pembuatan deskripsi otomatis untuk gambar (_image captioning_).
    
3. **Many-to-One**: Mengambil rangkaian urutan input dan memproyeksikannya menjadi satu output, umum dipakai dalam analisis sentimen teks.
    
4. **Many-to-Many**: Menerima urutan input ganda dan menghasilkan urutan output ganda, seperti pada mesin penerjemah bahasa.
    

### Varian Arsitektur RNN

- **Vanilla RNN (RNN Sederhana)**:
    
    - Bentuk dasar RNN di mana setiap neuron memiliki koneksi berulang ke dirinya sendiri.
        
    - Rentan terhadap kendala hilangnya gradien (_vanishing gradient problem_), sehingga sulit menangani dependensi urutan jangka panjang.
        
- **Long Short-Term Memory (LSTM)**:
    
    - Dirancang khusus untuk mengatasi _vanishing gradient_ dengan memperkenalkan mekanisme gerbang (_gates_) dan _cell state_.
        
    - **Forget Gate**: Berfungsi menyeleksi dan membuang informasi lama yang sudah tidak relevan.
        
    - **Input Gate**: Mengontrol informasi baru yang akan disimpan ke dalam memori jangka panjang.
        
    - Cocok untuk tugas NLP tingkat lanjut dan pemrosesan sinyal audio.
        
- **Gated Recurrent Unit (GRU)**:
    
    - Varian ringkas dari LSTM yang menggabungkan status ke dalam _hidden state_ tanpa memiliki _cell state_ terpisah.
        
    - Menggunakan dua gerbang utama: _update gate_ dan _reset gate_ untuk mengatur aliran informasi.
        
    - Memiliki parameter lebih sedikit sehingga proses pelatihan berlangsung lebih cepat dibanding LSTM.
        

### Tahapan dan Alur Kerja RNN

1. **Pengolahan Input**: Elemen berurutan dimasukkan satu demi satu ke dalam model setelah diubah menjadi representasi vektor numerik (misalnya _word embedding_).
    
2. **Perhitungan Aktivasi**: Unit neuron menghitung nilai aktivasi berdasarkan input langkah saat ini dan status (_state_) dari langkah sebelumnya menggunakan fungsi aktivasi seperti `tanh` atau `sigmoid`.
    
3. **Pembaruan Status Internal**: Memperbarui status memori internal melalui operasi perkalian matriks bobot dan penambahan bias.
    
4. **Generasi Output**: Model menghasilkan nilai luaran pada tiap langkah waktu untuk kebutuhan prediksi langkah selanjutnya maupun hasil akhir sekuens.
    

## 3. Arsitektur Deep Learning Tingkat Lanjut Lainnya

Selain CNN dan RNN, terdapat arsitektur khusus lain yang banyak diterapkan dalam industri AI modern:

- **Transformer**:
    
    - Arsitektur berbasis mekanisme atensi mandiri (_self-attention_) yang mampu memproses hubungan kata dalam teks secara paralel tanpa batasan jarak dependensi.
        
    - Terdiri dari blok _encoder_ dan _decoder_ untuk tugas pemodelan bahasa dan terjemahan mesin lintas bahasa.
        
- **Generative Adversarial Network (GAN)**:
    
    - Arsitektur generatif yang melatih dua model saraf secara simultan dan kompetitif.
        
    - **Generator**: Menghasilkan data sintetis (misalnya gambar realistis) dari distribusi laten.
        
    - **Diskriminator**: Mengevaluasi dan membedakan antara data nyata dengan data buatan generator.
        
    - Sering digunakan untuk sintesis citra kreatif dan augmentasi dataset.
        
- **Autoencoder**:
    
    - Jaringan nir-pengawasan (_unsupervised_) yang terdiri dari komponen _Encoder_ (memampatkan data input ke representasi laten dimensi rendah) dan _Decoder_ (merekonstruksi kembali data asli).
        
    - Berfungsi dalam reduksi dimensi serta penghilangan derau data (_denoising_).
        

## 4. Glosarium Terminologi Machine Learning & Deep Learning

### A

- **A/B Testing**: Pengujian statistik untuk membandingkan performa dua atau lebih teknik/model.
    
- **Action**: Keputusan atau tindakan yang diambil oleh agen dalam _reinforcement learning_.
    
- **Activation Function**: Fungsi matematika yang memproses penjumlahan berbobot input untuk menentukan nilai keluaran neuron ke lapisan berikutnya (contoh: ReLU, Sigmoid).
    
- **Agent**: Entitas otonom pembuat keputusan dalam _reinforcement learning_.
    
- **Akurasi**: Rasio prediksi yang benar terhadap total seluruh data uji.
    
- **Anomaly Detection**: Teknik identifikasi pola data yang menyimpang secara signifikan dari pola umum.
    

### B

- **Bobot (_Weight_)**: Parameter yang dipelajari model untuk menentukan kekuatan atau tingkat kepentingan hubungan antar-neuron.
    

### C

- **Callbacks**: Utilitas yang mengeksekusi instruksi tertentu pada berbagai tahap pelatihan model (misalnya menghentikan iterasi di akhir epoch).
    
- **Clustering**: Pengelompokan data tanpa label ke dalam beberapa klaster berdasarkan tingkat kemiripannya.
    
- **Collaborative Filtering**: Metode sistem rekomendasi berdasarkan kesamaan preferensi antarpengguna.
    
- **Content-based Filtering**: Sistem rekomendasi yang memanfaatkan atribut/fitur inheren dari suatu objek.
    

### D

- **Data Kategorik**: Fitur bernilai diskrit yang terbagi ke dalam kelompok tertentu.
    
- **Data Numerik**: Fitur kontinu berupa bilangan riil atau bulat.
    
- **Data Time Series**: Rangkaian observasi data yang tercatat berdasarkan interval waktu tertentu secara berurutan.
    
- **Dataset**: Kumpulan data terstruktur yang memuat satu atau beberapa fitur.
    
- **Deep Learning**: Subbidang _machine learning_ berbasis jaringan saraf tiruan berlapis banyak yang mampu mempelajari data kompleks.
    
- **Deep Neural Network**: Jaringan saraf tiruan yang memiliki lebih dari satu _hidden layer_.
    
- **Deployment**: Proses integrasi model yang telah dilatih ke lingkungan produksi operasional.
    
- **Dropout Regularization**: Teknik regularisasi dengan menonaktifkan sejumlah neuron secara acak selama pelatihan guna mengatasi _overfitting_.
    

### E

- **Embeddings**: Pemetaan representasi fitur kategorik atau teks ke dalam vektor ruang dimensi rendah secara kontinu.
    
- **Environment**: Lingkungan interaksi agen dalam _reinforcement learning_ yang memberikan observasi dan imbalan.
    
- **Epoch**: Satu putaran penuh proses pelatihan yang melewati seluruh sampel dalam dataset.
    

### F

- **Federated Learning**: Pendekatan pelatihan model terdesentralisasi yang mengutamakan privasi tanpa memusatkan data sensitif.
    
- **Feedback**: Kondisi di mana keluaran atau prediksi model memengaruhi siklus data pelatihan berikutnya.
    
- **Fitur (_Feature_)**: Variabel masukan yang digunakan model untuk membuat prediksi.
    

### G

- **Good Fit**: Keadaan ideal saat model mampu menggeneralisasi data pelatihan dan data baru secara optimal.
    

### H

- **Hidden Layer**: Lapisan neuron tersembunyi yang terletak di antara lapisan input dan output.
    
- **Hyperparameter**: Variabel konfigurasi eksternal yang diatur sebelum pelatihan untuk mengontrol proses belajar (contoh: _learning rate_, _epoch_).
    

### I

- **Image Augmentation**: Teknik memperkaya data latih visual secara artifisial melalui transformasi geometris gambar.
    
- **Input Layer**: Lapisan pertama penerima data masukan pada jaringan saraf.
    
- **Input_shape**: Parameter dimensi bentuk masukan data yang dapat diterima oleh lapisan pertama model.
    

### K

- **Keras**: Pustaka API tingkat tinggi berbasis Python untuk membangun dan melatih jaringan saraf.
    
- **Klasifikasi**: Model pembelajaran terarah (_supervised_) untuk memprediksi kategori kelas.
    

### L

- **Label**: Variabel target atau jawaban benar dari suatu sampel data.
    
- **Layer**: Kumpulan simpul neuron yang memproses input dan menghasilkan output pada arsitektur jaringan.
    
- **LSTM (_Long Short-Term Memory_)**: Varian sel RNN yang dirancang khusus untuk menyimpan konteks data urutan panjang.
    

### M

- **Machine Learning**: Bidang komputasi yang memberi sistem kemampuan belajar dari pola data tanpa instruksi terprogram eksplisit.
    
- **MAE (_Mean Absolute Error_)**: Metrik evaluasi rata-rata selisih absolut antara nilai prediksi dan nilai aktual.
    
- **Matplotlib**: Pustaka visualisasi grafik 2 dimensi di Python.
    
- **Model**: Struktur representasi hubungan antara variabel fitur dan label yang terbentuk dari proses pelatihan.
    
- **MSE (_Mean Squared Error_)**: Metrik evaluasi rata-rata kuadrat selisih antara nilai prediksi dan nilai aktual.
    

### N

- **Neural Network**: Model komputasi terinspirasi struktur otak yang tersusun dari neuron buatan saling terhubung.
    
- **Normalization**: Penyesuaian rentang data numerik ke skala standar (biasanya 0 hingga 1).
    

### O

- **One-Hot Encoding**: Representasi variabel kategorik ke dalam bentuk vektor biner kolom terpisah.
    
- **Optimizer**: Algoritma komputasi untuk memperbarui bobot model selama proses penurunan gradien.
    
- **Outlier**: Titik data ekstrem yang menyimpang jauh dari distribusi kumpulan data umum.
    
- **Output Layer**: Lapisan terakhir jaringan saraf yang menyajikan hasil prediksi akhir.
    
- **Overfitting**: Kondisi ketika model menghafal data latih terlalu detail sehingga gagal memprediksi data baru secara akurat.
    

### P

- **Pandas**: Pustaka manipulasi dan analisis data berbasis struktur tabel (Dataframe).
    
- **Parameter**: Variabel internal model (seperti bobot dan bias) yang disesuaikan secara mandiri selama proses pelatihan.
    
- **Policy**: Aturan atau strategi probabilitas yang memandu agen memilih aksi dalam _reinforcement learning_.
    
- **Presisi**: Proporsi prediksi positif model yang terbukti benar terhadap keseluruhan hasil yang diprediksi positif.
    
- **Propagasi Balik (_Backpropagation_)**: Algoritma penghitungan gradien galat secara mundur dari lapisan output ke input untuk memperbarui bobot.
    

### R

- **Recall**: Proporsi data positif aktual yang berhasil dikenali dan diklasifikasikan dengan benar oleh model.
    
- **Reinforcement Learning**: Pembelajaran berbasis interaksi agen dan lingkungan untuk memaksimalkan akumulasi hadiah (_reward_).
    
- **Reward**: Umpan balik numerik positif yang diberikan lingkungan kepada agen atas aksi yang tepat.
    

### S

- **Scikit-learn**: Pustaka pembelajaran mesin sumber terbuka untuk klasifikasi, regresi, prapemrosesan, dan evaluasi model.
    

### T

- **TensorBoard**: Dasbor visualisasi interaktif untuk memantau metrik pelatihan TensorFlow.
    
- **TensorFlow**: Platform komputasi terdistribusi tingkat lanjut dari Google untuk pengembangan model _machine learning_ skala besar.
    
- **TensorFlow.js**: Varian pustaka TensorFlow untuk mengeksekusi model _deep learning_ langsung di peramban web (_browser_) menggunakan format JSON.
    
- **TF-Agent**: Pustaka dari ekosistem TensorFlow untuk mempermudah implementasi algoritma _reinforcement learning_.
    
- **Test Set**: Kumpulan data uji independen untuk mengevaluasi kinerja akhir model setelah fase validasi.
    
- **Tokenisasi**: Proses memecah teks kalimat menjadi unit-unit kata atau token numerik yang lebih mendasar.
    
- **Training Set**: Bagian data utama yang dialokasikan khusus untuk melatih parameter bobot model.
    
- **Transfer Learning**: Pendekatan pemanfaatan bobot model terlatih dari satu tugas untuk diterapkan pada tugas baru.
    

### U

- **Underfitting**: Kondisi performa model yang buruk karena gagal menangkap pola hubungan fundamental dalam data pelatihan.
    
- **Unsupervised Learning**: Paradigma pembelajaran mesin pada data tanpa label untuk mengekstrak struktur atau pola tersembunyi.
    

### V

- **Validation Set**: Subhimpunan data terpisah yang digunakan untuk mengevaluasi model saat proses penyetelan _hyperparameter_ berlangsung.