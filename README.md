## Biodata 

Nama : Syafira Luthfi Azzahra

Kelas : TI.24.A.4

NIM : 312410353

# OOP-PYTHON
## Deskripsi
Program ini merupakan program manajemen data mahasiswa yang dibangun menggunakan Python. Program ini memungkinkan pengguna untuk menambah, mengubah, menghapus, dan mencari data mahasiswa. Data mahasiswa disimpan dalam format JSON, sehingga mudah untuk dibaca dan dikelola.

## Fitur
- Tambah data mahasiswa
- Ubah data mahasiswa
- Hapus data mahasiswa
- Cari data mahasiswa berdasarkan NIM
- Tampilkan semua data mahasiswa

## Struktur Proyek
![photo_2024-12-10_10-57-24](https://github.com/user-attachments/assets/54f6222d-98b9-46fb-93ac-dead367abace)

## Deskripsi Kode
### 1. `Data/mahasiswa.py`

File ini berisi definisi kelas `Mahasiswa` yang memiliki atribut `nama`, `nim`, dan `nilai`. Selain itu, terdapat beberapa fungsi untuk mengelola data mahasiswa:

- `tambah_mahasiswa(data_mahasiswa, mahasiswa)`: Menambahkan objek mahasiswa ke dalam daftar.
- `ubah_mahasiswa(data_mahasiswa, nim, nilai_baru)`: Mengubah nilai mahasiswa berdasarkan NIM.
- `hapus_mahasiswa(data_mahasiswa, nim)`: Menghapus mahasiswa dari daftar berdasarkan NIM.
- `cari_mahasiswa(data_mahasiswa, nim)`: Mencari mahasiswa berdasarkan NIM.
- `tampilkan_semua_mahasiswa(data_mahasiswa)`: Menampilkan semua data mahasiswa.

### 2. `View/input_form.py`
File ini berisi fungsi `input_data_mahasiswa()` yang digunakan untuk mengambil input dari pengguna untuk menambah data mahasiswa.

### 3. `View/mahasiswa.py`
File ini berisi fungsi `tampilkan_data_mahasiswa(mahasiswa)` yang digunakan untuk menampilkan informasi mahasiswa.

### 4. `Main.py`
File ini adalah file utama yang menjalankan aplikasi. Di dalamnya terdapat fungsi `load_data()` untuk memuat data dari file JSON dan `save_data(data)` untuk menyimpan data ke file JSON. Fungsi `main()` mengatur menu interaksi dengan pengguna.

```python
from dataclasses import Mahasiswa, DataMahasiswa
from view.input_from import InputForm
from view.mahasiswa import viewMahasiswa

def main():
    data_mahasiswa = DataMahasiswa()

    while True:
        print("\nMenu:")
        print("1. Tambah Data Mahasiswa")
        print("2. Hapus Data Mahasiswa")
        print("3. Ubah Data Mahasiswa")
        print("4. Cari Data Mahasiswa")
        print("5. Tampilkan Semua Data")
        print("6. Keluar")

        pilihan = input("Pilih menu: ")

        if pilihan == "1":
            nim, nama, jurusan = InputForm.input_mahasiswa()
            mahasiswa = Mahasiswa(nim, nama, jurusan)
            data_mahasiswa.tambah_data(mahasiswa)
            print("Data berhasil ditambahkan.")
        elif pilihan == "2":
            nim = input("Masukkan NIM mahasiswa yang akan dihapus: ")
            data_mahasiswa.hapus_data(nim)
            print("Data berhasil dihapus.")
        elif pilihan == "3":
            nim = input("Masukkan NIM mahasiswa yang akan diubah: ")
            nama_baru = input("Masukkan Nama baru: ")
            jurusan_baru = input("Masukkan Jurusan baru: ")
            data_mahasiswa.ubah_data(nim, nama_baru, jurusan_baru)
            print("Data berhasil diubah.")
        elif pilihan == "4":
            nim = input("Masukkan NIM mahasiswa yang akan dicari: ")
            mahasiswa = data_mahasiswa.cari_data(nim)
            View.Mahasiswa.tampilkan_detail(mahasiswa)
        elif pilihan == "5":
            semua_data = data_mahasiswa.tampilkan_semua_data()
            View.Mahasiswa.tampilkan_list(semua_data)
        elif pilihan == "6":
            print("Keluar dari program.")
            break
        else:
            print("Pilihan tidak valid.")

if __name__ == "main":
    main()
````

