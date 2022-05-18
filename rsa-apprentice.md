# rsa-apprentice | 126 points

<br>

## 문제에 주어진 값을 가지고 풀면 된다. (simple rsa prob)
문제 파일을 다운받아보면 
```
==== SECRET RSA MESSAGE ====
n = 1216177716507739302616478655910148392804849
e = 65537
c1 = 257733734393970582988408159581244878149116
c2 = 843105902970788695411197846605744081831851
```
라고 나와있다. 먼저 n을 이용해서 p와 q를 구해주면 된다.

나는 http://factordb.com/ 를 통해서 구해주었다.
```
p = 1033247481589406269253
q = 1177043968824330681533
```
p와 q가 이런식으로 나온다. 이제 rsa 코드를 짜서 값을 그대로 넣어주면된다.
``` python
def zx(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        g, y, x = zx(b % a, a)
        return (g, x - (b // a) * y, y)

def modi(a, m):
    g, x, y = zx(a, m)
    if g != 1:
        raise Exception('modular inverse does not exist')
    else:
        return x % m

p = 1033247481589406269253
q = 1177043968824330681533

n = 1216177716507739302616478655910148392804849
e = 65537
c1 = 257733734393970582988408159581244878149116

fi =(p-1)*(q-1)
d = modi(e, fi)
print("%x" % (pow(c1, d, n))).decode("hex")
```

``` python
def zx(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        g, y, x = zx(b % a, a)
        return (g, x - (b // a) * y, y)

def modi(a, m):
    g, x, y = zx(a, m)
    if g != 1:
        raise Exception('modular inverse does not exist')
    else:
        return x % m

p = 1033247481589406269253
q = 1177043968824330681533

n = 1216177716507739302616478655910148392804849
e = 65537
c2 = 843105902970788695411197846605744081831851

fi =(p-1)*(q-1)
d = modi(e, fi)
print("%x" % (pow(c2, d, n))).decode("hex")
```

위 두 코드를 통해 값을 구하면 아래와 같이 나오는데
``` 
746a6374667b6e30745f73305f
5333637572335f4372797037307d
```
이 16진수를 텍스트로 변환하면 플래그가 나온다.

![Untitled-2](https://user-images.githubusercontent.com/87555811/169009865-cfdac9d3-a38e-444b-a7fe-8625957476f2.png)

## flag
```
tjctf{n0t_s0_S3cur3_Cryp70}
```

