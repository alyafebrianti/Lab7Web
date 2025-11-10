# Lab7Web
# Data Mahasiswa
## Nama : Alya Febrianti
## Kelas : TI.24.A1
## NIM : 312410692
## Mata Kuliah : Pemrograman Web 1

# code
```php
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Program Input dan Output Terintegrasi</title>
    <style>
        body { font-family: Arial, sans-serif; background-color: #f4f4f4; display: flex; justify-content: center; align-items: center; min-height: 100vh; margin: 0; }
        .container { width: 500px; padding: 30px; background-color: white; border-radius: 8px; box-shadow: 0 0 15px rgba(0,0,0,0.1); }
        h2 { color: #333; border-bottom: 2px solid #007bff; padding-bottom: 10px; margin-bottom: 20px; }
        label, select, input[type="text"], input[type="date"] { display: block; margin-bottom: 15px; width: 100%; padding: 10px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px; }
        input[type="submit"] { background-color: #4CAF50; color: white; padding: 12px 20px; border: none; border-radius: 4px; cursor: pointer; font-size: 16px; }
        .output-result { margin-top: 20px; padding: 15px; border: 1px solid #007bff; background-color: #e6f7ff; border-radius: 5px; }
        .output-result p { margin: 5px 0; line-height: 1.6; }
        .output-result strong { color: #0056b3; }
    </style>
</head>
<body>
    <div class="container">
        <?php
        $show_output = false;
        
        
        if ($_SERVER["REQUEST_METHOD"] == "POST") {
            
          
            $nama = $_POST['nama'] ?? '';
            $tanggal_lahir = $_POST['tanggal_lahir'] ?? '';
            $pekerjaan_key = $_POST['pekerjaan'] ?? '';
            
            if ($nama && $tanggal_lahir && $pekerjaan_key) {
                $show_output = true;

               
                try {
                    $tgl_lahir_obj = new DateTime($tanggal_lahir);
                    $hari_ini = new DateTime();
                    $umur = $tgl_lahir_obj->diff($hari_ini)->y;
                } catch (Exception $e) {
                    $umur = "Tanggal tidak valid";
                    $show_output = false; 
                }

              
                $daftar_gaji = [
                    'programmer' => ['nama' => 'Programmer', 'gaji' => 'Rp 50.000.000'],
                    'designer' => ['nama' => 'Designer Grafis', 'gaji' => 'Rp 28.500.000'],
                    'manager' => ['nama' => 'Manager Proyek', 'gaji' => 'Rp 25.000.000'],
                    'guru' => ['nama' => 'Guru Sekolah', 'gaji' => 'Rp 15.000.000']
                ];
                
               
                $info_pekerjaan = $daftar_gaji[$pekerjaan_key] ?? ['nama' => 'Pekerjaan Tidak Diketahui', 'gaji' => 'Tidak Tersedia'];
                $nama_pekerjaan = $info_pekerjaan['nama'];
                $gaji = $info_pekerjaan['gaji'];
            }
        }

        if ($show_output) {
            ?>
            <h2>✅ Hasil Data Pengguna</h2>
            <div class="output-result">
                <p>Nama Lengkap: <strong><?php echo htmlspecialchars($nama); ?></strong></p>
                <p>Tanggal Lahir: <strong><?php echo htmlspecialchars($tanggal_lahir); ?></strong></p>
                <p>Usia Saat Ini: <strong><?php echo $umur; ?> tahun</strong></p>
                <p>Pekerjaan: <strong><?php echo $nama_pekerjaan; ?></strong></p>
                <p>Estimasi Gaji: <strong><?php echo $gaji; ?></strong></p>
            </div>
            <hr>
            <?php
        }
        ?>

        <h2>📝 Input Data Pengguna</h2>
        <form method="POST" action="lab7.php"> 
            <label for="nama">Nama Lengkap:</label>
            <input type="text" id="nama" name="nama" required value="<?php echo htmlspecialchars($_POST['nama'] ?? ''); ?>">

            <label for="tanggal_lahir">Tanggal Lahir:</label>
            <input type="date" id="tanggal_lahir" name="tanggal_lahir" required value="<?php echo htmlspecialchars($_POST['tanggal_lahir'] ?? ''); ?>">
            
            <label for="pekerjaan">Pilih Pekerjaan:</label>
            <select id="pekerjaan" name="pekerjaan" required>
                <option value="">-- Pilih salah satu --</option>
                <option value="programmer" <?php echo (($_POST['pekerjaan'] ?? '') == 'programmer' ? 'selected' : ''); ?>>Programmer</option>
                <option value="designer" <?php echo (($_POST['pekerjaan'] ?? '') == 'designer' ? 'selected' : ''); ?>>Designer Grafis</option>
                <option value="manager" <?php echo (($_POST['pekerjaan'] ?? '') == 'manager' ? 'selected' : ''); ?>>Manager Proyek</option>
                <option value="guru" <?php echo (($_POST['pekerjaan'] ?? '') == 'guru' ? 'selected' : ''); ?>>Guru Sekolah</option>
            </select>
            
            <input type="submit" value="Tampilkan Hasil dan Hitung">
        </form>
    </div>
</body>
</html>
```

# Tampilan
![Gambar WhatsApp 2025-11-10 pukul 15 46 11_2831f1e0](https://github.com/user-attachments/assets/92df8177-2a3d-4a83-9b44-25bbc5bb7f08)
![Gambar WhatsApp 2025-11-10 pukul 15 46 13_870dd40c](https://github.com/user-attachments/assets/da620629-6387-4452-adcf-d8af92d79597)
![Gambar WhatsApp 2025-11-10 pukul 15 46 12_365d2b22](https://github.com/user-attachments/assets/73369d45-f690-462c-a95b-8780a5e249bc)
![Gambar WhatsApp 2025-11-10 pukul 15 46 13_70bd1d8c](https://github.com/user-attachments/assets/0d770e92-e3cf-46ca-9c39-031b1b498480)
![Gambar WhatsApp 2025-11-10 pukul 15 46 11_6dec03d4](https://github.com/user-attachments/assets/d6cbaf58-d5c2-4459-89fd-c6c82acd2c35)
![Gambar WhatsApp 2025-11-10 pukul 15 46 12_f65c91f0](https://github.com/user-attachments/assets/ff94790e-7560-4151-a28c-bf5a8d420935)





