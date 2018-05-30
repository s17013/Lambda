# ランダ計算

​						작성자: 윤도훈

*  λx.x+2
  * const f = (x => x + 2);
    * (x => x + 2)(1);





*  λx.x+2(1)
  * const p = console.log;
    * p((x => x +2)(1));



* `0` := λ*f* *x*. *x*

  `1` := λ*f* *x*. *f* *x*

  `2` := λ*f* *x*. *f* (*f* *x*)

  `3` := λ*f* *x*. *f* (*f* (*f* *x*))



* const p = console.log;
  * const ZERO = f => x => x;
  * const ONE = f => x => f(x);
  * const TWO = f => x => f(f(x));
  * const THREE = f => x =>f(f(f(x)));
  * const FOUR= f => x => f(f(f(f(x))));
  * const FIVE = f => x => f(f(f(f(f(x)))));



* const toInt = n => n(x + 1)(0);

  * p(TWO(x => x + 1)(0));
  * p(toInt(TWO)); 

  두개는 같은 식임.

  

* SUCC := λn f x. f (n f x)

  PLUS := λm n f x. m f (n f x)

  PLUS := λm n. m SUCC n

  MULT := λm n. m (PLUS n) 0

  MULT := λm n f. m (n f)
  PRED := λn f x. n (λg h. h (g f)) (λu. x) (λu. u)

  PRED := λn. n (λg k. (g 1) (λu. PLUS (g k) 1) k) (λv. 0) 0

* const toInt = n => n(x + 1)(0);
* const SUCC = n =>f =>x=>f(n(f)(x));
  * p(toInt(SUCC(SUCC(ZERO))));                        



* const PLUS = m => n => f => x =>
  * p(toInt(PLUS(ONE)(TWO)));		3
    * m(f)(n(f)(x));
      * 

* const MULT = m => n=>  f => x =>
  * p(toInt(MULT(ONE)(TWO)));	2
    * m(n(f))(x);
* const POW = m => n=>  f => x =>
  * p(toInt(POW(TWO)(TWO)));		４
    * (ｎ(ｍ))(f)(x);



* const PRED = n => f  =>x => n(g => h => h(g(f)))(u => x)(u => u);
  * p(toInt(PRED((TWO));	
* const TRUE = x => y => x;
* const FALSE =x => y=> y;





* iszero?

  * const isZero = z => z(x => FALSE)(TRUE);

  * p(isZero(Zero)('yes')('no'));

    

* const CONS = x => y => f =>f(x)(y);

* const CAR = cons => cons(TRUE);

*  const CDR = cons => cons(FALSE);

* const pair = CONS(1)(0);

  * p(CAR(pair));
  * p(CDR(pair));

* let pair = CONS(1)(0);



* let list = CONS(2)(CONS(1)(null));

  const sum = list =>

  ​	CDR(list,acc = 0) ===null

  ​	? acc + CAR(list)

  ​	:sum(CDR(list),acc + CAR(list))

  p(sum(list));



- let list = CONS(2)(CONS(1)(*null*));

  const len = (list,acc = 0) =>

  ​	CDR(list) === *null*

  ​	? acc + 1

  ​	:len(CDR(list),acc + 1)

  p(len(list));

  ##	하노이의 탑

３　ー＞　３가고 2부름 -> 2가고 1부름 

```
int Hanoi(int from, int to, int n) // from번 기둥에서 to번 기둥으로 n개의 원반을 이동.
{
    if(n == 1)
    {
        printf("%d번 기둥에서 %d번 기둥으로 이동\n", from, to);
        return 0;
    }

    Hanoi(from, 6-from-to, n-1);
    printf("%d번 기둥에서 %d번 기둥으로 이동\n", from, to);
    Hanoi(6-from-to, to, n-1);
    return 0;
}int Hanoi(int from, int to, int n) // from번 기둥에서 to번 기둥으로 n개의 원반을 이동.
{
    if(n == 1)
    {
        printf("%d번 기둥에서 %d번 기둥으로 이동\n", from, to);
        return 0;
    }

    Hanoi(from, 6-from-to, n-1);
    printf("%d번 기둥에서 %d번 기둥으로 이동\n", from, to);
    Hanoi(6-from-to, to, n-1);
    return 0;
}
```





##	피보나치

https://ko.wikipedia.org/wiki/%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98_%EC%88%98

피보나치 수를 이용한 사각형 채우기
피보나치 수(영어: Fibonacci Numbers)는 수학에서 아래의 점화식으로 정의되는 수열이다.

{\displaystyle F_{n}:={\begin{cases}0&{\mbox{if }}n=0;\\1&{\mbox{if }}n=1;\\F_{n-1}+F_{n-2}&{\mbox{if }}n>1.\\\end{cases}}} {\displaystyle F_{n}:={\begin{cases}0&{\mbox{if }}n=0;\\1&{\mbox{if }}n=1;\\F_{n-1}+F_{n-2}&{\mbox{if }}n>1.\\\end{cases}}}

피보나치 수렴 그래프
피보나치 수는 0과 1로 시작하며, 다음 피보나치 수는 바로 앞의 두 피보나치 수의 합이 된다. n = 0, 1,...에 해당하는 피보나치 수는 (OEIS의 수열 A000045)

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, 2584, 4181, 6765, 10946...
이다.



https://backpaper0.github.io/ghosts/optimized_tail_call_recursive_fibonacci_in_java.html#/







https://ramdajs.com/docs/#zip メッソド集

zip,trim,add,equals,any,always,and,innerjoin,some,every