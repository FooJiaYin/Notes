# Common Mistakes and Code Snippets

## About OJ

- **NO NEED** to use array to store your output
可以輸入一次輸出一次


# Common Mistakes
## Declaration
* ``x = 2`` , ~~NOT `` 2 = x``~~
* `char string[n]`, n = (string length required) +1
    -  reserve a bit for `'\0'` when using `scanf()`
    ```C
    char string[5];
    scanf("%s", s); //input"star"
    ```
    

## Input and Output
* ``scanf("``裡面有除了``%d``以外其他東西``")``的話就無法execute下一行scanf
方法：在下一行前面放空格。例如：

    ```C
        scanf("(%d,%d)", &x1, &y1);
        scanf(" (%d,%d)", &x2, &y2);
        scanf("  (%d,%d)", &X, &Y);
    ```
* ``scanf`` string no need to put ``&``
    ```
    char string[10];
    scanf("%s", string);
    ```

## Data type
* float = int /2 會得到整數，要得到小數的話要 /2.0
* 注意先乘除後加減，而且是從左到右，例如
~~``(y2-y1)/(x2-x1)*1.0``~~ **False** because``(y2-y1)/(x2-x1))`` will return integer
``(y2-y1)/((x2-x1)*1.0)`` **Correct**
* Use **double**， don't use ~~float~~（more precise）

## ``for`` & `while` loop
:::warning

* ``for( ; ; )``, ~~NOT ``for( , , )``~~
* `if`/`while(x==1)` ~~NOT `(x=1)`~~
* ``i++``執行后會+1，如果要print滿足條件之前的i，要print ``i-1``
* ``for { if() break;}``
 break的是``for`` loop不是``if`` *（break不能break if）*
:::

* 在loop裏面如果已經給variable賦值，記得考慮loop結束之後要不要reset（直接下一個loop的話就reset在``for()``裡面）或者是clone
常常有出現``for(i=0; i<=j; i++)``，隨後j=i而i會+1，注意要print哪一個（``j`` or ``i-1``都可以）

* i一開始等於一個value，``for(j=1; j<i; j++,i--)``
如果condition是``j<5``（一開始的i），應該要先在loop外面clone一個``i_2=i``，然後正確的寫法：``for(j=1; j<i_2; j++,i--)``

* 某個條件之後要break可以用&&雙條件
``for(i=0; i<limit && remainder >0; i++)``

* 如果衹是想要++ until condition satisfied，可以直接在``for( )``後面加分號``;``

* 如果是<input的最大值，從最大開始算起然後``i--``比較有效率

## Array
:::warning
* ``a[10]`` declare ``a[0~9]``, ~~NOT ``a[1~10]``~~
* Array can not use to store series of ``%d``, can only use to store string (series of ``%c``)
:::
* Remember to initialize!!! `a[10]={0}`
* Always declare **LARGER size** than requirement

## Function
* function cannot return >1 value or array
can return ``struct``
* Declare array globally to 'share' array with function

## `strlen()`
遇到 strlen 的時候
條件判斷內不要用減法
因為 strlen 傳回的值是 unsigned long 
條件中如果出現負數反而會被轉換成很大的正數

#  Code Snippets

## Solving X, Y Problems
Exercise:
* [10042 - Lab01](https://acm.cs.nthu.edu.tw/problem/10042/)
* [10728 - A simple set problem](https://acm.cs.nthu.edu.tw/problem/10728/)
* [11540 - animals](https://acm.cs.nthu.edu.tw/problem/11540/)
* [11542 - Rap of china](https://acm.cs.nthu.edu.tw/problem/11542/)
* [11099 - Money Money](https://acm.cs.nthu.edu.tw/problem/11099/)
* [11551 - chickens and rabbits](https://acm.cs.nthu.edu.tw/problem/11551/)
* [11592 - Change the Cap](https://acm.cs.nthu.edu.tw/problem/11592/)

先在纸上面算好equation：``x``、``y``分别等于什么
:::warning
``x = 3*A + 2*B;``，~~NOT  ``x = 3A + 2B;``~~ 
::: 
 
## Binary
Exercise:
* [10763 - binary](https://acm.cs.nthu.edu.tw/problem/10763/)
* [11119 - binary addition](https://acm.cs.nthu.edu.tw/problem/11119/)
```C
    /* transform into inverted binary representation */
    for(i=0; input>0; input/=2, i++)
        bin[i] = input%2;
    
    /* invert back to normal */
    for(j=i-1; j>=0; j--)
        printf("%d", bin[j]);
```

## `int` to `char`
Exercise:
* [10741 - The Encoded Word](https://acm.cs.nthu.edu.tw/problem/10741/)
* [11111 - Encode number](https://acm.cs.nthu.edu.tw/problem/11111/)
```C
    int a,b,c;
    scanf("%1d%1d%1d",&a,&b,&c);
    printf("%c%c%c",a+64,b+64,c+64);
```
***Note:** Characters like 'A', 'B', 'C' are constant values. We can use them in computations such as 0*'A' + 1*'B' or 'D' - 'A'.*

## Odd and Even
Exercise:
* [11576 - Time conversion](https://acm.cs.nthu.edu.tw/problem/11576/)
* [11111 - Encode number](https://acm.cs.nthu.edu.tw/problem/11111/)

### Method 1: If else
```C
    if(x%2)
        y = M;
    else
        y = N;
```
### Method 2: Addition of Booleans
```C
    y = (x%2)*M + ((x+1)%2)*N;
```
Another example:
```C
int key_info = 'a' * ((flag+1)%2) + 'p' * flag ;
```
***Note:** if x is odd, y will have value M; if x is even, y will get value N.*

## Number Reverse
Exercise:
* [11543 - number reverse and average](https://acm.cs.nthu.edu.tw/problem/11543/)
* [11549 - Easy Palindrome](https://acm.cs.nthu.edu.tw/problem/11549/)
* [10735 - The interleaved integer](https://acm.cs.nthu.edu.tw/problem/10735/)
* [11116 - I2P(I)2016_Yang_Hw2-3](https://acm.cs.nthu.edu.tw/problem/11116/)
* [11122 - I2P Lab2-1](https://acm.cs.nthu.edu.tw/problem/11122/)

### Method 1: Scan separately
Exercise：

```C
    int a, b, c, d, REVERSE;

    scanf("%1d%1d%1d%1d", &a, &b, &c, &d);

    REVERSE = (d*1000 + c*100 + b*10 + a);
```
***Note:** Only for known number of digit.*

### Method 2: By division
```C
    int input, a, b, c, d, REVERSE;
    
    scanf("%d", &input);
    
    a = input/1000,
    b = (input/100)%10;   //OR b = (input%1000 - input%100)/100
    c = (input/10)%10;    //OR c = (input%100 - input%10)/10 
    d = input%10;
    
    REVERSE = (d*1000 + c*100 + b*10 + a);
```
### Method 3: Unknown no of digits 
*Evaluate from [Method 2](#method-2-by-division)*

```C
    long input, REVERSE, n;
    int digit[10]={0}, i;

    scanf("%ld", &input);

    /* Get numbers */
    for(i=0, n=1; i<=10; n*=10, i++)
        digit[i]=(input/n)%10;

    /* Find i = number of digits */
    for(i=10;!(digit[i]);i--);

    /* Reverse and sum up */
    for(n=1, REVERSE=0; i>=0; n*=10, i--)
        REVERSE += digit[i]*n;

    printf("%d",REVERSE);
```

## Average
Exercise:
* [11543 - number reverse and average](https://acm.cs.nthu.edu.tw/problem/11543/)
```C
    SUM = (a+c)*101 + 2*b*10 + (f+d)*0.101 + 2*e*0.01;
    printf("%.3f", SUM);
```

## Separator
Exercise:
* [11113 - Thousands Separator Lite](https://acm.cs.nthu.edu.tw/problem/11113/)
* [11120 - Float addition](https://acm.cs.nthu.edu.tw/problem/11120/)
```C
    scanf("%d,%d,%d.%d", &input1[0], &input1[1], &input1[2], &input1[3]);
    scanf("%d,%d,%d.%d", &input2[0], &input2[1], &input2[2], &input2[3]);

    SUM = (input1[0]+input2[0])*1000000 + (input1[1]+input2[1])*1000 + (input1[2]+input2[2]) + (input1[3]+input2[3])/1000.0;

    printf("%.3f", SUM);
```

## Prime Number
Exercise:
* [11572 - Prime](https://acm.cs.nthu.edu.tw/problem/11572/)
* [11591 - Book Donation Program](https://acm.cs.nthu.edu.tw/problem/11591/)
* Prime Number
* Practice - largest prime number
* Practice - nth prime

### Method 1 (slower)
```C
for(number = 1; number <= limit; number++)
{
    for(divisor = 2; divisor < number && number%divisor > 0; divisor++);
    if(number == divisor)
       printf("%d\n", number);
}
```

### Method 2 (faster)
* **Concept:** 
  1. `number+=2`: skip all even numbers 
  2. `divisor*divisor<number`: factors <= square root of number
Time ~ square root of time of [Method 1](#method-1-slower) /2
* **Note:** specific case for 1
```C
for(number = 1; number <= limit; number+=2)
{
    for(divisor=2; number%divisor > 0 && divisor*divisor<number; divisor++);
    if((x%divisor > 0 && number>1)
        printf("%d\n", number);
}
```

***Note:***
> 任何數字``/1``都可以，沒有remainder，找prime number不能從``%1``開始``++``

## Swaps

Exercise:
* [10766 - Shell Game](https://acm.cs.nthu.edu.tw/problem/10766/)

```C
    int ball[5]={0,1,2,3,4}, k, swap1, swap2, temp;

    scanf("%d", &k);

    for(k=k;k>0;k--)
    {
        scanf("%d %d", &swap1, &swap2);
        temp = ball[swap1];
        ball[swap1] = ball[swap2];
        ball[swap2] = temp;
    }
    
    printf("%d %d %d %d %d", ball[0], ball[1], ball[2], ball[3], ball[4]);
```
## GCD and LCM

Exercise:
* [11160 - GCD and LCM](https://acm.cs.nthu.edu.tw/problem/11160/)
* Practice - GCD and LCM

### Method 1: Using Prime Factors
```C
int gcd(int a, int b)
{
    int i;
    if(a<=b)
        for(i=a; i>=0 && (a%i>0 || b%i>0); i--);
    else
        for(i=b; i>=0 && (a%i>0 || b%i>0); i--);
    return i;
}

int lcm(int a, int b)
{
    int i;
    if(a<=b)
        for(i=b; i%a>0 || i%b>0; i++);
    else
        for(i=a; i%a>0 || i%b>0; i++);
    return i;
}
````
### Method 2: Using the Divisor Algorithm (GCD)
Theory and Explaination: 
- [wikiHow to Find the Greatest Common Divisor of Two Integers](http://www.wikihow.com/Find-the-Greatest-Common-Divisor-of-Two-Integers)
- [Euclidean algorithm - Wikipedia](https://en.wikipedia.org/wiki/Euclidean_algorithm)

#### Recursion
```C
// A piece of C code
#include <stdio.h>  // GCD 遞迴版
int GCD(int a, int b){
    if( b == 0 )
        return a;
    else
        return GCD( b, a%b );
}
int main(void){
    int a, b; // a,b > 0 
    scanf("%d%d", &a, &b);
    printf("%d\n", GCD(a,b));
    return 0;
}
```

#### Loop
```C
// A piece of C code
#include <stdio.h> // GCD 迴圈版
int main(void){
    int a, b; // a,b > 0 
    scanf("%d%d", &a, &b);
    while( a!=0 && b!=0 ){
        if( a > b )
        	a = a % b;
        else
        	b = b % a;
    }
    if( a != 0 )
        printf("%d\n", a);
    else
        printf("%d\n", b);
    return 0;

```
***Note:*** ``GCD of a,b,c = GCD(GCD(a,b),c)``,
        ``LCM of a,b,c = LCM(LCM(a,b),c)``

## Print patterns
Exercise:
* [11533 - Christmas tree](https://acm.cs.nthu.edu.tw/problem/11513/)
* [11129 - Alphabet Diamond](https://acm.cs.nthu.edu.tw/problem/11129/)
* [11593 - Mexican Wave](https://acm.cs.nthu.edu.tw/problem/11593/)

> Mostly use ``for`` loop

### Using the %*.s format in printf()
```C
#include <stdio.h>
#include <string.h>
#define BORDER "############################################"
int main(void)
{
    char word[26];
    scanf("%25s", word);
    printf("%.*s\n", strlen(word)+2, BORDER);
    printf("#%s#\n", word);    
    printf("%.*s\n", strlen(word)+2, BORDER);

    return 0 ;
}
/*
Input: University
############
#University#
############
*/
``

````
### Method 2: Using the Divisor Algorithm (GCD)

#### Recursion
```C
// A piece of C code
#include <stdio.h> // GCD 遞迴版
int GCD(int a, int b){
    if( b == 0 )
        return a;
    else
        return GCD( b, a%b );
}
int main(void){
    int a, b; // a,b > 0 
    scanf("%d%d", &a, &b);
    printf("%d\n", GCD(a,b));
    return 0;
}
```

#### Loop
```C
// A piece of C code
#include <stdio.h> // GCD 迴圈版
int main(void){
    int a, b; // a,b > 0 
    scanf("%d%d", &a, &b);
    while( a!=0 && b!=0 ){
        if( a > b )
        	a = a % b;
        else
        	b = b % a;
    }
    if( a != 0 )
        printf("%d\n", a);
    else
        printf("%d\n", b);
    return 0;

```
***Note:*** ``GCD of a,b,c = GCD(GCD(a,b),c)``,
        ``LCM of a,b,c = LCM(LCM(a,b),c)``

## Big Number

### Step 1: Input
1.  Scan as `string`
2. Convert `char`(ASCII) to  `int` (decimal)：

    ```C
    for(i=0; i<strlen(string); i++) 
        a[i]-='0'
    ```
    
### Step 2: Reverse
- decimal places 對齊

### Addition (Carry)
```C
for(i=strlen(a); i>0; i--)
        {
            sum[i] += a[i-1]-'0' + b[i-1]-'0';
            sum[i-1] += sum[i]/10; //carry
            sum[i] %= 10;
        }
```

## Sorting

### Method 1: Insertion Sort

### Method 2: Bubble Sort（氣泡排序法）
- Flag

### Method 3: `qsort`

### 