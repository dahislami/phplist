<h1 align="center"><img src="https://commons.wikimedia.org/wiki/File:PhpList_Logo.png"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:



# Sekilas Tentang
[`^ kembali ke atas ^`](#)

**PHPList** adalah sebuah CMS (*content management system*) aplikasi web *e-commerce* yang gratis dan *Open Source*. Aplikasi ini mulai beroperasi pada tahun 2005 sebagai proyek dari seorang murid *EPITECH IT School* di Paris, Perancis, yang awalnya bernama `phpOpenStore`. Hingga saat ini, **PHPList** telah berkembang pesat dan berkomitmen untuk memberikan pengalaman berbelanja terbaik untuk para pedagang dan pelanggannya. 



# Instalasi
[`^ kembali ke atas ^`](#)

#### Kebutuhan **PHPList** :
Untuk menginstall **PHPList** kita membutuhkan:
·         GNU/Linux OS
·         Apache web server
·         PHP version 4.3 or atau versi yang lebih tinggi
·         PHP Imap Module
·         MySQL server version 4.0 atau versi yang lebih tinggi

#### Proses Instalasi :
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


# Maintenance
[`^ kembali ke atas ^`](#)

# Otomatisasi
[`^ kembali ke atas ^`](#)


# Cara Pemakaian
[`^ kembali ke atas ^`](#)



# Pembahasan
[`^ kembali ke atas ^`](#)

# Referensi
[`^ kembali ke atas ^`](#)
