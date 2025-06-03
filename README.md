# TASK-REPOSITORY

---
#### Cek Kabisat dan Hitung Hari dengan Loop
---
##### Ini ilmu baru yang saya pelajari sekaligus pengalaman mencerna berbagai cara memahami system dan membuat codding walaupun belum sepenuhnya memahami,tetapi berusaha untuk tetap memperhatikan step by step yang diberikan.
---
def validasi_input():
    while True:
        try:
            tanggal = int(input("Masukkan tanggal (1-31): "))
            if tanggal < 1 or tanggal > 31:
                print("Tanggal harus antara 1 dan 31!")
                continue
            bulan = int(input("Masukkan bulan (1-12): "))
            if bulan < 1 or bulan > 12:
                print("Bulan harus antara 1 dan 12!")
                continue
            tahun = int(input("Masukkan tahun: "))
            if tahun < 1:
                print("Tahun harus positif!")
                continue
            return tanggal, bulan, tahun
        except ValueError:
            print("Harus masukkan angka!")

# Minta input valid
print("Masukkan tanggal untuk cek hari dan kabisat:")
tanggal, bulan, tahun = validasi_input()

# Cek kabisat untuk rentang tahun
print("\nCek tahun kabisat untuk rentang tahun:")
for i in range(tahun - 2, tahun + 3):
    if (i % 4 == 0 and i % 100 != 0) or (i % 400 == 0):
        print(f"Tahun {i} adalah tahun kabisat!")
    else:
        print(f"Tahun {i} bukan tahun kabisat!")

# Zeller’s Congruence untuk hitung hari
if bulan == 1 or bulan == 2:
    bulan += 12
    tahun -= 1
K = tahun % 100
J = tahun // 100
h = (tanggal + ((13 * (bulan + 1)) // 5) + K + (K // 4) + (J // 4) - 2 * J) % 7
print("\nHasil perhitungan hari:")
if h == 0:
    print(f"Tanggal {tanggal}/{bulan}/{tahun} adalah hari Sabtu!")
elif h == 1:
    print(f"Tanggal {tanggal}/{bulan}/{tahun} adalah hari Minggu!")
elif h == 2:
    print(f"Tanggal {tanggal}/{bulan}/{tahun} adalah hari Senin!")
elif h == 3:
    print(f"Tanggal {tanggal}/{bulan}/{tahun} adalah hari Selasa!")
elif h == 4:
    print(f"Tanggal {tanggal}/{bulan}/{tahun} adalah hari Rabu!")
elif h == 5:
    print(f"Tanggal {tanggal}/{bulan}/{tahun} adalah hari Kamis!")
else:
    print(f"Tanggal {tanggal}/{bulan}/{tahun} adalah hari Jumat!")
__________
__________
__________
#### Fungsi validasi_input ( ):
Meminta input tanggal, bulan dan tahun yang diisi dan memvalidasinya. Setelah itu hasil akan difilter oleh fungsi try: dan exept ValueError:
Jika input bukan angka : Kembali ke fungsi return Kembali lagi ke tanggal,bulan dan tahun. Jika input angka dan sesuai fungs if ( tanggal <=31,bulan<=12 dan tahun >0 maka Valid.

def validasi_input():
    while True:
        try:
            tgl = int(input("Masukkan tanggal (1-31): "))
            bln = int(input("Masukkan bulan (1-12): "))
            thn = int(input("Masukkan tahun: "))
            if 1 <= tgl <= 31 and 1 <= bln <= 12 and thn > 0:
                return tgl, bln, thn
            print("Input tidak valid. Coba lagi.")
        except ValueError:
            print("Harus masukkan angka!")

##### Fungsi input:
Meminta fungsi input dan menyimpanhaasilanya dalam variable tgl,bln,thn.

print("Masukkan tanggal untuk cek hari dan kabisat:")
tgl, bln, thn = validasi_input()

#### Cek Tahun kabisat:
Memunculkan hasil apakah termasuk tahun kabisat dari rentan waktu 2 tahun sebelum dan 2 tahun setelah dari hasil input tahun.
Sementara itu perhitungan tahun kabisat yaitu :
“Habis dibagi 4 dan bukan habis dibagi 100 atau habis dibagi 400.

print("\nCek tahun kabisat:")
for i in range(thn - 2, thn + 3):
    status = "kabisat" if (i % 4 == 0 and i % 100 != 0) or (i % 400 == 0) else "bukan kabisat"
    print(f"Tahun {i} adalah {status}")

#### Hitung hari dari Zeller’s Congruence :
Jika bulan Januari/Februari bulan diganti menjadi 13/14 dan tahun dikurangi -1 K=dua digit terakhir tahun dan J= dua digit terakhir tahun.
Menentukan nama hari :
Hari [h]: mengakses nama hari berdasarkan hasil [h] Jika [h=2] maka hasilnya Senin.
    
b, t = (bln + 12, thn - 1) if bln < 3 else (bln, thn)
K, J = t % 100, t // 100
h = (tgl + (13 * (b + 1)) // 5 + K + K // 4 + J // 4 - 2 * J) % 7
hari = ["Sabtu", "Minggu", "Senin", "Selasa", "Rabu", "Kamis", "Jumat"]

print(f"\nTanggal {tgl}/{bln}/{thn} adalah hari {hari[h]}!")
