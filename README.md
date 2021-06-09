# Praktikum 9 - PHP Modular

```
Gede Krishna
311910429
TI 19 A2
```

## LANGKAH 1
### Jalankan XAMPP dan akses http://localhost/phpmyadmin/ untuk membuat database.
![LANGKAH 1](https://user-images.githubusercontent.com/22215113/120314094-10db6a80-c305-11eb-8d26-02289dd27c1c.png)

## LANGKAH 2
### Buat file `lab9_php_modular` pada root directory web server `(d:\xampp\htdocs)`
![LANGKAH 2 BUAT FOLDER](https://user-images.githubusercontent.com/22215113/120469229-49924700-c3cc-11eb-8a67-b4ebda3c6519.png)

## LANGKAH 3
### Buat file baru dengan nama `header.php` pada folder `(d:\xampp\htdocs\lab9_php_modular)`
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/stylesheet" media="screen" />
</head>
<body>
    <div class="container">
        <header>
            <h1>Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
        <a href="home.php">Home</a>
        <a href="about.php">Tentang</a>
        <a href="kontak.php">Kontak</a>
        </nav>
```

## LANGKAH 4
### Buat file baru dengan nama `footer.php` pada folder `(d:\xampp\htdocs\lab9_php_modular)`
```
        <footer>
            <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
```
![LANGKAH 4](https://user-images.githubusercontent.com/22215113/120469680-e05f0380-c3cc-11eb-95d5-3fb2c1114916.png)

## LANGKAH 5
### Buat file baru dengan nama `home.php` pada folder `(d:\xampp\htdocs\lab9_php_modular)`
```
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman Home</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
```
![LANGKAH 5](https://user-images.githubusercontent.com/22215113/120469847-1603ec80-c3cd-11eb-8bd0-efd311822f12.png)

## LANGKAH 6
### Buat file baru dengan nama `about.php` pada folder `(d:\xampp\htdocs\lab9_php_modular)`
```
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman About</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
```
![LANGKAH 6](https://user-images.githubusercontent.com/22215113/120469974-359b1500-c3cd-11eb-9422-ecaeb2e45232.png)


## TUGAS
### Implementasikan konsep modularisasi pada kode program `praktikum 8` tentang database, sehingga setiap halamannya memiliki template tampilan yang sama.

## LANGKAH 1
### Buat file `lab9_tugas` pada root directory web server `(d:\xampp\htdocs)`
![TUGAS 1](https://user-images.githubusercontent.com/22215113/120470563-e0133800-c3cd-11eb-9fc9-682524df9499.png)

## LANGKAH 2
### Buat file baru dengan nama `koneksi.php` pada folder `(d:\xampp\htdocs\lab9_tugas)`
```
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db = "latihan1";
$conn = mysqli_connect($host, $user, $pass, $db);

if ($conn == false)
{
    echo "Koneksi ke server gagal.";
    die();
} #else echo "Koneksi berhasil";
?>
```
![TUGAS 2](https://user-images.githubusercontent.com/22215113/120470818-32ecef80-c3ce-11eb-970d-08b5bb5d5ec6.png)

## LANGKAH 3
### Buat file baru dengan nama `header.php` pada folder `(d:\xampp\htdocs\lab9_tugas)`
```
<?php
include("koneksi.php");

// query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/css" />
</head>
<body>
    <div id="container">
        <header>
            <h1>Database</h1>
        </header>
        <nav>
            <a href="home.php">Home</a>
            <a href="tambah.php">Tambah Barang</a>
        </nav>
```
![TUGAS 3](https://user-images.githubusercontent.com/22215113/120471021-6760ab80-c3ce-11eb-9f50-9a56fe90ac25.png)

## LANGKAH 4
### Buat file baru dengan nama `footer.php` pada folder `(d:\xampp\htdocs\lab9_tugas)`
```
        <footer>
            <p>&copy; 2021, Veno Setyoaji Wiratama, 3111910363, TI.19.A.2</p>
        </footer>
    </div>
</body>
</html>
```
![TUGAS 4](https://user-images.githubusercontent.com/22215113/120471212-a2fb7580-c3ce-11eb-8a61-29298d3edd54.png)

## LANGKAH 5
### Buat file baru dengan nama `home.php` pada folder `(d:\xampp\htdocs\lab9_tugas)`
```
<?php require('header.php'); ?>

<div class="content">
    <h1>Data Barang</h1>
    <div class="main">
        <table>
        <tr>
            <th>Gambar</th>
            <th>Nama Barang</th>
            <th>Katagori</th>
            <th>Harga Jual</th>
            <th>Harga Beli</th>
            <th>Stok</th>
            <th>Aksi</th>
        </tr>
        <?php if($result): ?>
        <?php while($row = mysqli_fetch_array($result)): ?>
        <tr>
            <td><img src="gambar/<?= $row['gambar'];?>" alt="<?=$row['nama'];?>"></td>
            <td><?= $row['nama'];?></td>
            <td><?= $row['kategori'];?></td>
            <td><?= $row['harga_jual'];?></td>
            <td><?= $row['harga_beli'];?></td>
            <td><?= $row['stok'];?></td>
            <td>
                <a href="ubah.php?id=<?= $row['id_barang'];?>">Ubah</a>
                <a href="hapus.php?id=<?= $row['id_barang'];?>">Hapus</a> 
            </td>
        </tr>
        <?php endwhile; else: ?>
        <tr>
            <td colspan="7">Belum ada data</td>
        </tr>
        <?php endif; ?>
        </table>
    </div>
</div>

<?php require('footer.php'); ?>
```
![TUGAS 5 (1)](https://user-images.githubusercontent.com/22215113/120471406-e0f89980-c3ce-11eb-89ac-4d0a870a328e.png)
![TUGAS 5 (2)](https://user-images.githubusercontent.com/22215113/120471414-e2c25d00-c3ce-11eb-918e-bb78291a77a6.png)

## LANGKAH 6
### Buat file baru dengan nama `tambah.php` pada folder `(d:\xampp\htdocs\lab9_tugas)`
```
<?php
error_reporting(E_ALL);
include_once 'koneksi.php';

if (isset($_POST['submit']))
{
    $nama = $_POST['nama'];
    $kategori = $_POST['kategori'];
    $harga_jual = $_POST['harga_jual'];
    $harga_beli = $_POST['harga_beli'];
    $stok = $_POST['stok'];
    $file_gambar = $_FILES['file_gambar'];
    $gambar = null;

    if ($file_gambar['error'] == 0)
    {
        $filename = str_replace(' ', '_',$file_gambar['name']);
        $destination = dirname(__FILE__) .'/gambar/' . $filename;
        if(move_uploaded_file($file_gambar['tmp_name'], $destination))
        {
            $gambar = 'gambar/' . $filename;;
        }
    }
    
    $sql = 'INSERT INTO data_barang (nama, kategori, harga_jual, harga_beli, stok, gambar) ';
    $sql .= "VALUE ('{$nama}', '{$kategori}','{$harga_jual}','{$harga_beli}', '{$stok}', '{$gambar}')";
    $result = mysqli_query($conn, $sql);
    header('location: home.php');
}
?>

<?php require('header.php'); ?>

<div class="content">
    <h1>Tambah Barang</h1>
    <div class="main">
        <form method="post" action="tambah.php" enctype="multipart/form-data">
            <div class="input">
                <label>Nama Barang</label>
                <input type="text" name="nama" style="margin-left: 20px;" />
            </div>
            <div class="input">
                <label>Kategori</label>
                <select name="kategori" style="margin-left: 58px;" >
                    <option value="Komputer">Komputer</option>
                    <option value="Elektronik">Elektronik</option>
                    <option value="Hand Phone">Hand Phone</option>
                </select>
            </div>
            <div class="input">
                <label>Harga Jual</label>
                <input type="text" name="harga_jual" style="margin-left: 40px;" />
            </div>
            <div class="input">
                <label>Harga Beli</label>
                <input type="text" name="harga_beli" style="margin-left: 43px;" />
            </div>
            <div class="input">
                <label>Stok</label>
                <input type="text" name="stok" style="margin-left: 85px;" />
            </div>
            <div class="input">
                <label>File Gambar</label>
                <input type="file" name="file_gambar" />
            </div>
            <div class="submit">
                <input type="submit" name="submit" value="Simpan" />
            </div>
        </form>
    </div>
</div>

<?php require('footer.php'); ?>
```
![TUGAS 6 (1)](https://user-images.githubusercontent.com/22215113/120471827-6714e000-c3cf-11eb-919e-3db9e8b9ce68.png)
![TUGAS 6 (2)](https://user-images.githubusercontent.com/22215113/120471837-68dea380-c3cf-11eb-86b8-3cc8f97ada4a.png)
![TUGAS 6 (3)](https://user-images.githubusercontent.com/22215113/120471850-6aa86700-c3cf-11eb-8fb6-0a3580d21d47.png)

## LANGKAH 7
### Buat file baru dengan nama `ubah.php` pada folder `(d:\xampp\htdocs\lab9_tugas)`
```
<?php
error_reporting(E_ALL);
include_once 'koneksi.php';

if (isset($_POST['submit']))
{
    $id = $_POST['id'];
    $nama = $_POST['nama'];
    $kategori = $_POST['kategori'];
    $harga_jual = $_POST['harga_jual'];
    $harga_beli = $_POST['harga_beli'];
    $stok = $_POST['stok'];
    $file_gambar = $_FILES['file_gambar'];
    $gambar = null;

    if ($file_gambar['error'] == 0)
    {
        $filename = str_replace(' ', '_', $file_gambar['name']);
        $destination = dirname(__FILE__) . '/gambar/' . $filename;
        if (move_uploaded_file($file_gambar['tmp_name'], $destination))
        {
            $gambar = 'gambar/' . $filename;;
        }
    }

    $sql = 'UPDATE data_barang SET ';
    $sql .= "nama = '{$nama}', kategori = '{$kategori}', ";
    $sql .= "harga_jual = '{$harga_jual}', harga_beli = '{$harga_beli}', stok = '{$stok}' ";
    if (!empty($gambar))
        $sql .= ", gambar = '{$gambar}' ";
    $sql .= "WHERE id_barang = '{$id}'";
    $result = mysqli_query($conn, $sql);

    header('location: home.php');
    }

    $id = $_GET['id'];
    $sql = "SELECT * FROM data_barang WHERE id_barang = '{$id}'";
    $result = mysqli_query($conn, $sql);
    if (!$result) die('Error: Data tidak tersedia');
    $data = mysqli_fetch_array($result);

    function is_select($var, $val) {
        if ($var == $val) return 'selected="selected"';
        return false;
}
?>

<?php require('header.php'); ?>

<div class="content">
    <h1>Ubah Barang</h1>
    <div class="main">
        <form method="post" action="ubah.php" enctype="multipart/form-data">
            <div class="input">
                <label>Nama Barang</label>
                <input type="text" name="nama" value="<?php echo $data['nama'];?>" style="margin-left: 20px;"/>
            </div>
            <div class="input">
                <label>Kategori</label>
                <select name="kategori" style="margin-left: 58px;">
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Komputer">Komputer</option>
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Elektronik">Elektronik</option>
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Hand Phone">Hand Phone</option>
                </select>
            </div>
            <div class="input">
                <label>Harga Jual</label>
                <input type="text" name="harga_jual" value="<?php echo $data['harga_jual'];?>" style="margin-left: 40px;"/>
            </div>
            <div class="input">
                <label>Harga Beli</label>
                <input type="text" name="harga_beli" value="<?php echo $data['harga_beli'];?>" style="margin-left: 43px;"/>
            </div>
            <div class="input">
                <label>Stok</label>
                <input type="text" name="stok" value="<?php echo $data['stok'];?>" style="margin-left: 85px;"/>
            </div>
            <div class="input">
                <label>File Gambar</label>
                <input type="file" name="file_gambar" />
            </div>
            <div class="submit">
                <input type="hidden" name="id" value="<?php echo $data['id_barang'];?>" />
                    <input type="submit" name="submit" value="Simpan" />
            </div>
        </form>
    </div>
</div>

<?php require('footer.php'); ?>
```
![TUGAS 7 (1)](https://user-images.githubusercontent.com/22215113/120472102-b2c78980-c3cf-11eb-9b2f-2b0b0bb4630d.png)
![TUGAS 7 (2)](https://user-images.githubusercontent.com/22215113/120472112-b4914d00-c3cf-11eb-9419-753acf5c8851.png)
![TUGAS 7 (3)](https://user-images.githubusercontent.com/22215113/120472117-b5c27a00-c3cf-11eb-91c8-ca9af7bac797.png)

## LANGKAH 8
### Buat file baru dengan nama `hapus.php` pada folder `(d:\xampp\htdocs\lab9_tugas)`
```
<?php
include_once 'koneksi.php';
$id = $_GET['id'];
$sql = "DELETE FROM data_barang WHERE id_barang = '{$id}'";
$result = mysqli_query($conn, $sql);
header('location: home.php');
?>
```
![TUGAS 8 (1)](https://user-images.githubusercontent.com/22215113/120472280-e4d8eb80-c3cf-11eb-91e8-d5bb29cd3163.png)

## LANGKAH 9
### Buat file baru dengan nama `style.css` pada folder `(d:\xampp\htdocs\lab9_tugas)` untuk mempercantikan tampilan
```
/* import google font */
@import
url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,600;0,700;0,800;1,300;1,400;1,600;1,700;1,800&display=swap');
@import
url('https://fonts.googleapis.com/css2?family=Open+Sans+Condensed:ital,wght@0,300;0,700;1,300&display=swap');

/* Reset CSS */
* {
    margin: 0;
    padding: 0;
}
body {
    line-height:1;
    font-size:100%;
    font-family:'Open Sans', sans-serif;
    color:#5a5a5a;
}
#container {
    width: 980px;
    margin: 0 auto;
    box-shadow: 0 0 1em #cccccc;
}

/* header */
header {
    padding: 20px;
}
header h1 {
    margin: 20px 10px;
    color: #b5b5b5;
}

/* navigasi */
nav {
    display: block;
    background-color: #1f5faa;
}
nav a {
    padding: 15px 30px;
    display: inline-block;
    color: #ffffff;
    font-size: 14px;
    text-decoration: none;
    font-weight: bold;
}
nav a.active,
nav a:hover {
    background-color: #2b83ea;
}

/* Content Panel */
.content {
    background-color: #e4e4e5;
    padding: 50px 20px;
    margin-bottom: 20px;
}
.content h1 {
    margin-bottom: 20px;
    font-size: 35px;
}
.content p {
    margin-bottom: 20px;
    font-size: 18px;
    line-height: 25px;
}

/* footer */
footer {
    clear:both;
    background-color:#1d1d1d;
    padding:20px;
    color:#eee;
}

/* tabel */
body{
    font-family: sans-serif;
}
table{
    border-collapse: collapse;
}
th, td{
    border: 1px solid black;
    font-size: 16px;
    padding: 7px 9px;
}
table th {
    background:#1f5faa;
    color:#DCDCDC;
    font-weight:bold;
    font-size:14px;
}
table tr:nth-child(even) {
    background:#F0F8FF;
}

/* Tambah Barang */
.input{
    padding: 5px;
}
```
