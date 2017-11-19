<h1 align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/7/79/PhpList_Logo.png"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Kebutuhan Instalasi](#kebutuhan-instalasi) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:



# Sekilas Tentang
[`^ kembali ke atas ^`](#)

**PHPList** adalah sebuah CMS (*content management system*) aplikasi web *e-commerce* yang gratis dan *Open Source*. 
**PHPList** adalah software yang digunakan untuk mengelola miling list. **PHPList** dirancang untuk menyebarkan informasi seperti buletin, berita, iklan ke daftar pelanggan. Software ini ditulis dalam bahasa PHP dan database MySQL untuk menyimpan informasinya. 
 



# Kebutuhan Instalasi
[`^ kembali ke atas ^`](#)

#### Kebutuhan **PHPList** :
Untuk menginstall **PHPList** kita membutuhkan:
-         GNU/Linux OS
-         Apache web server
-         PHP version 4.3 or atau versi yang lebih tinggi
-         PHP Imap Module
-         MySQL server version 4.0 atau versi yang lebih tinggi

# Instalasi :
[`^ kembali ke atas ^`](#)

1. Login kedalam server menggunakan SSH. Untuk pengguna windows bisa menggunakan aplikasi PuTTY.
    ```
    $ ssh student@172.18.88.88 -p 22
    ```

2. Pastikan seluruh paket sistem kita up-to-date, dan install seluruh kebutuhan sisrem seperti `Apache`, `PHP`, dan `MySQL`.
    ```
    $ sudo apt install apache2
    $ sudo apt install mysql-server
    $ sudo apt install php
    $ sudo apt install libapache2-mod-php 
    $ sudo apt install php-mysql php-mysqli
    $ sudo apt install php-imap php-date php-mbstring php-curl php-xml  
    php7.0-common php-json php-gettext php7.0-xml php-gd

    ```

3. Restart kembali Apache web server. 
    ```
    $ sudo service apache2 restart
    ```

4. Buat database dan user untuk **PHPList**.
    ```
    $ mysql -u root -p -v -e "
       	CREATE DATABASE phplistdb;
   	    CREATE USER phplistuser IDENTIFIED BY 'phplistpassword';
   	    GRANT ALL PRIVILEGES ON phplistdb.* TO phplistuser;"
    ```

5. Unduh **PHPList** ke dalam direktori kita.
    ```
    $ wget "https://sourceforge.net/projects/phplist/files/phplist/3.3.1/phplist-3.3.1.tgz/download" -O phplist.tgz
    ```

6. Ekstrak file yang sudah diunduh ke folder yang kita inginkan.
    ```
    $ sudo tar -xzf phplist.tgz
    $ sudo cp -r phplist*/public_html/lists /var/www/html/lists

    ```

7. Ubah kepemilikian otorisasi ke user www-data (webserver).
    ```
    $ sudo chown -R www-data:www-data /var/www/html/lists
    ```

8. Tambahkan konfigurasi PHPMAILER :
    ```
    define('PHPMAILER',1);
    define('PHPMAILERHOST', 'smtp.gmail.com:587');
    $phpmailer_smtpuser = 'email@gmail.com';
    $phpmailer_smtppassword = 'password gmail';
    define('PHPMAILER_SECURE','tls');

    ```

9. Konfigurasi mode TEST : 0 mail send aktif sedangkan 1 mail send tidak aktif
    ```
    define('TEST', 0);
    ```


# Konfigurasi
[`^ kembali ke atas ^`](#)
1. Melakukan setup pada bagian System Function halaman admin **PHPList**.
2. Melakukan setup pada bagian **Configure Attributes**
 ```
 Membuat atribut yang dapat ditampilkan ketika user hendak mendaftar ke sebuah mailing list
 Mengisikan nama, misalnya pekerjaan
 Menentukan tipe untuk atribut tersebut pada kotak type, jika ada nilai default untuk atribut tersebut isikan di kotak Default Value
 Tentukan juga apakah variabel tersebut harus diidi oleh pendaftar atau tidak, pada kotak **Is this attribute required?**
 Klik merge
 ```
2. Membuat **List** . List adalah objek yang menyimpan daftar user berta email yang terdaftar
 ```
 Isi nama pada kotak List name
 Mengklik kotak **Check this box to make this list active**. List yang dibuat akan langsung aktif dan bisa menerima user yang ingin berlangganan/subscibe
 Mengisikan owner yang berhak mengatur list tersebut
 Mengisikan deskripsi tentang list pada kotak List Descriiption
 Simpan perubahan **Save**
 ```
 3. Membuat **Subcriber Pages** 
 ```
 Pengisian Thank You page, text for button dan opsi Email Configuration
 Pengisian judul dan isi email subscribe dan email konfirmasi
 Mengisi isi pesan yang ada di kotak Message bagian Message they receive when they subscibe
 Mengisi pesan yang akan dikirim setelah terkonfirmasi di kotak Message pada bagian bawah tulisan Message the receive when they confirm their subscription
 Simpan perubahan **Save Change**
 ```

# Maintenance
[`^ kembali ke atas ^`](#)

# Otomatisasi
[`^ kembali ke atas ^`](#)


# Cara Pemakaian
[`^ kembali ke atas ^`](#)



# Pembahasan
[`^ kembali ke atas ^`](#)
#### Kelebihan penggunaan **PHPList**
1. Interface aplikasi berbasis web sehingga mudah untuk menulis, mengatur, dan mengirimkan pesan melalui internet
2. Dapat melacak respon dan perilaku pelanggan secara real-time.
3. PHPList dapat terus mwngirimkan pesan dari web server yang digunakan, meskipun kita sudah mematikan komputer dan tidak mengakses web server tersebut.
4. Dapat mengakomodasi jumlah pelanggan dengan susbscriber yang banyak, namun tetap elegan dipakai untuk sedikit orang.
5. Tidak ada pesan yang terduplikasi dan terlupakan.

#### Kekurangan penggunaan **PHPList**

# Referensi
[`^ kembali ke atas ^`](#)
