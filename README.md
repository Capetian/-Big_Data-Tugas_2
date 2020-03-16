# Big Data - Tugas 2


Nama: Raden Bimo Rizki Prayogo

NRP: 0511740000139


# Exercise 1

## DB Connect

![picture](img\db_connect.JPG)

### Buat koneksi SQLite

![picture](img\sqlite_conf.JPG)

### Select tabel

![picture](img\select_tabel.JPG)

### Baca tabel

![picture](img\db_reader.JPG)

### Optional: konfigurasi koneksi

![picture](img\auth_conf.JPG)

Gunakan credentials configuration untuk menset user dan password koneksi. Node ini akan menghasilkan variabel yang dapat digunakan untuk credential suatu koneksi.


## DB Processing

![picture](img\ex_1_2.JPG)

### Join tabel dan menghilangkan kolom

![picture](img\join.JPG)

Join dengan kolom serial no dengan node DB Joiner dan filter kolom puma* dan pwgtp* dengan node Column filter denagn regex ^((?!puma|pwgtp).*)$

![picture](img\join_conf.JPG)
![picture](img\regex.JPG)

Hasilnya sebagai berikut:

![picture](img\join_res.JPG)

### Filter row

![picture](img\row_filter.JPG)

Filter row dengan cow is null dengan node DB row filter dengan konfigurasi berikut:

![picture](img\cow_null.JPG)

Hasilnya adalah sebagai berikut:

![picture](img\filter_res.JPG)

### Hitung AVG agep berdasarkan sex

![picture](img\avg.JPG)

Gunakan node DB GroupBy dan setting sex sebagai group,agep sebagai kolom aggregasi dan AVG sebagai metode aggregasi.

![picture](img\group1.JPG)
![picture](img\group2.JPG)

Hasil:

![picture](img\group_res.JPG)

### Optional: konfigurasi koneksi

Gunakan node-node berikut:

![picture](img\sort.JPG)

Sorting dengan DB Sorter dan batasi query menjadi 10 dengan DB Query.

Hasil:

![picture](img\sort_res.JPG)

## DB Modelling

![picture](img\modelling.JPG)

Tambahkan Decison Tree Learner dan Predictor ke workflow yang sudah ada.

Berikut adalah konfigurasi yang digunakan:

![picture](img\modelling_learn.JPG)

berikut adalah hasilnya:

![picture](img\modelling_res.JPG)

## DB Write

Gunakan node DB Write untuk membuat tabel baru dan node DB Update untuk menambahkan/ mengedit data pada suatu tabel

![picture](img\write.JPG)

Hasil update:

![picture](img\write_res.JPG)

Hasil backup:
![picture](img\backup.JPG)

Hasil model:
![picture](img\write_model.JPG)


# Exercise 2

## Koneksi Hive

![picture](/img/hive_set.JPG)


### Siapkan folder temp untuk dijadikan HDFS

![picture](/img/to_hdfs.JPG)

Node Create Temp Dir membuat folder di temp sedangkan node String Manipulation mengubah penamaan folder menjadi format yang dapat diterima oleh HDFS.

![picture](/img/to_hdfs_name.JPG)


### Konfigurasi koneksi spark

![picture](/img/spark_conf.JPG)

Node akan menghasilkan suatu koneksi sebagai berikut:

![picture](/img/hive_conn.JPG)

### Load Tabel ke hive

![picture](/img/load_to_hive.JPG)

CSV reader akan membaca isi csv, kemudian table creator akan membuat table sesuai koneksi spark, kemudian DB loader akan membuat table ke DB di temp folder yang sudah didefinisikan sebelumnya

![picture](img/loader_conf.JPG)

Hasilnya adalah sebagai berikut:

![picture](img/ssp_knime_res.JPG)

Di DBeaver:

![picture](img/139_ssh_res.JPG)
![picture](img/139_ssp_res.JPG)
![picture](img/139_ssh_count.JPG)
![picture](img/139_ssp_count.JPG)

## Hive Modelling

Ubah node SQLite Connector pada workflow yang disediakan menjadi node Create Local Big Data Enviroment. Pastikan sudah melakukan setup yang sudah digambar sebelumnya

![picture](/img/hive_modelling.JPG)

Hasil:

![picture](/img/hive_modelling_res.JPG)


## Hive Write

![picture](/img/hive_write.JPG)

Siapkan terlebih dahulu directory HDFS denagn node Create Temp Dir seperti yang sudah dijelaskan kemudian buat tabel dengan node Tabel Creator dan commit tabel ke DB dengan node DB Loader.

![picture](/img/hive_write_conf.JPG)


Hasil:

![picture](/img/hive_write_res.JPG)