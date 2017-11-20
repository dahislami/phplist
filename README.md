<h1 align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/7/79/PhpList_Logo.png"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Kebutuhan Instalasi](#kebutuhan-instalasi) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Maintanance](#maintanance) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) |[Slide Presentasi](#slide-presentasi) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:



# Sekilas Tentang
[`^ kembali ke atas ^`](#)

**PHPList** adalah sebuah CMS (*content management system*) aplikasi web *e-commerce* yang gratis dan *Open Source*. 
**PHPList** adalah software yang digunakan untuk mengelola miling list. **PHPList** dirancang untuk menyebarkan informasi seperti buletin, berita, iklan ke daftar pelanggan. Software ini ditulis dalam bahasa PHP dan database MySQL untuk menyimpan informasinya. 

# Kebutuhan Instalasi
[`^ kembali ke atas ^`](#)

#### Kebutuhan **PHPList** :
Untuk menginstall **PHPList** kita membutuhkan:
- GNU/Linux OS
- Apache web server
- PHP version 4.3 or atau versi yang lebih tinggi
- PHP Imap Module
- MySQL server version 4.0 atau versi yang lebih tinggi

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
[Config](https://www.phplist.org/manual/static/phpList_config_done.png)
2. Melakukan setup pada bagian **Configure Attributes**
 
    - Membuat atribut yang dapat ditampilkan ketika user hendak mendaftar ke sebuah mailing list
    - Mengisikan nama, misalnya pekerjaan
    - Menentukan tipe untuk atribut tersebut pada kotak type, jika ada nilai default untuk atribut tersebut isikan di kotak Default Value
    - Tentukan juga apakah variabel tersebut harus diisi oleh pendaftar atau tidak, pada kotak **Is this attribute required?**
    - Klik merge
 
3. Membuat **List** . List adalah objek yang menyimpan daftar user berta email yang terdaftar
 
    - Isi nama pada kotak List name
    - Mengklik kotak **Check this box to make this list active**. List yang dibuat akan langsung aktif dan bisa menerima user yang ingin berlangganan/subscibe
    - Mengisikan owner yang berhak mengatur list tersebut
    - Mengisikan deskripsi tentang list pada kotak List Description
    - Simpan perubahan Save
 
 4. Membuat **Subcriber Pages** 

    - Pengisian Thank You page, text for button dan opsi Email Configuration
    - Pengisian judul dan isi email subscribe dan email konfirmasi
    - Mengisi isi pesan yang ada di kotak Message bagian Message they receive when they subscibe
    - Mengisi pesan yang akan dikirim setelah terkonfirmasi di kotak Message pada bagian bawah tulisan Message the receive when they confirm their subscription
    - Simpan perubahan Save Change
 

# Maintanance
[`^ kembali ke atas ^`](#)

#### Scheduling

**Scheduling** dilakukan pada halaman administrator. Ketika administrator mengatur scheduling pengiriman newsletter, maka **PHPList** otomatis akan mengirimkan newsletter sesuai dengan waktu yang telah diset oleh administrator.
-  Pada tab scheduling, administrator menentukan menahan tulisan untuk dipublish hingga waktu tertentu yang otomatis akan diantrikan untuk dikirim jika masa penahanannya sudah usai.

### Pemberhentian berlangganan
**Unsubscribe** merupakan proses ketika pelanggan newsletter berhenti berlangganan artinya pelanggan tersebut menghentikan pengiriman newsletter ke email yang telah didaftarkan dan diverifikasi. Hal tersebut mungkin saja dilakukan oleh pelanggan dengan berbagai alasan. Adapun langkah untuk berhenti berlangganan sebagai berikut :
- Masuk ke halaman utama phplist kemudian pilih **unsubscribe** dan mengisikan alasan dari pemberhentian dalam berlangganan newsletter
- Pemberitahuan unsubscribe sukses dengan melakukan pengecekan pada email dan melakukan konfirmasi unsubscibe newsletter pada email pemberitahuan untuk berhenti berlangganan 


# Cara Pemakaian
[`^ kembali ke atas ^`](#)

#### Sisi Pelanggan
Cara menggunakan PHPList dari sisi pelanggan adalah dengan berlangganan newsletter yang disediakan oleh administrator. Pelanggan dapat memilih berita dan dapat mendaftarkan email untuk berlangganan newsletter. Selanjutnya, pengguna dapat menikmati layanan dengan menerima newsletter sesuai dengan kebutuhan dan keinginan dari pengguna tersebut.

1. Mendaftarkan diri sebagai pelanggan dengan cara membuka halaman utama **PHPList** kemudian **Subscribe to our newsletter**
2. Mengisikan data-data yang dibutuhkan seperti email
3. Subscribe
4. Jika berhasil, maka pemberitahuan akan masuk ke email yang telah didaftarkan
5. Konfirmasi untuk memverifikasi melalui email dengan mengikuti url pada email yang telah didaftarkan dan selesai
6. Secara periodik newsletter akan dikirimkan ke email yang telah didaftarkan dan terverifikasi

#### Sisi Administrator
Administrator dapat menggunakan PHPList sebagai sarana untuk mengirim bulletin dan newsletter secara periodik kepada pelanggan yang telah berlangganan ke email yang telah diverifikasi oleh administrator. Administrator juga dapat memilih newsletter dan bulletin sesuai dengan kebutuhan masing-masing pelanggan. Administrator juga dapat tidak mengirimkan bulletin dan newsletter ke email yang belum terverifikasi. Administrator juga dapat mengatur isi konten dari newsletter dan bulletin. Administrator juga dapat mengatur schedule pengiriman newsletter dan bulletin pada waktu tertentu.

1. Masuk ke halaman utama **PHPList** kemudian login sebagai administrator
2. Pada menu **List and user function** pilih users kemudian melakukan konfigurasi pelanggan yang telah terdaftar yang akan berlangganan newsletter
3. Melakukan **verifikasi** email pelanggan yang telah melakukan subscribe
4. Sebelum melakukan pengiriman newsletter, administrator harus mengatur **konten** dari newsletter yang akan dikirim kepada pelanggan terlebih dahulu. Pengaturan konten meliputi, memberikan judul newsletter, penambahan gambar, penambahan isi dari newsletter, mengatur allign, sampai menambahkan footer pada newsletter.
5. Melakukan penyimpanan konfigurasi
6. Kemudian berpindah ke tab format pengiriman newsletter ada 2 format yang ditawarkan yakni dapat berupa html atau text format
7. Berpindah ke tab **attach** administrator dapat menentukan apakah hendak menambahkan attachment file atau tidak pada newsletter yang akan dikirim
8. Berpindah ke tab **scheduling** administrator dapat mengatur jadwal dan waktu pengiriman newsletter tanpa mengharuskan adanya pengawasan dari administrator
9. Untuk pengiriman pesan terdapat pada tab **lists** , kemudian administrator memilih list yang ingin dikirimi newsletter tersebut
10. **Send message to selected mailinglist** untuk mengirimkan newsletter yang telah dibuat ke semua alamat email yang terdaftar pada list
11. Selanjutnya klik **process the message queue** untuk menunggu giliran pengiriman ke masing-masing email tujuan
12. Selesai


# Pembahasan
[`^ kembali ke atas ^`](#)

**PHPList** merupakan aplikasi bulletin untuk menyebarkan newsletter berbasis web. **PHPList** memungkinkan pengaturan template email yang akan digunakan untuk tampilan yang seragam dan konsisten. Berikut ini merupakan beberapa **fitur pada PHPList** :
1. Adanya berbagai macam **variasi instalasi** via Fantastico, FTP, atau SSH
2. **User management** untuk mengatur dan menjaga data pelanggan
3. **CSV Import and Export** untuk mengimpor daftar user yang telah ada
4. **Attachment** dapat diupload dan dimasukkan di pesan untuk didownload
5. **Penjadwalan pengiriman** untuk menentukan kapan pesan dikirim

#### Kelebihan penggunaan **PHPList**
1. Interface aplikasi berbasis web sehingga mudah untuk menulis, mengatur, dan mengirimkan pesan melalui internet
2. Dapat melacak respon dan perilaku pelanggan secara real-time.
3. PHPList dapat terus mengirimkan pesan dari web server yang digunakan, meskipun kita sudah mematikan komputer dan tidak mengakses web server tersebut.
4. Dapat mengakomodasi jumlah pelanggan dengan susbscriber yang banyak, namun tetap elegan dipakai untuk sedikit orang.
5. Tidak ada pesan yang terduplikasi dan terlupakan.

#### Kekurangan penggunaan **PHPList**
1. Membutuhkan jaringan internet yang stabil
2. Jika perlu mengirimkan newsletter kepada subscriber yang sangat banyak, sistem yang berjalan tidak bisa melakukan task lain.

#### Perbandingan **PHPList** dengan CMS lainnya
1. **PHPList** vs **Mailman** 

    - PHPList memiliki user interface dan admin interface yang lebih baik jika dibandingkan dengan mailman. Mailman berbasis text sehingga memiliki tampilan yang simpel dan polos
    - PHPList merupakan open source system
 
2. **PHPList** vs **Web Mailing List**
 
    - PHPList memiliki keunggulan dapat mengirimkan newsletter dalam jumlah banyak ke banyak email, sedangkan pada web mailing list hanya dapat mengatur email dalam jumlah yang sedikit 
  

# Slide Presentasi
[`^ kembali ke atas ^`](#)

Berikut ini merupakan lampiran dari slide presentasi **PHPList**

 ![slide](https://github.com/dahislami/phplist/blob/master/Presentasi%20PHPList2.pptx)

# Referensi
[`^ kembali ke atas ^`](#)

1. [About PHPList](https://www.phplist.com/) - PHPList
2. [PHPList User Manual](https://www.phplist.org/manual/phpList_manual_pdf_20150522.pdf) - User Manual
