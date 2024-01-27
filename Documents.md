# Function
Một số hàm thông dụng (Ngôn ngữ Pascal)

## Kiểm Tra Số Nguyên Tố
```pascal
function ngto(n : longint):boolean;
var i : longint;
begin
  ngto := n > 1;
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then
      exit(false);
end;
ngto(2) -> true
```
## Kiểm Tra Xâu Đối Xứng
```pascal
function dx(st : string):boolean;
var i : longint;
begin
  dx := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) - i + 1] then
      exit(false);
end;
dx('abcba') -> true
```
## Kiểm Tra Xâu Lặp Lại
```pascal
function laplai(st : string):boolean;
var i : longint;
begin
  laplai := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) div + i] then
      exit(false);
end;
laplai('abcabc') -> true
```
## Tìm X Có Xuất Hiện Trong Mảng A Không 
-- Nên dùng cùng mảng đã sắp xếp tăng dần nha
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
