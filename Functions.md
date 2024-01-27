# Function & Procedure
Một số hàm thông dụng (Ngôn ngữ Pascal)

## Toán Tin (int, double)
### Số Nguyên Tố
Ví dụ: 2, 3, 5, 7, 11, 13 ... 
```pas
function Prime(n : qword):boolean;
var i : longint;
begin
  Prime := n > 1;
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then exit(false);
end;
```
### Tính A ^ B (a ^ b <= 10^18)
```pas
function pow(a, b : longint):qword;
begin
  if b = 0 then
    exit(1);
  if odd(b) then
    pow := a * sqr(pow(a, (b - 1) div 2))
  else
    pow := sqr(pow(a, b div 2));
end;
```
### Tính A ^ B Mod C (Luỹ Thừa Nhanh) (a, b, c <= 10^18)
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
  powMod := 1;
  a := a mod c; // Số a mod c trước để giảm độ lớn
  if Prime(c) then
    b := b mod (c - 1); // Mũ b mod (c - 1) nếu c là số nguyên tố
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
#### Nhập
```pas
procedure readArr(var a : array of longint; n : longint);
begin
  for i := 0 to n - 1 do
    read(a[i]);
  readln;
end;
```
#### Xuất
```pas
procedure printArr(a : array of longint; n : longint);
var i : longint;
begin
  for i := 0 to n - 1 do
    write(a[i],' ');
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
#### Bubble Sort (Tốt nhất: O(n) trung bình-xấu: O(n ^ 2))
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
#### Quick Sort (trung bình: O(nlog(n)) xấu: O(n ^ 2))
Đệ quy chia mảng ra từng vùng rồi sắp xếp
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
### Kiểm Tra X Có Xuất Hiện Trong Mảng A Không 
Note: Nên dùng cùng mảng đã sắp xếp tăng dần
```pas
function binarySearch(a : array of longint; l, r, x : longint):boolean;
begin
  if l > r then exit(false);
  mid := l + (r - l) div 2;
  if a[mid] = x then
    exit(true);
  if a[mid] > x then
    exit(binarySearch(a, l, mid - 1, x));
  exit(binarySearch(a, mid + 1, r, x));
end;
```
## Xâu Kí Tự (String)
### Xâu Đối Xứng
Ví dụ: '12321'
```pas
function kt(st : string):boolean;
var i : longint;
begin
  dx := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) - i + 1] then
      exit(false);
end;
```
### Xâu Lặp Lại
Ví dụ: 'ABCABC'
```pas
function kt(st : string):boolean;
var i : longint;
begin
  laplai := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) div 2 + i] then
      exit(false);
end;
```
