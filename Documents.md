# Function
Một số hàm thông dụng (Ngôn ngữ Pascal)
## Check Prime
```pascal
function Ngto(n : longint):boolean;
var i : longint;
begin
  ngto := n > 1;
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then
      exit(false);
end;
```
## Xâu đối xứng
```pascal
function dx(st : string):boolean;
var i : longint;
begin
  dx := true;
  for i := 1 to length(st) div 2 do
    if st[i] <> st[length(st) - i + 1] then
      exit(false);
end;
```
