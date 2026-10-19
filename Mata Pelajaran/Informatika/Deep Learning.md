Istilah
- plot loss
## Dropout dan Batch Normalization
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


10. x = -4.0, -3.0, -2.0, -1.0, 0.0, 1.0, 2.0, 3.0, 4.0, 5.0
11. f(x) = 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0, 13.0, 14.0

Sebuah model dari API Keras dapat menerima masukan dengan tipe data numpy array sehingga kita bisa membuat 2 buah objek bertipe numpy array, satu untuk atribut (x) dan satu lagi sebagai labelnya (f(x)). Untuk jenis tipe data lain yang dapat diterima sebagai masukan sebuah model dari API Keras, Anda dapat mengunjungi tautan [berikut](https://www.tensorflow.org/api_docs/python/tf/keras/Model). 

Mari kita mulai dengan melakukan impor library yang akan digunakan seperti kode di bawah ini.

1. import tensorflow as tf
2. import numpy as np
3. from tensorflow import keras
Selanjutnya, kita harus mengubah angka-angka di atas menjadi sebuah larik/array agar dapat diterima oleh Keras sehingga proses pelatihan akan berjalan dengan baik. Kita dapat menggunakan kode berikut untuk mengubahnya menjadi sebuah larik/array.

4. X = np.array([-4.0, -3.0, -2.0, -1.0, 0.0, 1.0, 2.0, 3.0, 4.0, 5.0], dtype=float)
5. Y = np.array([5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0, 13.0, 14.0], dtype=float)
6. model = tf.keras.Sequential([
7.     tf.keras.layers.Dense(units=1, input_shape=[1])
8.     ])

9. model.predict(np.array([4, 5]))

Ketika kita menjalankan kode di atas, hasil yang kita dapat seharusnya adalah 13 dan 14 di mana f(4) = 4 + 9 dan f(5) = 5 + 9. Namun, ketika kita menjalankan kode tersebut, output yang dihasilkan adalah sebagai berikut.

1. 1/1 [==============================] - 0s 40ms/step
2. array([[12.999903],
3.        [13.999887]], dtype=float32)

4. # Opsi 1 (menggunakan dataset lokal)
5. import pandas as pd
6. df = pd.read_csv('citrus.csv')

7. # Opsi 2 (menggunakan dataset dari google drive)
8. df = pd.read_csv('https://drive.google.com/uc?id=1XZbZ5Z7MBXYaR3UO1HbQ4ncPi4R3HsyF')
9. df.head()
10. df.loc[df['name'] == 'grapefruit', 'name'] = 0
11. df.loc[df['name'] == 'orange', 'name'] = 1
12. from sklearn import preprocessing

13. label_encoder = preprocessing.LabelEncoder() 
14. df['name'] = label_encoder.fit_transform(df['name']) 
15. print(df)
16. dataset = df.values
’’’ pilih 5 kolom terakhir sebagai atribut
bilangan sebelum koma untuk memilih baris pada dataframe
bilangan setelah koma untuk memilih kolom pada dataframe ’’’
X = dataset[:,1:6]
Jangan lupa untuk memisahkan label dari dataset. Pada dataset kita, label terdapat pada kolom pertama. Jalankan kode di bawah untuk membuat sebuah array numpy yang hanya berisi label kita.

y = dataset[:,0]
from sklearn import preprocessing
min_max_scaler = preprocessing.MinMaxScaler()
X_scale = min_max_scaler.fit_transform(X)
X_scale
1. from sklearn.model_selection import train_test_split
2. X_train, X_test, Y_train, Y_test = train_test_split(X_scale, y, test_size=0.3)
3. model = Sequential([    
4.                     Dense(32, activation='relu', input_shape=(5,)),    
5.                     Dense(32, activation='relu'),    
6.                     Dense(1, activation='sigmoid')])

mport pandas as pd
from sklearn import preprocessing
from sklearn.model_selection import train_test_split
from keras.models import Sequential
from keras.layers import Dense
Setelah semuanya siap, Anda dapat menambahkan code cell pertama pada notebook yang telah dibuka. Dengan menggunakan pandas untuk kita dapat merubah dataset menjadi sebuah dataframe. Untuk melakukannya, gunakan fungsi read_csv().

df = pd.read_csv('https://drive.google.com/uc?id=1roJ83AbgzDcvRr0Gwud0BmdUQx-oSG-w')
df.head()
df = df.drop(columns='Id')
category = pd.get_dummies(df.Species, dtype=int)
category
new_df = pd.concat([df, category], axis=1)
new_df = new_df.drop(columns='Species')
new_df
1. dataset = new_df.values
2. dataset
3. min_max_scaler = preprocessing.MinMaxScaler()
4. X_scale = min_max_scaler.fit_transform(X)
5. X_scale
6. X_train, X_test, Y_train, Y_test = train_test_split(X_scale, y, test_size=0.3)
7. model = Sequential([    
8.                     Dense(64, activation='relu', input_shape=(4,)),    
9.                     Dense(64, activation='relu'),    
10.                     Dense(3, activation='softmax')])
11. model.compile(optimizer='Adam',
12.               loss='categorical_crossentropy',
13.               metrics=['accuracy'])

14. import matplotlib.pyplot as plt
15. plt.plot(hist.history['loss'])
16. plt.title('Model loss')
17. plt.ylabel('Loss')
18. plt.xlabel('Epoch')
19. plt.legend(['Train'], loc='upper right')
20. plt.show()
21. plt.plot(hist.history['accuracy'])
22. plt.title('Model accuracy')
23. plt.ylabel('Accuracy')
24. plt.xlabel('Epoch')
25. plt.legend(['Train'], loc='lower right')
26. plt.show()

from keras.layers import Dense, Dropout
model = Sequential([
                    Dense(64, activation='relu', input_shape=(4,)),
                    Dense(64, activation='relu'),
                    Dropout(0.5),
                    Dense(3, activation='softmax')])
from keras.layers import Dense, Dropout, BatchNormalization
model = Sequential([
                    Dense(64, activation='relu', input_shape=(4,)),
                    Dense(64, activation='relu'),
                    Dropout(0.5),
                    BatchNormalization(momentum=0.99),
                    Dense(3, activation='softmax')])