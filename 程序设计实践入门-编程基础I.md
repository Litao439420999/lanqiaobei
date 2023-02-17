# 编程基础

题目：Sum

请你求出1~n之间的所有整数的总和

输入：

输入是一个绝对值不大于10000的整数n

输出：

输出一个整数，该整数是所有在1~n之间的整数的总和。

| 样例输入 | 样例输出 |
| -------- | -------- |
| -3       | -5       |

第一种方法：

```C++
#include <iostream>
using namespace std;

int main()
{
    int n,sum = 0;

    cin >> n;
    if(n > 0)
        for(int i = 1; i <= n; i++)
            sum += i;
    else
        for(int i = 1; i >= n; i--)
            sum += i;
    cout << sum << endl;
    
    return 0;
}
```

第二种方法：

```C++C++
#include <iostream>
using namespace std;

int main(void)
{
    int n,sum=0;

    cin >> n;

    if(n > 0)
        sum = (1 + n) * n / 2;
    else
        sum =(1 - n) * n / 2 + 1; // 注意

    cout << sum << endl;
}
```


$$
如果n > 0 的正整数，Sn = 1 + 2 +... + n = n * (n + 1) / 2 ;

否则 Sn =  n * (1 - n) / 2 + 1;
$$
题目2  Gold Coins（POJ2000）

国王要给他的忠诚骑士支付金币。在他服务的第一天，骑士将获得一枚金币。在接下来的两天的每一天（服务的第二和第三天），骑士将获得2枚金币。在接下来的3天的每一天（服务的第四、五、六天），骑士将获得3枚金币。在接下来的4天的每一天（第七、八、九、十），骑士将获得4枚金币。这种支付模式将无限期地继续下去：在连续N天的每一天获得N枚金币，在下一个连续的N+1天的每一天，骑士将获得N+1枚金币，其中N是任意的正整数。

请编写程序，在给定天数的情况下，求出国王要支付给骑士的金币的总数（从第一天开始计算）；

输入：

输入至少一行，至多21行。每行给出问题的一个测试数据，即一个整数（范围为1~10000）表示天数。一行给出0表示输入结束。

输出：

对于输入中给出的每个测试用例，输出一行。每行先给出在输入中给出的天数，后面是一个空格，然后是在这些天数中，从第一天开始计算总共要支付给骑士的金币数。

| 样例输入 | 样例输出      |
| -------- | ------------- |
| 10       | 10  30        |
| 6        | 6    14       |
| 7        | 7   18        |
| 11       | 11  35        |
| 15       | 15  55        |
| 16       | 16  61        |
| 100      | 100  945      |
| 10000    | 10000  942820 |
| 1000     | 1000  29820   |
| 21       | 21   91       |
| 22       | 22   98       |
| 0        |               |

第一种方法：

```C++
#include <iostream>
using namespace std;

int main()
{
    int day,coin ;
    int i,j,k;

   while( cin >> day,day)
   {   coin = 0;
        for(j = 1,i = 1; j <= day; i++)
        {
            for(k = j; k < j + i; k++)
                if( k<= day)
                    coin += i;
                else break;
        
             j = k ;
        }

        cout << day <<" " << coin;

   }

   
    return 0;
}
```



第二种方法：

```C++
#include <iostream>
using namespace std;

int main()
{
    int i,n,m,ans;

    while(cin >> n,n)
    {
        ans = m = 0;
        for(i = 1;m + i <= n; m += i++)
            ans += i * i;
        ans += ( n - m) * i;
        cout << n << " " << ans << endl;
    }
    return 0;

}
```



题目：Hashmat the Brave Warrior

​	Hashmat 是一个勇敢的战士，他和一群年轻的士兵要从一个地方到另一个地方同敌人进行战斗。在战斗之前，他要计算他的士兵人数和敌方士兵的人数的差，由此决定是否和敌人作战。Hashmat的士兵人数不会超过地方士兵的人数。

输入：

输入的每行给出两个数字。这两个数字表示Hashmat的士兵人数和敌方的士兵人数，或者反之。输入数字不大于2的32次方。输入以“End of File”终止。

输出：

对于每行输入，输出Hashmat的士兵人数和敌方的士兵人数的差。每个输出单独一行。

| 样例输入 | 样例输出 |
| -------- | -------- |
| 10  12   | 2        |
| 10  14   | 4        |
| 100 200  | 100      |

第一种方法：

```c++
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
   long long  int a,b;
    while(cin >> a >> b )    
    {
        cout << abs(a-b) << endl;
    }

    return 0;
}
```



第二种方法：

```C++
#include <cstdio>
using namespace std;

int main()
{
    long long int a,b;

    while(scanf("%lld%lld",&a,&b)!= EOF )
        if(b > a)
            printf("%lld\n",b - a);
        else
             printf("%lld\n",a - b);
    return 0;
}
```

***注意：***

本题给出的输入数据的范围和规模。输入的数字不大于2的32次方，需选用long long int 作为输入数据的类型（8个字节)。



作业：

1. **Primary Arithmetic：**

   小学生学习算术的多位加法运算时，被教导对两个加数从右向左、每次相同位的两个数字相加。对于小学生，“进位”运算是一个很大的挑战，要把一个1从当前位加到下一位。给出一组加法题，请计算每个加法题的进位运算的次数，以便教育主管评估这些题目的难度。

   输入：

   输入的每一行给出两个不超过10位数字的无符号整数，输入的最后一行给出0 0。

   输出：

   对于除最后一行以外的每一行的输入，计算并输出两个数字相加产生的进位运算的次数，格式如样例输出所示。

   | 样例输入 | 样例输出            |
   | -------- | ------------------- |
   | 123 456  | No carry operation  |
   | 555 555  | 3   carry operation |
   | 123 594  | 1   carry operation |
   | 0   0    |                     |

   代码如下：

   ```C++
   #include <iostream>
   using namespace std;
   
   int main()
   {
       int num1,num2;
       while(cin>> num1 >> num2,num1 || num2)
       {
           int n1 = num1,n2 = num2;
           int count = 0;
           while(n1 && n2)
           {
               if ( (n1 % 10 + n2 % 10) >= 10)
                   count++;
               
               n1 /= 10;
               n2 /= 10;
           }
           if(count != 0)
           cout << count << " carry operation." << endl;
           else
           cout << "No carry operation." << endl; 
       }
   
       return 0;
   }
   
   
   ```

   <!--书上代码如下-->

   ```C++
   #include <cstdio>
   using namespace std;
   
   int main()
   {
       int a, b;
   
       while(scanf("%d%d",&a,&b) == 2)
       {
           if(!a && !b) return 0;
           int c = 0, ans = 0;
   
           for(int i = 9; i >= 0; i--)
           {
               c = ( a % 10 + b % 10 + c) > 9 ? 1 : 0;
               ans += c;
               a /= 10;
               b /= 10;
           }
   
           if(ans == 0)
               printf("No carry operation.\n");
           else
               printf("%d carry operations.\n",ans);
           
           
       }
       return 0;
   }
   ```

   

2. **The 3n+1 problem：**（POJ1207)

给定一个输入n,在被1被打印前可以确定被打印数字的个数，这样的个数被称为n的循环长度。

对于任意两个整数i 和j ,请计算在i和j之间的整数中循环长度的最大值。

输入

输入是由整数i 和j 组成的整数对序列，每队一行，所有整数都小于10000大于0。

输出

对输入的每队整数i和j,请输出i,j,以及i和j之间的所有整数中循环长度的最大值。这三个数字在一行输出，彼此间至少用一个空格分开。在输出中，i和j按输入的次序出现，然后是最大循环长度（在同一行中）。

| 样例输入 | 样例输出     |
| -------- | ------------ |
| 1 10     | 1 10 20      |
| 100 200  | 100 200 125  |
| 201 210  | 201 210 89   |
| 900 1000 | 900 1000 174 |

代码如下：

```C++
#include <iostream>
using namespace std;

int main()
{
    int a,b;

    while(cin >> a >> b)
    {
        int i, max = 0;
        for(i = a; i <= b; i++)
        {   
            int n = i,count = 1;
            while(n != 1)
            {
                if(n % 2 == 0)
                    n /= 2;
                else
                   n =  3 * n + 1;
                
                count++;

            }

            max = (max < count)?count:max;
        }

        cout << a << " " << b << " " << max << endl;
    }

    return 0;
}
```

下面是书上代码<!--书上代码-->有问题

```c++
#include <iostream>
using namespace std;

int main()
{
    int i,a,b,c,d,ans,n,m;

    while(cin >> a >> b)
    {
        ans = 0;
        c = min(a,b);
        d = max(a,b);

        for(n = c; c <= d; n++)
        {
            for(i = 1, m = n; m > 1; i++)
            {
                if (m % 2 == 0)
                    m /= 2;
                else
                    m = 3 * m + 1;
            }

            if( i > ans) ans = i;
        }

        cout << a << " " << b << " " << ans << endl;
    }
    return 0;
}
```

