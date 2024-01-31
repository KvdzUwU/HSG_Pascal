# Câu 1 Tin Học Trẻ 2018 AG
![](./De/2018_1.png)
## Pascal
```pas
program Cau1;
type int = integer;
var n, k : int;
a : array[0..100] of int;
procedure print;
var i : int;
begin
  for i := 1 to k do
    write(a[i],' ');
  writeln;
end;
procedure try(i : int);
var j : int;
begin
  for j := a[i - 1] + 1 to n - k + i do
  begin
    a[i] := j;
    n := n - j;
    if (i < k) then
      try(i + 1)
    else if n = 0 then print;
    n := n + j;
  end;
end;
begin
  assign(input, 'Cau1.inp'); reset(input);
  assign(output, 'Cau1.out'); rewrite(output);
  readln(n, k);
  a[0] := 0;
  try(1);
end.
```
## C++
