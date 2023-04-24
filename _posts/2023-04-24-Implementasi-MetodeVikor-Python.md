---
title: Implementasi Metode Vikor Menggunakan Python
author: mrhmt
date: 2023-4-24 07:00:00 +/-
categories: [coding]
tags: [coding]
toc: true # table of content
comments: true 
math: true
mermaid: true # diagram generation tool
image:
    src: https://www.inixindo.id/wp-content/uploads/2022/03/python-programming-intro-870x520.jpg
    width: 870 
    height: 520
    alt: Inixindo.id
pin: false
excerpt_separator: <!--more-->
published: true
---

# 1. Pengantar
Metode Vikor merupakan metode Multi-Criteria Decision Making (MCDM) yang dapat digunakan untuk
menyeleksi lebih dari satu kriteria. Metode VIKOR berfokus dalam perangkingan dengan mengkompromi dari hasil alternatif dan kriteria yang bertentangan.

<!--more-->
# 2. Persiapkan 
- IDE (Menggunakan Pycharm)
- Kopi

# 3. Implementasi Dan Hasil 

````python
#import library
import numpy as np
import pandas as pd
from decipy import executors as exe

#data dummy nilai dari setiap alternatif
matrix = np.array([
    [5, 5, 5],
    [4, 4, 5],
    [4, 4, 4],
    [3, 3, 3],
    [3, 2, 1],
    [2, 3, 3],
    [3, 2, 3],
    [2, 1, 1],
    [1, 2, 1],
    [1, 1, 1],

])

#alternatif
personel = ['Arya', 'Achmad', 'Rian','DEWO','DERRY','DENY','FILHAM','FIRMAN','ARIF','DODY']

# Kriteria
crits = ['Taktis', 'Teknis', 'Strategis']

# Tipe Kriteria Benefit / Cost, Studi Kasus Menggunakan Benefit
beneficial = [True, True, True]

# Nilai Bobot
weights = [0.10, 0.20, 0.30]

# Proses Kalkulasi Vikor
xij = pd.DataFrame(matrix, index=personel, columns=crits)

kwargs = {
    'data': xij,
    'beneficial': beneficial,
    'weights': weights,
    'rank_reverse': True,
    'rank_method': "ordinal"
}

# Code untuk Menjalankan Vikor
vikor = exe.Vikor(**kwargs) # Vikor

#Menampilkan Nilai Alternatif kriteria,dll
#Hasil Kandidat Personel Dengan Menggunakan Metode Vikor Akan muncul disini
print("Alternatif")
print(str(personel))

print("kriteria")
print(str(crits))

print("tipe kriteria")
print(str(beneficial))

print("bobot setiap kriteria")
print(str(weights))


print("Hasil Perangkingan Vikor")
print(vikor.dataframe)

````

# 4. Referensi
- Suniantara, I Ketut & Suwardika, Gede. (2018). Penerapan Metode VIKOR pada Pengambilan Keputusan Seleksi Calon Penerima Beasiswa Bidikmisi Universitas Terbuka. INTENSIF. 2. 24. 10.29407/intensif.v2i1.11848. 
- Arsyah, U. I., Nasution, A. R. ., Sweety, M. ., & Toar, M. J. . (2023). Sistem Pendukung Keputusan Penentuan Bayi Gizi Baik dan Buruk Metode VIKOR. Sistem Pendukung Keputusan Dengan Aplikasi, 2(1), 35–45. https://doi.org/10.55537/spk.v2i1.611
- Kristianto, Brian & Suryadibrata, Alethea & Hansun, Seng. (2021). Rekomendasi Pemilihan Mobil dengan Algoritma VIKOR. Jurnal Sains dan Informatika. 7. 97-106. 10.34128/jsi.v7i1.269. 
- https://extra.cahyadsn.com/vikor

