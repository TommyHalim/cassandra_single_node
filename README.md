# cassandra_single_node

## Instalasi

Konfigurasi vagrant

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/vagrantfile.JPG">

Karena vagrantfile tidak menggunakan file provision, maka saat setelah vagrant up dan ssh ke db1, lakukan perintah berikut agar ubuntu diperbarui
```
sudo apt-get update

sudo apt-get install software-properties-common
```

### 1. Membuat user serta memberi privilege

Untuk membuat user, lakukan perintah
```
adduser admin
 
gpasswd -a admin sudo
```
<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/add%20user.JPG"><br>

perintah adduser admin diatas, merupakan perintah pembuatan user bernama admin setelah itu, perintah gpasswd -a admin sudo merupakan pemberian kewenangan penuh untuk user admin

### 2. Instalasi Java Oracle JDK

sebelum instalasi oracle, buat terlebih dahulu repository untuk oracle java dengan menjalankan perintah
```
sudo add-apt-repository ppa:webupd8team/java

sudo apt-get update
```

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/install%20oracle.JPG">

Setelah kita membuat repository oracle, maka lakukan instalasi oracle dengan perintah sebagai berikut
```
sudo apt-get install oracle-java8-set-default
```
<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/install%20oracle%202.JPG">

Ikuti petunjuk instalasi, setelah itu kita dapat mengecek oracle yang telah terinstal dengan menjalankan perintah
```
java -version
```

### 3. Instalasi Cassandra

3.1 fetch package cassandra
dapat dilakukan dengan perintah
```
echo "deb http://www.apache.org/dist/cassandra/debian 39x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list

echo "deb-src http://www.apache.org/dist/cassandra/debian 39x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list
```

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/package.JPG">

3.2 Insert key cassandra
terdapat 3 key yang perlu diinputkan
```
#Key pertama
gpg --keyserver pgp.mit.edu --recv-keys F758CE318D77295D
gpg --export --armor F758CE318D77295D | sudo apt-key add -

#Key kedua
gpg --keyserver pgp.mit.edu --recv-keys 2B5C1B00
gpg --export --armor 2B5C1B00 | sudo apt-key add -

#Key ketiga
gpg --keyserver pgp.mit.edu --recv-keys 0353B12C
gpg --export --armor 0353B12C | sudo apt-key add -

sudo apt-get update
```
Input key 1

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/insert%20key%201.JPG">

Input key 2

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/Insert%20key%202.JPG">

Input key 3

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/Insert%20key%203.JPG">

3.3 Install Cassandra
Dilakukan dengan perintah
```
sudo apt-get install cassandra
```

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/install%20cassandra.JPG">

Setelah instalasi selesai, cassandra yang telah diinstal dapat dicek dengan
```
sudo service cassandra status
```
Untuk mengecek node cassandra, dapat dilakukan dengan perintah
```
sudo nodetool status
```

<img src="https://github.com/TommyHalim/cassandra_single_node/blob/master/SS/cek%20status%20cassandra.JPG">
