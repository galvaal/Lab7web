# Lab7web
# NAMA : Galva al Godzali
# Kelas : TI.22.A.3
NIM : 312210356

### Persiapan
#### Untuk memulai membuat kode php, perlu disiapkan web server dan interpreter PHP terlebih dahulu. Web servar yang kita gunakan adalah Apache 2 dan interpreter PHP 7. Untuk memudahkan proses praktikum, kita gunakan aplikasi bundle web server yaitu XAMPP.
Install XAMPP
#### Unduh XAMPP dari https://www.apachefriends.org/download.html dan pilih versi portable untuk memudahkan proses installasi. Kemudian extract file tersebut, seusikan direktorinya (misal: c:\xampp).


#### Konfigurasi Web Server
• Konfigurasi Apache
#### Untuk konfigurasi HTTP server, seperti port yang digunakan akses HTTP, modul yang diaktifkan, lokasi document root, dll.
#### Lokasi file: \xampp\apache\conf\httpd.conf
• Konfigrasi PHP
#### Untuk konfigurasi perilaku engine PHP yang berefek pada keamanan dan performa. Seperti batas maksimal waktu eksekusi script, batas file yang dapat diupload, error reporting, dll.
#### Lokasi file: \xampp\php\php.ini
• Konfigrasi MySql
#### Konfigurasi server MySQL, seperti administrator user, port, timezone, dll.
#### Lokasi file: \xampp\mysql\bin\my.ini
#### Menjalankan Web Server
##### ntuk menjalankan web server dari menu XAMPP Control.

##### Tampil halaman utama XAMPP jika server sudah berkerja dengan baik.
• Dokumen Website
##### Semua file website tempatkan di direktori: \xampp\htdocs\
• Database MySQL
##### Direktori: \xampp\mysql\
##### Manajemen database: http://localhost/phpmyadmin
##### Memulai PHP

# Kemudian untuk mengakses direktory tersebut pada web server dengan mengakses URL: http://localhost/lab7_php_dasar/
![AB1](https://github.com/galvaal/Lab7web/assets/115516730/23506fb0-0ee1-4100-8944-8de378ea18ec)

## Pertanyaan dan Tugas
##### Buatlah program PHP sederhana dengan menggunakan form input yang menampilkan nama, tanggal lahir dan pekerjaan. Kemudian tampilkan outputnya dengan menghitung umur berdasarkan inputan tanggal lahir. Dan pilihan pekerjaan dengan gaji yang berbeda-beda sesuai pilihan pekerjaan.
##### Input
```python
<!DOCTYPE html>
<html lang="en">

    <head>
        <title>Form Input</title>
        <meta charset="utf-8">

        <!-- CSS -->
        <style>
        body {
            width: 100%;
            height: 100vh;
            margin: 0;
            font-family: tahoma;
            font-size: 16px;
        }
        h1, p {
            margin: 1em auto;
            text-align: center;
        }
        form {
            width: 60vw;
            max-width: 500px;
            min-width: 300px;
            margin: 0 auto;
            padding-bottom: 2em;
            }
        label {
            display: block;
            margin: 0.5rem 0;
        }
        button[type="submit"] {
            display: block;
            width: 60%;
            margin: 1em auto;
            height: 2em;
            font-size: 1.1rem;
            background-color: #e0daca;
            border-color: white;
            min-width: 300px;
        }
        </style>
    </head>

    <body>
        <h1 id="title">Survey Formulir Pekerjaan dan Gaji</h1>
        <p id="description"><i>Melansir dari situs <a href="https://id.indeed.com/career/php-developer/salaries"> indeed.com</a></i></p>

        <form id="survey-form" action="" method="POST">
            <fieldset>
                <label>Nama: 
                    <input type="text" name="nama" required/>
                </label>
                <label>Tanggal lahir: 
                    <input type="date" name="date">
                </label>
                <label>Pekerjaan: 
                    <label>
                    <input type="radio" name="job" value="0"/>Database Administrator
                    </label>
                    <label>
                    <input type="radio" name="job" value="1"/>Software Developer
                    </label>
                    <label>
                    <input type="radio" name="job" value="2"/>Web Developer
                    </label>
                </label>
                <button type="submit" name="submit">Kirim</button>
            </fieldset>
            <fieldset>
                <?php
                if( isset($_POST['submit']))
                {
                    $nama = $_POST['nama'];
                    $date = $_POST['date'];
                    $job = $_POST['job'];


                    $date_user = new DateTime($date);
                    $today =  new DateTime('today');
                    $usia = $today->diff($date_user)->y;

                    $job_array = ["Database Administrator","Software Developer","Web Developer"];
                    $salary_array = ["Rp. 5.300.000","Rp. 5.400.000","Rp. 4.800.000"];


                    echo "Halo, ".$nama."<br>Kamu lahir pada tanggal ".$date.", Usia mu ".$usia." tahun";
                    echo "<br>Pekerjaan yang kamu pilih adalah ".$job_array[(int)$job].", dengan penghasilan kurang lebih ".$salary_array[(int)$job];
                }
                ?>
            </fieldset>
        </form>
    </body>
</html>

