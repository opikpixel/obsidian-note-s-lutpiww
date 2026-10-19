Dengan menggunakan Keras, kita dapat membuat sebuah model machine learning hanya dengan beberapa baris kode seperti berikut.
```
mnist = tf.keras.datasets.fashion_mnist
 
(x_train, y_train), (x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0
 
model = tf.keras.models.Sequential([
    tf.keras.layers.Flatten(input_shape=(28, 28)),
    tf.keras.layers.Dense(512, activation='relu'),
    tf.keras.layers.Dense(10, activation='softmax')
])
model.compile(optimizer = tf.optimizers.Adam(),
                              loss = ‘sparse_categorical_crossentropy’,
                              metrics = [‘accuracy’])
model.fit(x_train, y_train, epochs = 10)
```
Berikutnya, mari kita flashback sedikit untuk memperjelas kembali tiga layer utama pada model sequential tersebut.

Input layer
Layer yang memiliki parameter ‘input_shape’. Input_shape sendiri adalah resolusi dari gambar-gambar pada data latih. Dalam hal ini, sebuah gambar MNIST memiliki resolusi 28x28 piksel sehingga input shape-nya adalah (28, 28). Sebuah layer Flatten pada Keras akan berfungsi untuk meratakan input. Meratakan di sini artinya mengubah gambar yang merupakan matriks 2 dimensi menjadi larik/array 1 dimensi. Pada kasus kita, sebuah gambar MNIST yang merupakan matriks 28x 28 elemen akan diubah menjadi array satu dimensi sebesar 784 elemen.
Hidden layer
Dense layer pada Keras merupakan layer yang dapat dipakai sebagai hidden layer dan output layer pada sebuah MLP. Parameter unit merupakan jumlah perceptron pada sebuah layer. Kita dapat menggunakan fungsi aktivasi rectified linear unit (Relu) atau fungsi aktivasi lainnya pada layer ini.
Output layer
Layer ini dapat didefinisikan dengan membuat sebuah Dense layer. Jumlah unit menyesuaikan dengan jumlah label pada dataset. Untuk fungsi aktivasi pada layer output, gunakan fungsi aktivasi Sigmoid jika hanya terdapat 2 kelas/label pada dataset. Untuk dataset yang memiliki 3 kelas atau lebih, gunakan fungsi aktivasi Softmax. Fungsi aktivasi softmax akan memilih kelas mana yang memiliki probabilitas tertinggi. Untuk data fashion MNIST, kita akan menggunakan fungsi aktivasi softmax karena terdapat 10 kelas.

ecara umum, ada empat tahapan yang perlu kita lakukan dalam memproses data.

1. Ubah dataset ke dalam bentuk larik/array. _Yup_, larik berisi angka-angka adalah format data yang dapat diterima oleh model kita. Sama seperti pada kelas Belajar Machine Learning untuk Pemula, model kita menerima gambar sebagai matriks atau larik 2 dimensi.
2. Pisahkan atribut dan label pada data. Model kita akan mempelajari korelasi antara atribut dan label pada dataset.
3. Ubah skala data dalam skala yang seragam. Nama teknik ini adalah normalization. Normalization dilakukan karena NN akan memproses nilai yang berada di antara 0 dan 1  sehingga membuat komputasi lebih optimal. Teknik ini dibutuhkan sehingga komputasi lebih optimal.
4. Terakhir, pisahkan dataset ke dalam data latih dan data uji. Betul, kita memerlukan data uji untuk mengevaluasi kinerja dari model yang telah kita latih.

#### Data Augmentasi dengan TensorFlow <= 2.9
ImageDataGenerator merupakan sebuah fungsi yang sangat berguna untuk mempersiapkan data latih dan data validasi. Beberapa kemudahan yang disediakan ImageDataGenerator antara lain, preprocessing data, pelabelan sampel otomatis, dan augmentasi gambar.

Augmentasi gambar merupakan sebuah teknik yang dapat digunakan untuk memperbanyak data latih dengan cara menduplikasi gambar yang telah ada dengan menambahkan variasi tertentu seperti _rescale, rotation, zoom_, dan lain sebagainya. 

Kode berikut menunjukkan proses augmentasi gambar pada setiap sampel di dataset.

1. from tensorflow.keras.preprocessing.image import ImageDataGenerator
2. train_datagen = ImageDataGenerator(
3.                     rescale=1./255,
4.                     rotation_range=20,
5.                     horizontal_flip=True,
6.                     shear_range = 0.2,
7.                     fill_mode = 'nearest')

8. test_datagen = ImageDataGenerator(
9.                     rescale=1./255)