# Function & Procedure
Một số hàm thông dụng (Ngôn ngữ Pascal)

## Toán (Int, Double)
### Kiểm Tra Số Nguyên Tố O(sqrt(n))
```pas
function Prime(n : qword):boolean;
var i : longint;
begin
  Prime := n > 1;
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then
      exit(false);
end;
```
### Kiểm Tra Số Chính Phương O(1)
```pas
function check(n : qword):boolean;
var a : longint;
begin
  a := trunc(sqrt(n));
  check := a = sqrt(n);
end;
```
### Kiểm Tra Số Hoàn Thiện O(sqrt(n))
```pas
function check(n : qword):boolean;
var i : longint;
sum : qword;
begin
  if n < 2 then exit(false);
  sum := 1;
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then
    begin
      sum := sum + i;
      if n div i <> i then
        sum := sum + n div i;
    end;
  check := sum = n;
end;
```
### Đệ Qui Tính A ^ B O(logb)
```pas
function pow(a, b : longint):qword;
begin
  if b = 0 then
    exit(1);
  if odd(b) then
    exit(a * sqr(pow(a, (b - 1) div 2)));
  exit(sqr(pow(a, b div 2)));
end;
```
### Luỹ Thừa Nhanh Tính A ^ B Mod C O(logb)
```pas
function mulmod(a, b, c : qword):qword;
begin
  mulmod := 0;
  while b > 0 do
  begin
    if odd(b) then
      mulmod := (mulmod + a) mod c;
    a := (a * 2) mod c;
    b := b div 2;
  end;
end;
function powMod(a, b, c : qword):qword;
begin
  a := a mod c;
  if a = 0 then
    exit(0);
  powMod := 1;
  if Prime(c) then
    b := b mod (c - 1);
  while b > 0 do
  begin
    if odd(b) then
      powMod := mulmod(powMod, a, c);
    a := mulmod(a, a, c);
    b := b div 2;
  end;
end;
```
## Mảng (Array)
### Nhập / Xuất Mảng
Nhập vào n phần tử của mảng A
```pas
procedure readArr(var a : array of longint; n : longint);
var i : longint;
begin
  for i := 0 to n - 1 do
    read(a[i]);
  readln;
end;
```
Xuất ra n phần tử của mảng A
```pas
procedure printArr(a : array of longint; n : longint);
var i : longint;
begin
  for i := 0 to n - 1 do
    write(a[i],' ');
  writeln;
end;
```
### Đảo Giá Trị Của 2 Biến
Có thể thay kiểu dữ liệu longint thành char để đảo kí tự
```pas
procedure swap(var a, b : longint);
var t : longint;
begin
  t := a;
  a := b;
  b := t;
end;
```
### Sắp Xếp Mảng
Note: Dùng kèm hàm swap ở trên
#### Bubble Sort
Sắp xếp nổi bọt (Tốt nhất: O(n) trung bình-xấu: O(n ^ 2))
```pas
procedure bubbleSort(var a : array of longint; n : longint);
var i, j : longint;
swapped : boolean;
begin
  for i := 0 to n - 2 do
  begin
    swapped := false;
    for j := 0 to n - i - 2 do
      if a[j] > a[j + 1] then
      begin
        swap(a[j], a[j + 1]);
        swapped := true;
      end;
    if not swapped then
      exit;
  end;
end;
```
#### Insertion Sort Sắp Xếp Chèn O(n * 2)
Ưu điểm: không dùng đến swap để hoán đổi vị trí
```pas
procedure insertionSort(var a : array of longint; n : longint);
var i, j, key : longint;
begin
  for i := 1 to n - 1 do
  begin
    key := a[i];
    j := i - 1;
    while (j >= 0) and (a[j] > key) do
    begin
      a[j + 1] := a[j];
      dec(j);
    end;
    a[j + 1] := key;
  end;
end;
```
#### Quick Sort Sắp Xếp Nhanh O(nlog(n))
```pas
function part(var a : array of longint; l, r : longint):longint;
var i, j, pivot : longint;
begin
  pivot := a[r];
  i := l;
  for j := l to r do
    if a[j] < pivot then
    begin
      swap(a[i], a[j]);
      inc(i);
    end;
  swap(a[i], a[j]);
  exit(i);
end;
procedure quickSort(var a : array of longint; l, r : longint);
var pi : longint;
begin
  if l >= r then exit;
  pi := part(a, l, r);
  quickSort(a, l, pi - 1); 
  quickSort(a, pi + 1, r);
end;
```
### Tìm Kiếm X Trong Mảng
Trả về -1 nếu không có xuất hiện, trả về vị trí nếu có
#### Binary Search (Tìm kiếm nhị phân) O(logn)
Note: Dùng cùng mảng đã sắp xếp tăng dần
```pas
function binarySearch(a : array of longint; l, r, x : longint):longint;
var mid : longint;
begin
  while l <= r do
  begin
    mid := l + (r - l) div 2;
    if a[mid] = x then
      exit(mid);
    if a[mid] < x then
      l := mid + 1
    else
      r := mid - 1;
  end;
  exit(-1);
end;
```
#### Linear Search (Tìm Kiếm Thông Thường) O(n)
```pas
function Search(a : array of longint; n, x : longint):longint;
var i : longint;
begin
  for i := 0 to n - 1 do
    if a[i] = x then
      exit(i);
  exit(-1);
end;
```
## Xâu Kí Tự (String)
### Kiểm Tra Xâu Đối Xứng
Ví dụ: '12321'
```pas
function check(st : string):boolean;
var i : longint;
begin
  check := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) - i + 1] then
      exit(false);
end;
```
### Kiểm Tra Xâu Lặp Lại
Ví dụ: 'ABCABC'
```pas
function check(st : string):boolean;
var i : longint;
begin
  check := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) div 2 + i] then
      exit(false);
end;
```
### Hoán vị Xâu
Hoán vị một xâu theo đoạn mã n phần tử là các vị trí mới (2023 AG)
```pas
function hv(st : string; a : array of longint; n : longint):string;
var i : longint;
begin
  hv := '';
  for i := 0 to n - 1 do
    hv := hv + st[a[i]];
end;
```
