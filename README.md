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
-- Tipe yang berbeda
local x = 10 --number
local name = "john doe" --string
local isAlive = false -- boolean
local a = nil --Tidak ada nilai 
```

**Number**

operator
- \+ pertambahan
- \- pengurangan
- \* perkalian
- / pembagian
- ^ perpangkatan
- % modulus

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
local phrase = "My name is "
local name = "John Doe"
print(phase .. name) --My name is John Doe

-- string dan number
local age = 12
local name = "Billy"
print(name .. " is " .. age .. " years old")
````

**Boolean**
```lua
local isAlive = true
print(isAlive) --true
isAlive = false
print(isAlive) --false
```

## Pengkondisian
```lua
--Membandingkan angka
local age = 10
if age < 18 then
  print("over 18") --tidak akan dieksekusi
end

--elseif dan else
age = 20
if age > 18 then
  print("dog")
elseif age == 18 then
  print("cat")
else
  print("mouse")
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
local isAlive = true
if isAlive then
    print("dog")
end

--perbandingan string
local name = "billy"
if name == "Billy" then --false
  print("Billy")
elseif name == "billy" then --true
  print("billy")
end

```

**Kombinasi Statement**
```lua
local x = 10
if x == 10 and x < 0 then --keduanya bernilai true
  print("dog")
elseif x == 100 or x < 0 then --satu atau lebih bernilai true
  print("cat")
end
--hasil: cat
```

**Statement bercabang**

```lua
local x = 10
local isAlive = true
if x==10 then
  if isAlive == true then
    print("dog")
  else
    print("cat")
  end
end
```
**Membalikkan Nilai**

Kita juga bisa membalikkan nilai dengan kata kunci **not**
```lua
local x = 10
if not x == 10 then
  print("here")
end
```

## Function
```lua
function printTax(price)
  local tax = price * 0.21
  print("tax:" .. tax)
end

printTax(200)
```

```lua
--function yang mengembalikan/menghasilkan nilai
function calculateTax(price)
  return price * 0.21
end

local result = calculateTax(100)
print(result)

--memanggil function tapi kali ini dengan variabel
local bread = 130
local milk = 110

local breadTax = calculateTax(bread) --27.3
local milkTax = calculateTax(milk) --23.1

print("Bread Tax = " .. breadTax) 
print("Milk Tax = " .. milkTax) 
```

```lua
--parameter lebih dari satu
function displayInfo(name, age, country)
  print(name .. " is " .. age .. " years old and is from " .. country)
end

displayInfo("Billy", 12, "Jupiter")
```

## Scope
Variabel memiliki lingkup/scope yang berbeda. Jika sudah sampai pada akhir scope, variabel tidak dpaat diakses lagi
```lua
function foo()
  local a = 10
end

print(a) --nil
```

```lua
local isAlive = true
if isAlive then
  local a = 10
end

print(a) --nil
```

**Variabel Global**
```lua
local _G.myValue = 69
--Melakukan seperti ini terkadang bukan hal yang baik
```

## Perulangan
There is a few different ways you can do a loop in lua
```lua
--while loop
local i = 0
local count = 0

while i <= 10 do
  count = count + 1
end

print("count is " .. count) --count is 7


--for loop
count = 0
for i=1, 5 do
  count = count + 1
end
print("count is " .. count)

```

**Infinite Loops**
```lua
--infinite loop will never end
local i = 0
while i >= 0 do
 i = i + 1
 print(i)
end
```

**Nested Loops**
```lua
local count = 0
for a=1, 10 do
  for b=1, 10 do
    count = count + 1
  end
end
print(count) -- 100
```


## Tables
```lua
--basic table
local colors = { "red", "green", "blue" }

print(colors[1]) --red
print(colors[2]) --green
print(colors[3]) --blue

--using a loop to iterate though your table
for i=1, #colors do
  print(colors[i])
end
```

**Table Manipulation**
```lua
--insert
local colors = { "red", "green", "blue" }
table.insert(colors, "orange")
local index = #colors --4 (this is the last index in the table)
print(colors[index]) --orange
```

```lua
--insert at index
local colors = { "red", "green", "blue" }
table.insert(colors, 2, "pink")
for i=1, #colors do
  print(colors[i])
end
--red, pink, green, blue
```

```lua
--remove 
local colors = { "red", "green", "blue" }
table.remove(colors, 1)
for i=1, #colors do
  print(colors[i])
end
-- "green", "blue"
```


**2 Dimensional Table**
```lua
--tables within tables
local data = {
  { "billy", 12 },
  { "john", 20 },
  { "andy", 65 }
}

for a=1, #data do
  print(data[a][1] .. " is " .. data[a][2] .. " years old")
end
```


**Key Tables**

2 dimensional tables are not suited to data with different types, instead uses keys for tables
```lua
local teams = {
    ["teamA"] = 12,
    ["teamB"] = 15
}

print(teams["teamA"]) -- 12

for key,value in pairs(teams) do
  print(key .. ":" .. value)
end
```

```lua
--insert into key table
teams["teamC"] = 1
```

```lua
--remove key from table
teams["teamA"] = nil
```


**Returning a Table from a Function**

This can be used to return multiple values from a functions
```lua
function getTeamScores()
  local scores = {
    ["teamA"] = 12,
    ["teamB"] = 15
  }
  return scores
end

local scores = getTeamScores()
local total = 0
for key, val in pairs(scores) do
  total += val
end
print("Total score of all teams:" .. total)
```


## Math
The math class has a number of functions for dealing with numbers. You may not need them but here is some of the more useful one functions:

More: [Wiki](http://lua-users.org/wiki/MathLibraryTutorial)

* abs (absolute value)
  ```lua
  local x = -10
  print(math.abs(x)) --result: 10
  local a = 10
  print(math.abs(a)) --result: 10
  ```
* ceil (round up decimal value)
  ```lua
  local x = 1.2
  print(math.ceil(x)) --result: 2
  ```
* deg (Convert value from radians to degrees)
  ```lua
  print(math.deg(math.pi)) -- result: 180
  ```
* floor (round down decimal value)
  ```lua
  local x = 1.2
  print(math.floor(x)) --result: 1
  ```
* pi (constant value of pi)
  ```lua
  print(math.pi) --3.1415926535898
  3.1415926535898
  ```
* rad (Convert value from degrees to radians)
  ```lua
  print(math.rad(180)) --result: 3.1415926535898
  ```
* random (random number generation)
  ```lua
  --random value between 0 tand 1
  print(math.random()) --result: 0.0012512588885159

  --random integer value from 1 to 100 (both inclusive)
  print(math.random(100)) --result: 20

  --random integer value from 20 to 100 (both inclusive)
  print(math.random(20, 100)) --result: 54
  ```
* sqrt (Square root of a number)
  ```lua
  print(math.sqrt(100)) --result: 10
  ```

## Modules

Include code other files
```lua
require("otherfile")
```
