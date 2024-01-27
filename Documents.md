# Function
Một số hàm thông dụng (Ngôn ngữ Pascal)
## Check Prime
```pascal
function Ngto(n : longint):boolean;
var i : longint;
begin
  ngto := n > 1;
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then exit(false);
end;
```
