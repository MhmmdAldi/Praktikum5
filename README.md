# praktikum5-bahasa pemrograman

Repositiry ini dibuat untuk memenuhi tugas Bahasa Pemrograman (Module Praktikum 5)<br><br>
Nama : Muhammad Aldiansyah <br>
NIM : 312210118<br>
Dosen : Agung Nugroho, M.Kom<br>
Matkul : Bahasa Pemrograman<br>
Kelas : TI.22.B.1<br>

Pada halaman ini (Bahasa Pemrograman-Module Praktikum 5) Dosen memberi tugas sebagai berikut : <br>
* Soal Latihan yang ada pada module praktikum 5<br>
![Latihan-soal1](https://user-images.githubusercontent.com/115475098/204083133-32f95612-cebb-4740-b060-0830b5cac022.png)<br>
* Berikut adalah program syntax yang saya buat untuk memenuhi latihan module 5<br>

``` python
print("===================================================================")
print("Nama         :   Muhammad Aldiansyah")
print("NIM          :   312210118")
print("Kelas        :   TI.22.B1")
print("Mata Kuliah  :   Bahasa Pemrograman")
print("===================================================================")

# Buat dictionary daftar kontak
print("Buat dictionary nama sebagai key, dan nomor sebagai value")

isi = {'Ari': '081267888', 'Dina': '087677776'}
print("Nama | Nomor kontak")
print(isi)

print("Tampilkan Kontaknya Ari")
print(isi['Ari'])

print("Tambah kontak baru dengan nama Riko, nomor 087654544")
isi['Riko']= '087654544'
print(isi)

print("Ubah kontak Dina dengan nomor baru 088999776")
isi['Dina']= '088999777'
print(isi)

print("Tampilkan semua Nama")
print(isi.keys())

print("Tampilkan semua Nomor")
print(isi.values())

print("Tampilkan daftar Nama dan nomornya")
print(isi.items())

print("Hapus kontak Dina")
del isi['Dina']
print(isi)

print("===================================================================")
```
* Ini adalah hasil run dari syntax latihan module 5 yang saya buat <br>
![Hasil1](https://user-images.githubusercontent.com/115475098/204083165-012f7f31-ee09-4eb2-a265-a38cd230d0e7.png)<br>

* Soal Tugas Praktikum yang ada pada module praktikum 5 adalah sebagai berikut<br>
![Latihan-soal2](https://user-images.githubusercontent.com/115475098/204083187-3c38bf3e-d708-4183-ae8f-09d64c98b262.png)<br>
* Berikut hasil yang diinginkan pada soal praktikum  5<br>
![Latihan-soal3](https://user-images.githubusercontent.com/115475098/204083220-fc2734dc-da6d-4e9c-bb85-26b116e401b3.png)<br>
![Latihan-soal4](https://user-images.githubusercontent.com/115475098/204083240-056777ea-c99f-4f59-acf6-8f9a90ff5fe4.png)<br>

* Setelah memahami materi saya membuat syntax sebagai berikut untuk memenuhi tugas praktikum module 5 : <br>
```python
from prettytable import PrettyTable

print("===================================================================")
print("Nama         :   Muhammad Aldiansyah")
print("NIM          :   312210118")
print("Kelas        :   TI.22.B1")
print("Mata Kuliah  :   Bahasa Pemrograman")
print("===================================================================")

baris = []
x = PrettyTable()

while True:
    print("[ (L)ihat , (T)ambah, (U)bah, (H)apus, (C)ari, (K)eluar ]")
    tanya = input("Masukkan Pilihan : ")
    if tanya == "L":
        print("==== Daftar Nilai ====")
        no = 0
        no += 1
        x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
        if not baris:
            x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
            print("Not Data")
        else:
            for data in baris:
                x.add_row([no, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
            print(x)
    elif tanya == "T":
        print("Tambah Data ")
        nim_v = input("NIM : ")
        nama_v = input("Nama Lengkap : ")
        uts_v = input("Nilai UTS : ")
        uas_v = input("Nilai UAS : ")
        tugas_v = input("Nilai Tugas : ")
        akhir_v = 0.3 * float(tugas_v) + 0.35 * float(uts_v) + 0.35 * float(uas_v)
        baris.append({"nim": nim_v, "nama": nama_v, "tugas": tugas_v, "uts": uts_v, "uas": uas_v, "akhir": akhir_v})
        print()
        print("==== Daftar Nilai ====")
        i = 0
        for data in baris:
            i += 1
            x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
            x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
        print(x)
    elif tanya == "U":
        print("Edit File")
        print("Data siapa yang akan diubah ?")
        siapa = input("Masukkan NIM Mahasiswa yang akan diubah : ")

        print("Data apa yang akan diubah ? : ")
        mhs = input(" 1. Nama \n 2. Nilai Tugas \n 3. Nilai UTS \n 4. Nilai UAS\n Pilih dengan angka (1/2/3/4) : ")
        if mhs == "1":
            ubahnama = input("Silahkan masukan nama yang benar : ")
            i = 0
            d = next(item for item in baris if item['nim'] == siapa)
            d['nama'] = ubahnama
            x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
            i += 1
            x.add_row([i, d["nim"], d["nama"], d["tugas"], d["uts"], d["uas"], d["akhir"]])
            print(x)
        elif mhs == "2":
            ubahtugas = input("Masukkan Nilai Tugas yang benar : ")
            i = 0
            d = next(item for item in baris if item['nim'] == siapa)
            d['tugas'] = ubahtugas
            lihatuts = d['uts']
            lihatuas = d['uas']
            lihatakhir = 0.3 * float(ubahtugas) + 0.35 * float(lihatuts) + 0.35 * float(lihatuas)
            d['akhir'] = lihatakhir
            x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
            for data in baris:
                i += 1
                x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
            print(x)
        elif mhs == "3":
            ubahuts = input("Masukkan Nilai UTS yang benar : ")
            i = 0
            d = next(item for item in baris if item['nim'] == siapa)
            d['uts'] = ubahuts
            lihattugas = d['tugas']
            lihatuas = d['uas']
            lihatakhir = 0.3 * float(lihattugas) + 0.35 * float(ubahuts) + 0.35 * float(lihatuas)
            d['akhir'] = lihatakhir
            x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
            for data in baris:
                i += 1
                x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
            print(x)
        elif mhs == "4":
            ubahuas = input("Masukkan Nilai UAS yang benar : ")
            i = 0
            d = next(item for item in baris if item['nim'] == siapa)
            d['uas'] = ubahuas
            lihattugas = d['tugas']
            lihatuts = d['uts']
            lihatakhir = 0.3 * float(lihattugas) + 0.35 * float(lihatuts) + 0.35 * float(ubahuas)
            d['akhir'] = lihatakhir
            x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
            for data in baris:
                i += 1
                x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
            print(x)
        else:
            print("Pilihan Salah")

    elif tanya == "C":
        print(" ========== Pencarian Data ==========")
        print(" Pencarian berdasarkan NIM ")
        carinim = input("Masukkan NIM yang akan dicari : ")
        xdata = next(item for item in baris if item['nim'] == carinim)
        print("NIM : ", carinim)
        print("Nama : ", xdata['nama'])
        print("Nilai Tugas : ", xdata['tugas'])
        print("Nilai UTS : ", xdata['uts'])
        print("Nilai UAS : ", xdata['uas'])
        print("Nilai Akhir : ", xdata['akhir'])
    elif tanya == "H":
        print("Hapus Data Berdasarkan NIM")
        datahapus = input("Masukkan NIM data yang akan dihapus : ")
        xhapus = next(item for item in baris if item['nim'] == datahapus)
        del xhapus['nim']
        del xhapus['nama']
        del xhapus['tugas']
        del xhapus['uts']
        del xhapus['uas']
        del xhapus['akhir']
        print("Data Berhasil Dihapus")
        no = 0
        no += 1
        x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
        if not baris:
            x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
            print("Not Data")
        else:
            for data in baris:
                x.add_row([no, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
            print(x)

    elif tanya == "K":
        print("Anda Keluar Dari Aplikasi")
        break
    else:
        print("Anda Memilih Pilihan Yang Salah")
```
* Berikut ini adalah hasil run dari syntax diatas akan diuraikan satu persatu<br>
* *Lihat data sebelum data ditambahkan*<br>
![Hasil2(1)](https://user-images.githubusercontent.com/115475098/204083684-16ee59d5-5b76-4770-b76d-3827c9ac108b.png)<br>
* *Tambah data*<br>
![Hasil3](https://user-images.githubusercontent.com/115475098/204083715-79fc2f72-ca9d-4d47-9cb9-afb4672675ff.png)<br>
* *Lihat setelah tambah data*<br>
![Hasil4](https://user-images.githubusercontent.com/115475098/204083744-29635215-5074-4768-b090-b4f34f1b4920.png)<br>
* *Ubah data, dan pada gambar dibawah adalah hasil dari perubahan data*<br>
![Hasil6](https://user-images.githubusercontent.com/115475098/204083767-9ad6041c-f0cd-4152-b8fc-a0e29cd5833a.png)<br>
* *Mencari data yang diinputkan*<br>
![Hasil5](https://user-images.githubusercontent.com/115475098/204083780-df472efa-9158-46ef-aff7-cc18fb1d94c6.png)<br>
* *Menghapus data yang diinputkan*<br>
![Hasil7](https://user-images.githubusercontent.com/115475098/204083800-dda3556e-d8d9-4fba-9382-fd52a7a49c76.png)<br>
* *Keluar dari program aplikasi*<br>
![Hasil8](https://user-images.githubusercontent.com/115475098/204083833-aa0958f2-13fd-4ff3-96c1-eaefb7020e48.png)<br>
### Berikut langkah langkah untuk tugas Praktikum5, Terimakasih...
