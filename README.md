# Lua - Panduan Dasar (Bahasa Indonesia)

## Menampilkan tulisan
```lua
print("Hello World")
```

## Komentar
```lua
--ini adalah komentar
print("hello") --ini komentar juga
-- baris berikutnya tidak akan dijalankan karena dia berupa komentar
--print("world") 
```

## Variabel


```lua
-- Tipenya berbeda beda
local x = 10 --number
local nama = "Roni" --string
local nyala = false -- boolean
local a = nil --tidak ada nilai 
```

**Number**

operator
- \+ pertambahan
- \- pengurangan
- \* perkalian
- / pembagian
- ^ perpangkatan
- % modulus (sisa pembagian)

```lua
-- contoh
local a = 1
local b = 2
local c = a + b
print(c) -- 3

local d = b - a
print(d) -- 1

local x =  1 * 3 * 4 -- 12
print(x)

local y = (1+3) * 2 -- 8
print(y)


print(10/2) -- 5
print (2^2) -- 4
print(5%2) -- 1

print(-b) -- -2
```

```lua
-- increment
local level = 1
level = level + 1
print(level) -- 2
```

**String**
```lua
-- menggabungkan string
local kalimat = "Namaku adalah "
local nama = "Roni"
print(kalimat .. nama) --Namaku adalah Roni

-- string dan number
local umur = 12
local nama = "Irfan"
print(nama .. " berumur " .. age .. " tahun")
````

**Boolean**
```lua
local nyala = true
print(nyala) --true
nyala = false
print(nyala) --false
```

## Pengkondisian
```lua
--Membandingkan angka
local umur = 10
if umur > 18 then
  print("di atas 18 tahun") --tidak akan dieksekusi
end

--elseif dan else
umur = 20
if umur > 18 then
  print("di atas 18 tahun")
elseif umur == 18 then
  print("tepat 18 tahun")
else
  print("di bawah 18 tahun")
end
```

**Operator Perbandingan**
- == sama dengan
- < lebih kecil dari
- \> lebih besar dari
- <= lebih kecil dari atau sama dengan
- \>= lebih besar dari atau sama dengan
- ~= tidak sama dengan

```lua
--perbandingan boolean
local nyala = true
if nyala then
    print("Akhirnya nyala!")
end

--perbandingan string
local nama = "irfan"
if nama == "Irfan" then --false
  print("Irfan")
elseif nama == "irfan" then --true
  print("irfan")
end

```

**Kombinasi If**
```lua
local x = 10
if x == 10 and x < 0 then --keduanya harus bernilai true
  print("halo")
elseif x == 100 or x > 0 then --salah satunya harus bernilai true
  print("hai")
end
--hasil: hai
```

**If bercabang**

```lua
local x = 10
local nyala = true
if x==10 then
  if nyala == true then
    print("halo")
  else
    print("hai")
  end
end
```
**Membalikkan Nilai**

Kita juga bisa membalikkan nilai dengan kata kunci **not**
```lua
local x = 10
if not x == 10 then -- false
  print("halo") -- tidak dieksekusi
end
```

## Function
```lua
function tambahDua(angka)
  local hasil = angka + 2
  print("hasil:" .. hasil)
end

tambahDua(200)
```

```lua
--function yang mengembalikan/menghasilkan nilai
function tambahDua(angka)
  return angka + 2
end

local hasil = tambahDua(100)
print(hasil)

--memanggil function tapi kali ini dengan variabel
local angka1 = 130
local angka2 = 110

local tambahAngka1 = tambahDua(angka1) --132
local tambahAngka2 = tambahDua(angka2) --112

print("hasil angka1 = " .. tambahAngka1) 
print("hasil angka2 = " .. tambahAngka2) 
```

```lua
--parameter lebih dari satu
function tampilkanInfo(nama, umur, negara)
  print(nama .. " berumur " .. umur .. " tahun dan berasal dari " .. negara)
end

tampilkanInfo("Irfan", 12, "Indonesia")
```

## Scope
Variabel memiliki lingkup/scope yang berbeda. Dengan keyword local, variabel tidak bisa diakses di luar scope nya
```lua
function foo()
  local a = 10
end

print(a) --nil
```

```lua
local nyala = true
if nyala then
  local a = 10
end

print(a) --nil
```

**Variabel Global**
```lua
local _G.nilaiSaya = 69
--Melakukan seperti ini terkadang bukan hal yang baik
```

## Perulangan (Loop)
Ada banyak cara kita melakukan loop/perulangan di Lua
```lua
--while loop
local i = 0
local count = 0

while i <= 10 do
  count = count + 1
end

print("count berjumlah " .. count) --count berjumlah 7


--for loop
count = 0
for i=1, 5 do
  count = count + 1
end
print("count berjumlah " .. count)

```

**Infinite Loops**
```lua
--infinite loop tidak akan berakhir
local i = 0
while i >= 0 do
 i = i + 1
 print(i)
end
```

**Nested Loops (Loop bercabang)**
```lua
local count = 0
for a=1, 10 do
  for b=1, 10 do
    count = count + 1
  end
end
print(count) -- 100
```


## Table
```lua
--Dasar table
local warna = { "merah", "hijau", "biru" }

print(warna[1]) --merah
print(warna[2]) --hijau
print(warna[3]) --biru

--menggunakan loop untuk melakukan iterasi terhadap table
for i=1, #warna do
  print(warna[i])
end
```

**Manipulasi Table**
```lua
--insert
local warna = { "merah", "hijau", "biru" }
table.insert(warna, "jingga")
local index = #warna --4 (ini adalah index terakhir pada table, atau jumlah keseluruhan index pada table)
print(colors[index]) --jingga
```

```lua
--insert pada index tertentu
local warna = { "merah", "hijau", "biru" }
table.insert(warna, 2, "pink")
for i=1, #warna do
  print(warna[i])
end
--merah, pink, hijau, biru
```

```lua
--remove 
local warna = { "merah", "hijau", "biru" }
table.remove(warna, 1)
for i=1, #warna do
  print(warna[i])
end
-- "hijau", "biru"
```


**Table dua dimensi**
```lua
--table di dalam table
local data = {
  { "irfan", 12 },
  { "roni", 20 },
  { "andy", 65 }
}

for a=1, #data do
  print(data[a][1] .. " berumur " .. data[a][2] .. " tahun")
end
```


**Key pada table**

```lua
local tim = {
    ["timA"] = 12,
    ["timB"] = 15
}

print(tim["timA"]) -- 12

for key,value in pairs(tim) do
  print(key .. ":" .. value)
end
```

```lua
--memasukkan key baru ke dalam table
tim["timC"] = 1
```

```lua
--menghapus key dari table
tim["timA"] = nil
```


**Me-return table dari function**

Hal ini bisa digunakan untuk me-return nilai yang banyak (lebih dari satu)
```lua
function dapatkanSkorTim()
  local skor = {
    ["timA"] = 12,
    ["timB"] = 15
  }
  return skor
end

local skor = dapatkanSkorTim()
local total = 0
for key, val in pairs(skor) do
  total += val
end
print("Total skor dari semua tim adalah:" .. total)
```


## Math
Kelas math memiliki berbagai macam function yang bisa kamu gunakan untuk bermain dengan angka. Mungkin ini tidak terlalu penting, tapi ini dia daftar function nya:

Lebih banyak: [Wiki](http://lua-users.org/wiki/MathLibraryTutorial)

* abs (nilai absolut)
  ```lua
  local x = -10
  print(math.abs(x)) --hasil: 10
  local a = 10
  print(math.abs(a)) --hasil: 10
  ```
* ceil (membulatkan ke angka tertinggi)
  ```lua
  local x = 1.2
  print(math.ceil(x)) --hasil: 2
  ```
* deg (mengubah dari radian ke derajat)
  ```lua
  print(math.deg(math.pi)) -- hasil: 180
  ```
* floor (membulatkan ke angka terendah)
  ```lua
  local x = 1.2
  print(math.floor(x)) --hasil: 1
  ```
* pi (nilai konstan dari phi)
  ```lua
  print(math.pi) --3.1415926535898
  3.1415926535898
  ```
* rad (mengubah dari derajat ke radian)
  ```lua
  print(math.rad(180)) --hasil: 3.1415926535898
  ```
* random (menghasilkan angka random (acak))
  ```lua
  --angka random dari 0 - 1
  print(math.random()) --hasil: 0.0012512588885159

  --angka random dari 1 - 100
  print(math.random(100)) --hasil: 20

  --angka random dari 20 - 100
  print(math.random(20, 100)) --hasil: 54
  ```
* sqrt (Akar dari sebuah bilangan)
  ```lua
  print(math.sqrt(100)) --hasil: 10
  ```

## Modul

Memasukkan/mengimpor kode dari file lain
```lua
require("filelain")
```
