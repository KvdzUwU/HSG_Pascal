# Function & Procedure
Một số hàm thông dụng (Ngôn ngữ Pascal)

## Kiểm Tra Số Nguyên Tố
```pascal
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
```pascal
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
Note: Nên dùng cùng mảng đã sắp xếp tăng dần nha
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
  end;
end;
```
## Đảo Giá Trị Của 2 Số
```pascal
procedure swap(var a, b : longint);
var t : longint;
begin
  t := a;
  a := b;
  b := t;
end;
```
# Sắp Xếp Mảng (Quick Sort)
Dùng kèm hàm swap
```pascal
function part(var a : array of longint; l, r : longint):longint;
var i, j, pivot : longint;
begin
  pivot := a[r];
  i := l - 1;
  for j := l to r do
    if a[j] < pivot then
    begin
      inc(i);
      swap(a[i], a[j]);
    end;
  swap(a[i + 1], a[j]);
  exit(i + 1);
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
