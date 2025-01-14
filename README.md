### Praktikum 1 [ Komputasi Numerik B ] Kelompok 8
| Nama                      | NRP           |
|---------------------------|---------------|
|Moh rosy haqqy aminy       |5025211012     |
|Charles                    |5025211082     |
|Hammuda Arsyad             |5025211146     |

### Library Yang Digunakan
Library yang digunakan adalah pandas, numpy, matplotlib, dan Equation

### Code

```python
# Tugas Praktikum Membuat Metode Bolzano Menggunakan Python Kelompok 8

# Ditulis oleh :
#   Moh. Rosy Haqqy Aminy (5025211012)
#   Hammuda Arsyad (5025211146)
#   Charles (5025211082)

# Problem : Membuat metode bolzano menggunakan python dan menampilkan tabel iteratif serta grafik fungsi
# Solve : Menggunakan library python pandas sebagai representasi tabel dan matplotlib untuk menampilkan grafik fungsi.
#         Penyelesaian dibantu juga dengan library numpy dan Equation untuk mempermudah perhitungan.

import math
import numpy as np
import pandas as pd
from Equation import Expression
from matplotlib import pyplot as plt

# Presisi sebelum iterasi berhenti
precision = 0.01

# fungsi untuk mengembalikan suatu string persamaan menjadi persamaan matematika
def f(x):
    return (Expression(x))
    
# Untuk function yang complex, perlu dimasukkan secara manual
# Contoh complex equation :
# euler = math.e
# e**x = np.exp()
# log =  math.log(a, base)
# natural log = np.log(x)

# copy function di bawah ini dan comment function di atas untuk menggunakan complex equation
# np.log(x) (semua yang ada fx harus diganti dengan ini!)

# fungsi untuk menggambar grafik
def plotChart(f, equ, c, d):

    # x dan y untuk grafik
    x = np.arange(c, d, 0.01)
    y = [(f(i)) for i in x]

    # setting untuk grafik
    plt.figure(figsize=(14, 8))
    plt.grid(which = 'both', color = 'grey')
    plt.plot(x, y, label = equ, color='black', linewidth = 2, linestyle='-')
    plt.legend()
    plt.title("Grafik Fungsi")
    plt.xlabel("x", fontsize = 12, color = 'black')
    plt.ylabel("y", fontsize = 12, color = 'black')
    plt.show()

# metode bolzano
def bolzano(f, x0, x1):

    # jika f(x0)*f(x1)>0 berarti rentang antara dua titik yang dipilih tidak memiliki akar
    if f(x0)*f(x1) > 0:
        print("Tidak ada perpotongan antara kedua titik x tersebut!")
    else:
        # buat dataframe kosong
        tabel = pd.DataFrame()

        # Kalau pakai precision
        # ft = 1
        # while abs(ft) > precision:

        # Kalau pakai iterasi yang sudah ditentukan
        n = 0
        # while n < 15

        # looping dengan metode bolzano hingga suatu ketelitian tercapai
        while n < 15:
            # data yang dicari
            xt = (x0 + x1)/2
            f0 = f(x0)
            f1 = f(x1)
            ft = f(xt)
            n = n + 1

            # memasukkan data ke tabel
            tab = pd.DataFrame([[x0, x1, xt, f0, f1, ft]], columns=['x0', 'x1', 'xt', 'f0', 'f1', 'ft'])
            tabel = pd.concat([tabel, tab], ignore_index=True)

            # penentuan x yang akan diganti
            if ft < 0:
                if(f0) < 0:
                    x0 = xt
                else:
                    x1 = xt
            elif ft > 0:
                if(f0) > 0:
                    x0 = xt
                else:
                    x1 = xt
            else:
                break
        
        # terakhir, tampilkan tabel
        tabel.index = np.arange(1, len(tabel)+1)
        print(tabel)
        print(f"\nNilai x yang didapatkan adalah {xt}\n")

# function untuk menyelesaikan dengan metode bolzano serta menampilkan grafik
def solve(equ, a, b, c, d):
    fn = f(equ)
    print("Tabel iterasi : ")
    bolzano(fn, a, b)
    print("Grafik fungsi : \n")
    plotChart(fn, equ, c, d)

# Mengambil persamaan dari user
equ = input("Masukkan persamaan (contoh : x^2+cos(x)+2*x+3) : ")

# Titik untuk melakukan bisection method
print("Masukkan letak akar yang ingin dicari antara kedua titik x!")
a = float(input("x pertama : "))
b = float(input("x kedua : "))

# Rentang grafik yang akan ditampilkan
print("Masukkan rentang grafik yang ingin ditampilkan! (batas awal hingga batas akhir dari x)")
c = float(input("Batas awal : "))
d = float(input("Batas akhir : "))

# Menyelesaikan problem
solve(equ, a, b, c, d)
Footer
© 2022 GitHub, Inc.
Footer navigation
Terms

```  

### Contoh Pengerjaan Soal Dengan Metode Bolzano Menggunakan Google Collab
![image](https://user-images.githubusercontent.com/115076652/197742015-f792f57e-ee26-4ef7-b701-2fec43a97f88.png)
![image](https://user-images.githubusercontent.com/115076652/197742182-5ae395dd-c3f4-4ca0-829d-fc5bb0c006a9.png)

### Link Google Collab
https://colab.research.google.com/drive/1MWOivJvrUy0-HCLUct_gzF4V8VyVcYdz?usp=sharing
