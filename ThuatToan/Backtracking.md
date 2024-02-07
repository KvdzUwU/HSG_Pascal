# Xâu Nhị Phân Độ Dài N
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

int n, a[105];

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
		    } else {
			      Try(i + 1);
		    }
	  }
}

int main() {
	  cin >> n;
	  Try(1);
	  return 0;
}
```
# Xâu Nhị Phân Độ Dài N Có Dãy K Bit Liên Tiếp
Input
```
5 3
```
Output
```
00111
01110
10111
11100
11101
```
## Pascal
```pascal
program Binary2;
uses crt;
type int = longint;
var n, k : int;
a : array of int;
procedure print;
var i, m, d : int;
begin
  m := 0; d := 0;
  for i := 1 to n do
    if a[i] = 1 then
      inc(d)
    else
    begin
      if d > m then
        m := d;
      d := 0;
    end;
    if d > m then
      m := d;
    if m <> k then exit;
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
    readln(n, k);
    setlength(a, n + 1);
    try(1);
  readln;
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n, k, a[105];

void print() {
	int m = 0, d = 0;
	for (int i = 1; i <= n; i++) {
		if (a[i]) {
			d++;
		} else {
			m = max(m, d);
			d = 0;
		}
	}
	m = max(m, d);
	if (m != k) {
		return ;
	}
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
		} else {
			Try(i + 1);
		}
	}
}

int main() {
	cin >> n >> k;
	Try(1);
	return 0;
}
```
# Tổ Hợp Chập K Của N
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

int n, k, a[105];

void print() {
	for (int i = 1; i <= k; i++) {
		cout << a[i] << ' ';
	}
	cout << '\n';
}

void Try(int i) {
	for (int j = a[i - 1] + 1; j <= n - k + i; j++) {
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
	a[0] = 0;
	Try(1);
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

int n, a[105], b[105];

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
            } else {
                Try(i + 1);
            }
            b[j] = 0;
        }
    }
}
 
int main() {
    cin >> n;
    Try(1);
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
# Tạo Xâu Độ Dài N Từ 3 Kí Tự A, B, C
Input
```
3
```
Output
```
ABC
ACB
BAC
BCA
CAB
CBA
```
## Pascal
```pascal
program ABC;
uses crt;
var n : longint;
procedure try(s : string);
var c : char;
begin
  if length(s) < n then
    for c := 'A' to 'C' do
      try(s + c)
  else if (pos('A', s) <> 0) and (pos('B', s) <> 0) and (pos('C', s) <> 0) then
    writeln(s); 
end;
begin
  clrscr;
    readln(n);
    try('');
  readln;
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n;

void Try(string s) {
	if (s.size() == n) {
		if (s.find('A') != string::npos && s.find('B') != string::npos && s.find('C') != string::npos) {
			cout << s << '\n';
		}
	} else {
		for (char c = 'A'; c <= 'C'; c++) {
			Try(s + c);
		}
	}
}

int main() {
	cin >> n;
	Try("");
	return 0;
}
```
# Phân Tích N Thành Dãy K Phần Tử
Input
```
10 3
```
Output
```
1 2 7
1 3 6
1 4 5
2 3 5
```
## Pascal
```pascal
program PhanTichN;
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
  for j := a[i - 1] + 1 to n - k + i do
  begin
    a[i] := j;
    n := n - a[i];
    if i = k then
    begin
      if n = 0 then
        print;
    end
      else if n > a[i] then
        try(i + 1);
    n := n + a[i];
  end;
end;
begin
  clrscr;
    readln(n, k);
    setlength(a, n + 1);
    a[0] := 0;
    try(1);
  readln;
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n, k, a[105];

void print() {
	for (int i = 1; i <= k; i++) {
		cout << a[i] << ' ';
	}
	cout << '\n';
}

void Try(int i) {
	for (int j = a[i - 1] + 1; j <= n - k + i; j++) {
		a[i] = j;
		n -= a[i];
		if (i == k) {
			if (n == 0) {
			print();
			}
		} else if (n > a[i]) { 
			Try(i + 1);
		}
		n += a[i];
	}
}

int main() {
	cin >> n >> k;
	a[0] = 0;
	Try(1);
	return 0;
}
```
# Chia M Phần Thưởng Cho N Học Sinh
Input
```
5 3
```
Output
```
5 0 0
4 1 0
3 2 0
3 1 1
2 2 1
```
## Pascal
```pascal
program ChiaThuong;
uses crt;
type int = longint;
var m, n : int;
a : array of int;
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
  for j := a[i - 1] downto 1 do
  begin
    a[i] := j;
    m := m - a[i];
    if m = 0 then
      print
    else if (i < n) and (m > 0) then
      try(i + 1);
    m := m + a[i];
  end;
end;
begin
  clrscr;
    readln(m, n);
    setlength(a, n + 1); 
    a[0] := m;
    try(1);
  readln;
end.
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int m, n;
vector<int> a(105, 0);

void print() {
	for (int i = 1; i <= n; i++ ) {
		cout << a[i] << ' ';
	}	
	cout << '\n';
}

void Try(int i) {
	for (int j = a[i - 1]; j > m / n; j--) {
		a[i] = j;
		m -= a[i];
		if (m == 0) {
			print();
		} else if (m > 0 && i < n) {
			Try(i + 1);
		}
		m += a[i];
	}
}

int main() {
	cin >> m >> n;
	a[0] = m;
	Try(1);
	return 0;
}
```
# Tìm Đường Đi Có Tổng Lớn Nhất Trong Tam Giác
Input
```
5
7
3 8
8 1 0
2 7 4 4
4 5 2 6 5
```
Output
```
30
7 3 8 7 5
```
## Pascal
```pascal
```
## C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int n, m = INT_MIN, cmax = INT_MIN, sum = 0, a[105][105], b[105], luu[105];

void Nhap() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL); cout.tie(NULL);
    cin >> n;
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= i; j++) {
            cin >> a[i][j];
            cmax = max(cmax, a[i][j]);
        }
    }
}

void copyArr(int *a, int *b, int s) {
    copy(b, b + s, a);
}

void Try(int i, int k) {
    for (int j = k; j <= k + 1; j++) {
        b[i] = a[i][j];
        sum += b[i];
        if (i == n) {
            if (m < sum) {
                m = sum;
                copyArr(luu, b, n + 1);
            }
        } else if (sum + a[i + 1][j] + (n - i - 1) * cmax >= m) {
            Try(i + 1, j);
        }
        sum -= b[i];
    }
}

int main() {
    Nhap();
    Try(1, 1);
    cout << m << '\n';
    for (int i = 1; i <= n; i++) {
        cout << luu[i] << ' ';
    }
    return 0;
}
```
# Người Du Lịch