# **Package & Module**

# **Module**
# Pengertian Module
- Modul merupakan bagian dari program yang berisi fungsi-fungsi yang dibuat pada file terpisah.
- Dengan adanya modul-modul yang terpisah, dapat dikelompokkan sesuai dengan fungsinya dan memudahkan dalam mengelola kode
program.
- Modul dapat dipanggil sesuai dengan kebutuhannya.
# Membuat Module
• Buat sebuah file kode program python (ekstensi .py)
• Buat fungsi pada file tersebut. Contoh:
Filename: example.py
# Python Module example
```
def add(a, b):
 """This program adds two
 numbers and return the result"""
 result = a + b
 return result
 ```
# Menggunakan Module
• Untuk menggunakan modul yang telah dibuat cukup menggunakan
perintah import
Contoh:
```
>>> import example
>>> example.add(4,5.5)
9.5

# import module by renaming it
import math as m
print("The value of pi is"
, m.pi)
```

# **Package**

# Pengertian Package
• Package merupakan namespace yang berisi banyak modul dan paket. • Package merupakan sebuah direktory yang berisi banyak file-file modul. 
• Setiap package pada Python, harus ada file khusus yang bernama __init__.py
• File tersebut merupakan file kosong, atau bisa juga diisi dengan sesuatu.
# Membuat Package
Untuk membuat package pada Python cukup mudah. • Buat sebuah directory (folder), dan tambahkan file kosong dengan nama __init__.py
• Buat sejumah file kode program python (ekstensi .py) pada folder tersebut yang berisi fungsi-fungsi (modul program)
• Untuk menggunakan package yang telah dibuat cukup menggunakan perintah import
```
import nama_package.nama_module
atau
from nama_package import nama_module
```

# **Tugas**
Buat package dan modul berdasarkan tugas praktikum sebelumnya dengan struktur seperti berikut:
• daftar_nilai.py berisi modul untuk:
tambah_data, ubah_data, hapus_data, dan
cari_data
• view_nilai.py berisi modul untuk:
cetak_daftar_nilai, cetak_hasil_pencarian
• input_nilai.py berisi modul untuk: input_data
yang meminta pengguna memasukkan data. • main.py berisi program utama (menu pilihan
yang memanggil semua menu yang ada)

# Package Input Nilai
```
def input_nama():
    global nama
    nama = input("Masukkan Nama        : ")
    return nama

def input_nim():
    global nim
    nim = input("Masukkan NIM         : ")
    return nim

def input_nilaiTugas():
    global nilaiTugas
    nilaiTugas = int(input("Masukkan Nilai Tugas : "))
    return nilaiTugas

def input_nilaiUts():
    global nilaiUts
    nilaiUts = int(input("Masukkan Nilai UTS   : "))
    return nilaiUts

def input_nilaiUas():
    global nilaiUas
    nilaiUas = int(input("Masukkan Nilai UAS   : "))
    return nilaiUas
```
- Screenshot
![Input Nilai](https://user-images.githubusercontent.com/22215113/71729769-254ad780-2e73-11ea-900a-a0b349f28fd8.png)

# Package Daftar Nilai
```
from view.input_nilai import *

dataMhs = {}

def tambah_data():
    global dataMhs
    nama = input_nama()
    nim = input_nim()
    nilaiTugas = input_nilaiTugas()
    nilaiUts = input_nilaiUas()
    nilaiUas = input_nilaiUas()
    nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
    dataMhs[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
    print("\nData Berhasil Ditambahkan!")
    return dataMhs

def ubah_data():
    nama = input("Masukkan Nama: ")
    if nama in dataMhs.keys():
        nim           = input_nim()
        nilaiTugas    = input_nilaiTugas()
        nilaiUts      = input_nilaiUts()
        nilaiUas      = input_nilaiUas()
        nilaiAkhir    = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
        dataMhs[nama]  = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
        print("\nData Berhasil Di Update!")
    else:
        print("Data tidak ditemukan!")

def hapus_data():
    nama = input("Masukkan Nama:  ")
    if nama in dataMhs.keys():
        del dataMhs[nama]
        print("Data",nama,"Telah dihapus!")
    else:
        print("Data Mahasiswa Tidak Ada".format(nama))
```
- Screenshot
![Daftar Nilai (1)](https://user-images.githubusercontent.com/22215113/71729767-24b24100-2e73-11ea-816f-7d28938a6a13.png)
![Daftar Nilai (2)](https://user-images.githubusercontent.com/22215113/71729768-254ad780-2e73-11ea-89e0-8590cf9d4cb9.png)

# Package View Nilai
```
from model.daftar_nilai import *

def cetak_daftar_nilai():
    if dataMhs.items():
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        i = 0
        for x in dataMhs.items():
            i += 1
            print("| {6:2} | {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6} |".format(x[0], x[1][0], x[1][1], x[1][2],
                                                                                        x[1][3], x[1][4], i))
        print("==================================================================")
    else:
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        print("|                          TIDAK ADA DATA!                       |")
        print("==================================================================")

def cetak_hasil_pencarian():
    nama = input("Masukkan Nama        : ")
    if nama in dataMhs.keys():
        print("\n                   DAFTAR NILAI MAHASISWA                   ")
        print("==============================================================")
        print("|     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir  |")
        print("==============================================================")
        print("| {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6}  |".format(nama, dataMhs[nama][0], dataMhs[nama][1],
                                                                            dataMhs[nama][2], dataMhs[nama][3],
                                                                            dataMhs[nama][4]))
        print("==============================================================")
    else:
        print("Datanya {0} Tidak Ada ".format(nama))
```
- Screenshot
![View Nilai (1)](https://user-images.githubusercontent.com/22215113/71729772-267c0480-2e73-11ea-9ceb-25e19e5d8232.png)
![View Nilai (2)](https://user-images.githubusercontent.com/22215113/71729773-267c0480-2e73-11ea-893b-537af9b0a4bd.png)

# Main
```
from model.daftar_nilai import *
from view.view_nilai import *

while True:
    c = input("\nA)dd, E)dit, S)earch, D)elete L)ist, Q)uit: ")

    if (c.lower() == 'a'):
        tambah_data()

    elif (c.lower() == 'e'):
        ubah_data()

    elif (c.lower() == 's'):
        cetak_hasil_pencarian()

    elif (c.lower() == 'd'):
        hapus_data()

    elif (c.lower() == 'l'):
        cetak_daftar_nilai()

    elif (c.lower() == 'q'):
        break

    else:
        print("Silahkan pilih menu yang tersedia!")
```
- Screenshot
![Main](https://user-images.githubusercontent.com/22215113/71729770-25e36e00-2e73-11ea-8d68-2b3dad331ef4.png)

```
                                                    Veno Setyoaji Wiratama
                                                           311910363
                                                           TI.19.A.2
                                                   Universitas Pelita Bangsa
```
