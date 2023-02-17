# 程序设计实践入门——基础编程II



**题目：  IBM Minus One**

如果你按字母表的顺序，将“HAL”一词中的每一个字母用下一个字母替换，则是“IBM”。请你编写一个程序来找出这样的联系。

输入：

输入的第一行给出整数n,表示后面的字符串的数目。接下来的n行每行给出一个字符串，最多位50个大写字母。

输出：

对于输入中的每个字符串，首先，输出字符串的编号，如样例输出所示。然后，输出一个由输入字符串所派生的字符串，将输入字符串中的每个字母都按字母表顺序，用下一个字母，并用‘A‘ 替换’Z‘。

在每个测试用例后输出空行。

| 样例输入 | 样例输出  |
| -------- | --------- |
| 2        | String #1 |
| HAL      | IBM       |
| SWERC    |           |
|          | String #2 |
|          | TXFSD     |

 代码如下：

```C++
#include <iostream>
#include <cstring>
using namespace std;

int main()
{
    char str[50];
    int  j = 0, n;

    cin >> n;
    while(j++ < n)
    {
        scanf("%s",str);

         int i = 0;
         while(str[i] != '\0')
         {
            str[i] = str[i] == 'Z' ? 'A': str[i] + 1;

            i++;
         }

         printf("String #%d\n%s\n",j,str);

    }

    return 0;
}
```

<!下面是书上给参考代码---->

```C++
#include <iostream>
#include <string>
using namespace std;

int main()
{
    int n;
    string s;

    cin >> n;
    for(int i = 0; i < n; i++)
    {
        cin >> s;
        int l = s.length();
        cout << "String # " << i + 1 << endl;
        for(int j = 0; j < l; j++)
            if(s[j] == 'Z')
                cout << 'A';
            else
                cout << (char)(s[j] + 1);
        cout << endl;
    }
    return 0;
}


```



**题目：对称三位数素数**

题目内容
判断一个数是否为对称三位数素数。所谓“对称”是指一个数，倒过来还是该数。例如，375不是对称数，因为倒过来变成了573。
输入描述∶

输入数据含有不多于50个的正整数（0<n<2的32次方）。

输出描述∶

对于每个n，如果该数是对称三位数素数，则输出"Yes"，否则输出"No"。每个判断结果单独列一行。
输入样例

11 101 272 

输出样例

No 

Yes 

No

代码如下：

```C++
#include <iostream>
#include <cstring>
#include <string>
#include <algorithm>
using namespace std;
bool  Isprime(int n)
{
    int k;
    bool label = true;

    for( k = 2; k < n; k++)
    {
        if(n % k == 0)
        {
            label = false; break;
        }
    }

    return label;
}

int main()
{
    int n;
    int num;

    cin >> n;

    while( n--)
    {
        cin >> num;
        char sn[10];
        if(num /100 <= 9 && num /100 >= 1)
        {   
            bool  flag;
            itoa(num,sn,10);
            for(int j = 0, k = strlen(sn) - 1; j < strlen(sn);j++, k--)
            {    
                flag = true;
                if( sn[j] != sn[k])
                {
                    flag = false;break;
                }
            }
            if(flag == true && Isprime(num))
                cout << "YES"  << endl;                          
              
            else
                cout << "NO"  << endl;        

        }
        else
            cout << "NO"  << endl;
    }

    return 0;

}
```

<!下面是书上参考代码---->

```C++
#include <iostream>
#include <cmath>
using namespace std;

bool isPrime(int x)
{
    int sqr = sqrt(x * 1.0);
    for(int i = 2; i <= sqr; i++)
     {
         if( x % i == 0) return false;
     }  

     return true;
}
int main()
{
    int n;
    
    while(cin >> n)
    {
        cout << (n > 100 && n < 1000 && n/100 == n % 10 && isPrime(n)? "YES\n":"NO\n");
    }

    return 0;
}
```



**题目：排列对称串**

 题目内容：
字符串有些是对称的，有些是不对称的，请将那些对称的字符串按从小到大的顺序输出。字符串先以长度论大小，如果长度相同，再以ASCII码值为排序标准。
输入描述∶输入数据中含有一些字符串（1≤串长≤256）。
输出描述∶根据每个字符串，输出对称的那些串，并且要求按从小到大的顺序输出。

输入样例

123321

 123454321

 123 

321 

sdfsdfd 

121212 

\ \\dd\\\

输出样例

123321

 \\dd\\

123454321

代码如下：

```C++
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool Comp(const string &s1, const string &s2)
{
    if(s1.length() != s2.length()) return   s1.length() < s2.length();
    else
        return  s1 < s2;

}

int main()
{
    string  s;
    vector<string> vs;

     while(cin >> s)
     {  
        bool flag = true;
        for(int i = 0, j = s.length() -1 ; i < j; i++,j--)
        {
            if(s[i] != s[j])
            {
                flag = false;break;
            }
        }

        if(flag == true)
            vs.push_back(s);
     }

     sort(vs.begin(),vs.end(),Comp);
     vector<string>:: iterator it;

     for(it = vs.begin(); it != vs.end(); it++)
        cout << *it  << endl;

    return 0;

     
}
```

<!下面是书上参考代码---->

```C++
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

bool Comp(const string &s1, const string &s2)
{
    return s1.length()!= s2.length()?s1.length() <s2.length() : s1 < s2;
}

int main()
{
    vector<string> v;
    string s,t;

    while(cin >> s)
    {
        t = s;
        reverse(t.begin(),t.end());
        if(t == s)
            v.push_back(s);
    }

        sort(v.begin(),v.end(),Comp);

        for(int i = 0; i < v.size(); i++)
            cout << v[i] << endl;C++
 

    return 0;
}
```

