# KN-M2

## Bisection
```
procedure BagiDua(a,b: real);
  { Mencari akar f(x)=0 di dalam selang [a,b] dengan metode
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
  { mencari akar f(x) = 0 di dalam selang [a,b] dengan metode regulafalsi
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
