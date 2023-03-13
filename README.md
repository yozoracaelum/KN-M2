# KN-M2

## Bisection
```
procedure BagiDua(a,b: real);
  { 
    Mencari akar f(x)=0 di dalam selang [a,b] dengan metode
    bagidua
    K.Awal : a dan b adalah ujung-ujung selang sehingga
    f(a)*f(b) < 0, nilai a dan b sudah terdefinisi.
    K.Akhir : Hampiran akar tercetak di layar.
  }
const 
  epsilon1 = 0.000001; {batas lebar selang akhir lelaran} 
  epsilon2 = 0.00000001; {bilangan yang sangat kecil, mendekati nol}
begin
  repeat
    c:=(a+b)/2; { titik tengah [a,b]}
    if f(a)*f(c) < 0 then
      b:=c {selang baru [a,b]=[a,c]}
    else 
      a:=c; {selang baru [a,b]=[c,b]}
    until (ABS(a-b)< epsilon1) or (f(c)) < epsilon2);
    { c adalah akar persamaan }
    writeln(‘Hampiran kar = ‘, x:10:6);
end;
```

## Regula-Falsi
```
procedure regula_falsi(a, b: real);
  { 
    mencari akar f(x) = 0 di dalam selang [a,b] dengan metode regulafalsi
    K.Awal : a dan b adalah ujung-ujung selang sehingga f(a)*f(b) < 0,
             harga a dan b sudah terdefinisi
    K.Akhir : Hampiran akar tercetak di layar 
  }
const
  epsilon1 = 0.00001;  {batas lebar selang akhir lelaran}
  epsilon2 = 0.000001;  {bilangan yang sangat kecil, bisa diganti}
begin
  repeat
    c:=b-(f(b)*(b-a)/(f(b)-f(a)));
    if abs(f(c)) < epsilon2 then    {f(c) = 0, c adalah akar}
      begin
        a:=c;
        b:=c;
       end
    else
      if f(a)*f(c) < 0 then
        b:=c;     {selang baru [a,b]=[a,c]}
      else
        a:=c;     {selang baru [a,b]=[c,b]}
   untill abs(a-b) < epsilon1;
   writeln('Hampiran akar : ', c:10:6);
end;
```

## Fixed Point Iteration
```
1. Start
2. Define function as f(x)
3. Define convergent form g(x) 
4. Input:
	a. Initial guess x0 
	b. Tolerable Error e
	c. Maximum Iteration N
5. Initialize iteration counter: step = 1
6. Do 
	x1 = g(x0)
	step = step + 1
	If step > N
		Print "Not Convergent"
		Stop
	End If
	x0 = x1
   While abs f(x1) > e 
7. Print root as x1
8. Stop
Note: g(x) is obtained by rewriting f(x) in the form of x = g(x)
```

## Newton-Raphson
```
procedure Newton_Raphson(x:real);
  { 
    Mencari akar persamaan f(x) = 0 dengan metode Newton-Raphson
    K.Awal : x adalah tebakan awal akar, nilainya sudah terdefinisi
    K.Akhir: akar persamaan tercetak di layar 
  }
const 
  epsilon = 0.000001; 
var
  x_sebelumnya: real;
  function f(x:real):real;
    { 
      mengembalikan nilai f(x). Definisi f(x) bergantung pada persoalan 
    }
  function f_aksen(x:real):real;
    { 
      mengembalikan nilai f'(x). Definisi f’(x) bergantung pada persoalan 
    }
begin
  repeat
    x_sebelumnya:=x;
    x:=x - f(x)/f_aksen(x);
  until (ABS(x-x_sebelumnya) < epsilon) 
    { x adalah hampiran akar persamaan }
  write(‘Hampiran akar x = ‘, x:10:6);
end;
```

## Secant
```
procedure Secant(x0, x1:real); 
  { 
    Mencari akar persamaan f(x) = 0 dengan metode secant 
    K.Awal : x0 dan x1 adalah tebakan awal akar, terdefenisi nilainya 
    K.Akhir: akar persamaan tercetak di layar 
  } 
const 
  epsilon = 0.000001; { toleransi galat akar hampiran }
var 
  x_sebelumnya: real; 
  function f(x:real):real; 
    { 
      mengembalikan nilai f(x). Definisi f(x) bergantung pada persoalan 
    }
begin
  repeat 
    x_sebelumnya:=x1; 
    x:=x-(f(x1)*(x1 - x0)/(f(x1)-f(x0))); 
    x0:=x1; 
    x1:=x; 
  until (ABS(x-x_sebelumnya) < epsilon); 
    { x adalah hampiran akar persamaan } 
  write(‘Hampiran akar x = ‘, x:10:6); 
end; 
```
