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


