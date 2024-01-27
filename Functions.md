# Function & Procedure
Một số hàm thông dụng (Ngôn ngữ Pascal)

## Kiểm Tra Số Nguyên Tố
Ví dụ: 2, 3, 5, 7, 11, 13 ... 
```pas
function Prime(n : longint):boolean;
var i : longint;
begin
  ngto := n > 1;
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then
      exit(false);
end;
```
## Kiểm Tra Xâu Đối Xứng
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
## Kiểm Tra Xâu Lặp Lại
Ví dụ: 'ABCABC'
```pascal
function kt(st : string):boolean;
var i : longint;
begin
  laplai := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) div + i] then
      exit(false);
end;
```
## Tìm X Có Xuất Hiện Trong Mảng A Không 
Note: Nên dùng cùng mảng đã sắp xếp tăng dần
```pascal
function binarySearch(a : array of longint; l, r, x : longint):boolean;
begin
  if r >= l then
  begin
    mid := l + (r - l) div 2;
    if a[mid] = x then
      binarySearch := true
    else if a[mid] > x then
      binarySearch := binarySearch(a, l, mid - 1, x)
    else binarySearch := binarySearch(a, mid + 1, r, x);
  end
  else binarySearch := false;
end;
```
## Đảo Giá Trị Của 2 Biến
Có thể thay kiểu dữ liệu longint thành char để đảo kí tự
```pascal
procedure swap(var a, b : longint);
var t : longint;
begin
  t := a;
  a := b;
  b := t;
end;
```
## Sắp Xếp Mảng
Đệ quy chia mảng ra từng vùng rồi sắp xếp
Note: Dùng kèm hàm swap
# Quick Sort
```pascal
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
