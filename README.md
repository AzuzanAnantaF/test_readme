###### Nama : Azuzan Ananta F
###### Kelas : XIII RPL 1
###### No Absen : 17 

# Modul 1

Soal
1. Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing.
2. Buatlah projek pertama laravel dengan nama projek “penjualan” dan tampilkan dalam browser.

```
composer create-project laravel/laravel penjualan
```

# Modul 2

Soal
1. Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam 
modul ini.

Langkah pertama
```
php artisan make:migration create_kategori_table
```

Langkah kedua
```
Isilah kode dibawah ini kedalam file migration create_kategori_table

<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
```

Untuk mengeksikusi, jalankan perintah berikut ditermial
```
php artisan migrate
```

Langkah ketiga

Membuat model
```
php artisan make:model kategori
```

Langkah keempat
```
Isilah kode dibawah ini kedalam file model kategori

<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class kategori extends Model
{
    use HasFactory;

    protected $table = 'kategori';
}
```

Untuk mengeksikusi, jalankan perintah berikut ditermial
```
php artisan make:model kegiatan
```

2. Berikan data dengan menggunakan seeder yang telah anda pelajari pada modul ini.

Langkah pertama

Untuk membuat seeder, gunakan perintah artisan pada command prompt sebagai berikut:
```
php artisan make:seeder kategoriTableSeeder
```

Langkah kedua
```
Isilah kode dibawah ini kedalam file seeder kategoriTableSeeder
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
                'nama' => 'Perlengkapan sekolah',
            ],
            [
                'nama' => 'Komputer',
            ],
            [
                'nama' => 'Sabun',
            ],
            [
                'nama' => 'Accesories',
            ],
            [
                'nama' => 'Atk',
            ]
            ));

        }
}
```

Langkah ketiga

```
Buka file data base dan isi code bagian public funcition run()
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(kategoriTableSeeder::class);
    }
}
```

Untuk mengeksikusi Seeder, jalankan perintah berikut ditermial
```
php artisan db:seed
```

Untuk melihat hasil dari seeder yang dibuat bukalah localhost/phpmyadmin pada browser lalu pilih 
database penjualan dan table produks maka hasilnya akan ada 2 data baru yang dihasilkan dari 
pembuatan seeder yang telah kita melakukan.






