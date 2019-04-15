# cassandra_single_node

## Instalasi

Konfigurasi vagrant


### 1. Membuat user serta memberi privilege

Untuk membuat user, lakukan perintah
```
adduser admin
 
gpasswd -a admin sudo
```
![](/tugas_4_cassandara-single-and-multiple-note/tugas_single-note/screenshoot/cassandra_add_user.PNG)
perintah adduser admin diatas, merupakan perintah pembuatan user bernama admin setelah itu, perintah gpasswd -a admin sudo merupakan pemberian kewenangan penuh untuk user admin

### 2. Instalasi Java Oracle JDK

![]()
sebelum instalasi oracle, buat terlebih dahulu repository untuk oracle java dengan menjalankan perintah
```
sudo add-apt-repository ppa:webupd8team/java

sudo apt-get update
```
![]()
Setelah kita membuat repository oracle, maka lakukan instalasi oracle dengan perintah sebagai berikut
```
sudo apt-get install oracle-java8-set-default
```
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
![]()

Input key 2
![]()

Input key 3
![]()

3.3 Install Cassandra
Dilakukan dengan perintah
```
sudo apt-get install cassandra
```
Setelah instalasi selesai, cassandra yang telah diinstal dapat dicek dengan
```
sudo service cassandra status
```
Untuk mengecek node cassandra, dapat dilakukan dengan perintah
```
sudo nodetool status
```
