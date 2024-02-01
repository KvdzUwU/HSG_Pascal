# Câu 1 Tin Học Trẻ 2018 AG
![](./De/THT/2018/1.png)
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
```cpp
#include<bits/stdc++.h>
using namespace std;

int n, k;
int a[101];

void print() {
    for (int i = 1; i <= k; i++)
        cout << a[i] << ' ';
    cout << '\n';
}

void tryFunc(int i) {
    for (int j = a[i - 1] + 1; j <= n - k + i; j++) {
        a[i] = j;
        n -= j;
        if (i < k)
            tryFunc(i + 1);
        else if (n == 0)
            print();
        n += j;
    }
}

int main() {
    ios_base::sync_with_stdio(0);
    cin.tie(0);  cout.tie(0);
    freopen("Cau1.inp", "r", stdin);
    freopen("Cau1.out", "w", stdout);
    cin >> n >> k;
    a[0] = 0;
    tryFunc(1);
    return 0;
}
```
# Câu 2 Tin Học Trẻ 2018 AG
![](./De/THT/2018/2.png)
## Pascal
```pas
program Cau2;
type int = integer;
var m, n : int;
a : array[0..100] of int;
procedure print;
var i : int;
begin
  for i := 1 to n do
    write(a[i],' ');
  writeln;
end;
procedure try(i : int);
var j : int;
begin
  for j := a[i - 1] downto 0 do
  begin
    a[i] := j;
    m := m - j;
    if (i < n) then
      try(i + 1)
    else if m = 0 then print;
    m := m + j;
  end;
end;
begin
  assign(input, 'Cau2.inp'); reset(input);
  assign(output, 'Cau2.out'); rewrite(output);
  readln(m, n);
  a[0] := m;
  try(1);
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int m, n;
int a[101];

void print() {
    for (int i = 1; i <= n; i++)
        cout << a[i] << ' ';
    cout << '\n';
}

void tryFunc(int i) {
    for (int j = a[i - 1]; j >= 0; j--) {
        a[i] = j;
        m -= j;
        if (i < n)
            tryFunc(i + 1);
        else if (m == 0)
            print();
        m += j;
    }
}

int main() {
    ios_base::sync_with_stdio(0);
    cin.tie(0);  cout.tie(0);
    freopen("Cau2.inp", "r", stdin);
    freopen("Cau2.out", "w", stdout);
    cin >> m >> n;
    a[0] = m;
    tryFunc(1);
    return 0;
}
```
# Câu 3 Tin Học Trẻ 2018 AG
![](./De/THT/2018/3.png)
Sàng SNT Đến 10^7 (1e7 + 1)
## Pascal
```pas
program Cau3;
uses crt;
const maxn = 10000000;
var i, m, n : longint;
p : array[0..maxn] of boolean;
procedure sang;
var i, j : longint;
begin
  fillchar(p, sizeof(p), true);
  p[0] := false; p[1] := false;
  for i := 2 to trunc(sqrt(maxn)) do
    if p[i] then
    begin
      j := i * i;
      while j <= maxn do
      begin
        p[j] := false;
        j := j + i;
      end;
    end;
end;
begin
  sang;
  assign(input, 'Cau3.inp'); reset(input);
  assign(output, 'Cau3.out'); rewrite(output);
  readln(m, n);
  for i := m to n - 2 do
    if p[i] and p[i + 2] then
      writeln(i,' ',i + 2);
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

const int maxn = 1e7 + 1;
int p[maxn];
int m, n;

void sang() {
    fill_n(p, size(p), 1);
    p[0] = p[1] = 0;
    for (int i = 2; i * i <= maxn; i++) 
        if (p[i])
            for (int j = i * i; j <= maxn; j += i)
                p[j] = 0;
}

int main() {
    ios_base::sync_with_stdio(0);
    cin.tie(0);  cout.tie(0);
    sang();
    freopen("Cau3.inp", "r", stdin);
    freopen("Cau3.out", "w", stdout);
    cin >> m >> n;
    for (int i = m; i <= n - 2; i++)
        if (p[i] && p[i + 2])
            cout << i << ' ' << i + 2 << '\n';
    return 0;
}
```
# Bài 1 Tin Học Trẻ 2021 AG
![](./De/THT/2021/1.png)
## Pascal
```pas
program Bai;
type
  int = longint;
  Arr2C = array[1..50, 1..50] of int;
  arr = array[1..50] of int;
var n, sum, max : int;
a : Arr2C;
b, luu : arr;
procedure readArr(var a : Arr2C; n : int);
var i, j : int;
begin
  for i := 1 to n do
    for j := 1 to i do
      read(a[i, j]);
  readln;
end;
procedure writeArr(a : arr; n : int);
var i : int;
begin
  for i := 1 to n do
    write(a[i],' ');
  writeln;
end;
procedure try(i, k : int);
var j : int;
begin
  for j := k to k + 1 do
  begin
    sum := sum + a[i, j];
    b[i] := a[i, j];
    if i < n then
      try(i + 1, j)
    else
      if max < sum then
      begin
        max := sum;
        luu := b;
      end;
    sum := sum - a[i, j];
  end;
end;
begin
  assign(input, 'Bai01.inp'); reset(input);
  assign(output, 'Bai01.out'); rewrite(output);
  readln(n);
  readArr(a, n);
  max := -maxlongint;
  sum := 0;
  try(1, 1);
  writeln(max);
  writeArr(luu, n);
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n, m = INT_MIN, sum = 0;
int a[50][50], b[50], luu[50];

void readArr(int a[50][50], int n) {
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= i; j++)
            cin >> a[i][j];
}

void writeArr(int a[50], int n) {
    for (int i = 1; i <= n; i++)
        cout << a[i] << ' ';
    cout << '\n';
}

void copyArr(int a[], int b[], int s) {
    copy(b, b + s, a);
}

void tryFunc(int i, int k) {
    for (int j = k; j <= k + 1; j++) {
        sum += a[i][j];
        b[i] = a[i][j];
        if (i < n)
            tryFunc(i + 1, j);
        else
            if (m < sum) {
                m = sum;
                copyArr(luu, b, n + 1);
            }
        sum -= a[i][j];
    }
}

int main() {
    ios_base::sync_with_stdio(0);
    cin.tie(0);  cout.tie(0);
    freopen("Bai01.inp", "r", stdin);
    freopen("Bai01.out", "w", stdout);
    cin >> n;
    readArr(a, n);
    tryFunc(1, 1);
    cout << m << '\n';
    writeArr(luu, n);
}
```
