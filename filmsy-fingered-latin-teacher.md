# filmsy-fingered-latin-teacher | 132 points

<br>

## 문제에 she has trouble keeping her fingers on the right keys in home row 라는 지문을 잘 보면된다.
문제를 보면 아래와 같이 플래그가 나와있다.
```
ykvyg}pp[djp,rtpelru[pdoyopm|
```
이번 대회의 플래그 형식은 tjctf{flag} 이므로 위 주어진 문자가 플래그이면 }가 {일 것이고 |가 }일 것이다. 

그럼 결론적으로 }| 자리에 {}가 있어야하므로 키보드에 있는 키를 오른쪽으로 한칸씩 민것이다.

그래서 문제에 나와있는 문자의 한칸 왼쪽에 있는 키보드 글자를 대입해서 입력해보면 플래그가 나온다.

## flag
```
tjctf{oopshomerowkeyposition}
```
