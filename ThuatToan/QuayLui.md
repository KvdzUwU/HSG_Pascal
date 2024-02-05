# Chuỗi Nhị Phân Độ Dài N
Input
```
3
```
Output
```
000
001
010
011
100
101
110
111
```
## Pascal
```pascal
program Binary;
uses crt;
type int = longint;
var n : int;
a : array of int;
procedure print;
var i : int;
begin
  for i := 1 to n do
    write(a[i]);
  writeln;
end;
procedure try(i : int);
var j : int;
begin
  for j := 0 to 1 do
  begin
    a[i] := j;
    if i = n then
      print
    else try(i + 1); 
  end;
end;
begin
  clrscr;
    readln(n);
    setlength(a, n + 1);
    try(1);
  readln;
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n, *a;

void print() {
    for (int i = 1; i <= n; i++) {
        cout << a[i];
    }
    cout << '\n';
}

void Try(int i) {
    for (int j = 0; j <= 1; j++) {
        a[i] = j;
        if (i == n) {
            print();
        } else Try(i + 1);
    }
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL); cout.tie(NULL);
    cin >> n;
    a = new int[n + 1];
    Try(1);
    delete[] a;
    return 0;
}
```
# Tập Con K Phần Tử
Input
```
5 3
```
Output
```
1 2 3
1 2 4
1 2 5
1 3 4
1 4 5
2 3 4
2 3 5
2 4 5
3 4 5
```
## Pascal
```pascal
program Taphop;
uses crt;
type int = longint;
var n, k : int;
a : array of int;
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
  for j := a[i - 1] + 1 to n do
  begin
    a[i] := j;
    if i = k then
      print
    else try(i + 1);
  end;
end;
begin
  clrscr;
    readln(n, k);
    setlength(a, k + 1);
    a[0] := 0;
    try(1);
  readln;
end.

```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n, k;
int *a;

void print() {
    for (int i = 1; i <= k; i++) {
        cout << a[i] << ' ';
    }
    cout << '\n';
}w 

void Try(int i) {
    for (int j = a[i - 1] + 1; j <= n; j++) {
        a[i] = j;
        if (i == k) {
            print();
        } else {
            Try(i + 1);
        }
    }
}

int main() {
    cin >> n >> k;
    a = new int[k + 1];
    a[0] = 0;
    Try(1);
    delete[] a;
    return 0;
}
```
# Hoán Vị Dãy
Input
```
3
```
Output
```
1 2 3
1 3 2
2 1 3
2 3 1
3 1 2
3 2 1
```
## Pascal
```pascal
program HoanVi;
uses crt;
type int = longint;
var n : int;
a, b : array of int;
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
  for j := 1 to n do
    if b[j] = 0 then
    begin
      a[i] := j;
      b[j] := 1;
      if i = n then
        print
      else try(i + 1);
      b[j] := 0;
    end;
end;
begin
  clrscr;
    readln(n);
    setlength(a, n + 1);
    setlength(b, n + 1);
    try(1);
  readln;
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n, *a, *b;

void print() {
    for (int i = 1; i <= n; i++) {
        cout << a[i] << ' ';
    }
    cout << '\n';
}

void Try(int i) {
    for (int j = 1; j <= n; j++) {
        if (!b[j]) {
            a[i] = j;
            b[j] = 1;
            if (i == n) {
                print();
            } else Try(i + 1);
            b[j] = 0;
        }
    }
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL); cout.tie(NULL);
    cin >> n;
    a = new int[n + 1];
    b = new int[n + 1];
    Try(1);
    delete[] a;
    delete[] b;
    return 0;
}
```
# Số Siêu Nguyên Tố Độ Dài N
Input
```
5
```
Ouput
```
15
23333 23339 23399 23993 29399 31193 31379 37337 37339 37397 59393 59399 71933 73331 73939
```
## Pascal
```pascal
program SuperPrime;
uses crt;
type int = longint;
var i, n, d : int;
nt : qword;
a : array[1..25] of int;
x1 : array[1..4] of int = (2, 3, 5, 7);
x2 : array[1..4] of int = (1, 3, 7, 9);
function prime(n : qword):boolean;
var i : int;
begin
  if n < 2 then
    exit(false);
  for i := 2 to trunc(sqrt(n)) do
    if n mod i = 0 then
      exit(false);
  exit(true); 
end;
procedure try(i : int);
var j : int;
begin
  for j := 1 to 4 do
  begin
    nt := nt * 10 + x2[j];
    if prime(nt) then
      if i = n then
      begin
        inc(d);
        a[d] := nt;
      end
        else try(i + 1);
      nt := nt div 10;
  end;
end;
begin
  clrscr;
    readln(n);
    if n = 1 then
    begin
      for i := 2 to 9 do
        if prime(i) then
        begin
          inc(d);
          a[d] := i;
        end;
    end
    else
      for i := 1 to 4 do
      begin
        nt := x1[i];
        try(2);
      end;
    writeln(d);
    for i := 1 to d do
      write(a[i],' ');
  readln;
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
int n, d = 0, luu[25], x1[4] = {2, 3, 5, 7}, x2[4] = {1 , 3, 7, 9};
ll nt;

int Prime(ll n) {
    for (ll i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            return 0;
        }
    }
    return n > 1;
}

void Try(int i) {
    for (int j = 0; j < 4; j++) {
        nt = nt * 10 + x2[j];
        if (Prime(nt)) {
            if (i == n) {
                luu[d] = nt;
                d++;
            } else Try(i + 1);
        }
        nt /= 10;
    }
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL); cout.tie(NULL);
    cin >> n;
    if (n == 1) {
        for (int i = 2; i < 10; i++) {
            if (Prime(i)) {
                luu[d] = i;
                d++;
            }
        }
    } else {
        for (int i = 0; i < 4; i++) {
            nt = x1[i];
            Try(2);
        }
    }
    cout << d << '\n';
    for (int i = 0; i < d; i++) {
        cout << luu[i] << ' ';
    }
    return 0;
}
```