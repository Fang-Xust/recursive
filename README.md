# recursive
1.递归和非递归分别实现求第n个斐波那契数。 
2.编写一个函数实现n^k，使用递归实现 
3. 写一个递归函数DigitSum(n)，输入一个非负整数，返回组成它的数字之和， 
例如，调用DigitSum(1729)，则应该返回1+7+2+9，它的和是19 
4. 编写一个函数 reverse_string(char * string)（递归实现） 
实现：将参数字符串中的字符反向排列。 
要求：不能使用C函数库中的字符串操作函数。 
5.递归和非递归分别实现strlen 
6.递归和非递归分别实现求n的阶乘 
7.递归方式实现打印一个整数的每一位

1.递归和非递归分别实现求第n个斐波那契数。

#include<stdio.h>
#include<windows.h>
int Fibonacci()                  //非递归实现斐波那契数列求第n个数
{
	int n = 1;
	int fib1 = 1;
	int fib2 = 1;
	int fib = 2;
	printf("Please input a number:\n");
	scanf("%d", &n);
	for (int k = 3; k <= n; k++)
	{
		fib = fib1 + fib2;
		fib1 = fib2;
		fib2 = fib;
	}
	printf("第%d个Fibonacci数是：%d\n", n, fib);
	return fib;
}
int main()
{
	int ret = Fibonacci();
	system("pause");
	return 0;
}

#include<stdio.h>
#include<windows.h>
//int count = 0;
int Fib(int n)                //递归实现Fibonacci数列求第n个数
{
	//if (n == 3)
	//	count++;
	if (n <= 2)
		return 1;
	else
		return Fib(n - 2) + Fib(n - 1);
}
int main()
{
	int n = 0;
	printf("Please input a number:\n");
	scanf("%d",&n);
	int ret = Fib(n);
	printf("第%d个斐波那契数是%d:",n,ret);
	//printf("\n%d", count);
	system("pause");
	return 0;
}

2.编写一个函数实现n^k，使用递归实现

#include<stdio.h>
#include<windows.h>
int Cot(int n,int k)
{
	int ret = 1;
	for (int i = 1; i <= k; i++)         //递归实现n^k
	{
		ret = ret * n;
	}
	return ret;
}
int main()
{
	int x, y;
	printf("输入两个数字:\n");
	scanf("%d%d",&x,&y);
	int ret = Cot(x, y);
	printf("%d\n",ret);
	system("pause");
	return 0;
}

写一个递归函数DigitSum(n)，输入一个非负整数，返回组成它的数字之和，
例如，调用DigitSum(1729)，则应该返回1+7+2+9，它的和是19
#include<stdio.h>
#include<windows.h>
int Digitsum(int x)
{
	int mod_sum = 0;
	do {
		mod_sum = mod_sum + (x % 10);
		x = x / 10;
		if (x > 0 && x < 10)
		{
			mod_sum = mod_sum + x;
			break;
		}
	} while (x >= 10);   //注意循环执行到这时判断的是：是否满足这个条件，满足就继续执行循环，否则循环结束
	return mod_sum;
}
int main()
{
	int n;
	printf("请输入一个数字:\n");
	scanf("%d",&n);
	int ret = Digitsum(n);
	printf("各位数字之和为:%d\n",ret);
	system("pause");
	return 0;
}

编写一个函数 reverse_string(char * string)（递归实现）
实现：将参数字符串中的字符反向排列。
要求：不能使用C函数库中的字符串操作函数。
#include<stdio.h>
#include<windows.h>
void Reverse(char *arr, int len,int left,int right)
{                 //这里数组传参时必须传入数组有几个元素，不然会发生数组降维
	int temp;     //数组传参时函数参数列表里的char *arr等价于char arr[]
	for (; left<=right;left++,right--)
	{

		temp = arr[left];
		arr[left] = arr[right];
		arr[right]=temp;
	}
}
void show(char arr[],int len)        //char *arr等价于char arr[]
{
	for (int i = 0; i < len; i++)
	{
		printf("%c",arr[i]);
	}
}
int main()
{
	char arr[] = "ABCDEFGH";
	int len = sizeof(arr);
	int left = 0;
	int right = len - 1;
	Reverse(arr,len,left,right);
	show(arr,len);
	system("pause");
	return 0;
}

5.递归和非递归分别实现strlen

#include<stdio.h>
#include<windows.h>
int Strlen(char *arr)     //非递归实现strlen
{
	int count = 0;
	while (*arr != '\0')
	{
		count++;
		arr++;
	}
	return count;
}
int Strlen1(char arr[])     //递归实现strlen
{
	if (*arr != '\0')
		return 1 + Strlen1(arr + 1);
	else
		return 0;
}
int main()
{
	char arr[] = "dsfdsgeas";
	int ret = Strlen(arr);
	int ret1 = Strlen1(arr);
	printf("%d\n%d\n",ret,ret1);
	system("pause");
	return 0;
}

6.递归和非递归分别实现求n的阶乘

#include<stdio.h>
#include<windows.h>
int Fac(int n)              //非递归实现
{
	int fac = 1;
	for (int i = 1; i <= n; i++)
	{
		fac = fac * i;
	}
	return fac;
}
int Fac1(int n)           //递归实现
{
	if (1 == n)
		return 1;
	else
	return n * Fac1(n - 1);
}
int main() 
{
	int x = 0;
	printf("请输入一个数：\n");
	scanf("%d",&x);
	int ret = Fac1(x);
	printf("%d",ret);
	system("pause");
	return 0;
}

7.递归方式实现打印一个整数的每一位

#include<stdio.h>
#include<windows.h>
void Respective_num(int n)
{
	if (n > 0 && n < 10)
		printf("%d ",n);
	else
	{
		printf("%d ",n%10);
		Respective_num(n/10);         //递归调用
	}
}
int main()
{
	int x;
	printf("Please input a number:\n");
	scanf("%d",&x);
	Respective_num(x);
	system("pause");
	return 0;
}
--------------------- 
作者：我爱这蓝色海洋 
来源：CSDN 
原文：https://blog.csdn.net/qq_42031380/article/details/89067748 
版权声明：本文为博主原创文章，转载请附上博文链接！
