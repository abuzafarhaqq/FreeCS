[Back](/NTCP/01_number_theory_for_cp.md "Number Theory") | [Home Page](/README.md "Free CS")
# Program to Find GCD and HCF of Two Numbers

---

GCD(Greatest Common Divisor) / HCF(Highest Common Factor) of Two Numbers is the largest number that divided both of them.
Example: GCD of 20 and 28 is: 4; GCD of 98 and 56 is: 14.
Simple and Old method is: **Euclidean Algorithm by Subtraction**
> It is a process of repeat subtraction, carrying the result forward each time untill the result is equal to any one number being subtracted. If the answer is greater than 1, there is a GCD (besides 1). If the answer is 1, there is no common divisor (besides 1), and so both numbers are coprime.
Pseudo Code for the approach:
```python
def gcd(a, b):
  if(a==b):
    return a
  if(a>b):
    gcd(a-b, b)
  else:
    gcd(a, b-a)
```
Simple Solution: For finding the GCD of two numbers we will first find the minimum of the two numbers and then find the highest common factor of that minimum which is also the factor of the other number.

```cpp
// GCD Finder : CPP
#include<iostream>
using namespace std;
int gcd(int a, int b){
  int result = min(a, b); //Find Minimum of a, b
  while(result > 0){
    if((a%result==0) && (b%result==0)){
      break;
    }
    result--;
  }
  return result;
}
int main()
{
  int a, b;
  cout<<"Enter Two Number: ";
  cin>>a>>b;
  cout<<"GCD of "<<a<<" and "<<b<<" is "<<gcd(a, b);

  return 0;
}
```

```java
// GCD Finder : Java
public class CFG{
  static int gcd(int a, int b){
    int result = Math.min(a, b);
    while(result>0){
      if(a%result == 0 && b%result == 0){
        break;
      }
      result--;
    }
    return result;
  }
  public static void main(String[] args){
    int a = 98, b = 54;
    System.out.print("GCD of " + a + " and " + b + " is " + gcd(a, b));
  }
}
```
```python
# GCD Finder : Python
def gcd(a, b):
  result = min(a, b)
  while result:
    if a%result == 0 and b% result == 0:
      break
    result -= 1
  return result

a = 98
b = 56
print(f"GCD of {a} and {b} {gcd(a,b)}")
```

**Time Complexity: O(min(a,b))** | **Auxiliary Space: O(1) / Constant**

> An efficient solution is to use **Euclidean Algorithm which is the main algorithm used for this purpose. The idea is, GCD of two numbers doesn't change if a smaller number is subtracted from a bigger number.

```cpp
//GCD Finder Euclidean: CPP
#include<iostream>
using namespace std;
int gcd(int a, int b){
  if(a==0) return b;
  if(b==0) return a;
  if(a==b) return a;
  if(a>b) return gcd(a-b,b);
  return gcd(a, b-a);
}
int main()
{
  int a=98, b=56;
  cout<<"GCD of "<<a<<" and "<<b<<" is: "<<gcd(a, b);
  return 0;
}
```
**Time Complexity: O(min(a, b))** | **Auxiliary Space: O(min(a,b))**

> Dynamic Programming Approach (Top Down Using Memoization):
```cpp
#include<bits/stdc++.h>
using namespace std;
int static dp[1001][1001];
int gcd(int a, int b){
  if(a==0) return b;//everything divides 0
  if(b==0) return a;
  if(a==b) return a;//base case
  if(dp[a][b] != -1) return dp[a][b]; //if a value is already present in dp
  if(a>b) dp[a][b] = gcd(a-b,b);//a is greater.
  else dp[a][b] = gcd(a, b-a);//b is greater.
  return dp[a][b];//return dp
}
int main(){
  int a = 98, b = 56;
  memset(dp, -1, sizeof(dp));
  cout<<"GCD of "<<a<<" and "<<b<<" is "<<gcd(a, b)<<endl;
}
```

**Time Complexity: O(min(a,b))** | **Auxiliary Space: o(1)**

> Instead of Euclidean Algorithm by subtraction, a better approach can be divided the bigger with smaller one. An Example using the Modulo Operator in Euclidean Algorithm:

```cpp
#include<iostream>
using namespace std;
//recursive function return gcd of a, b in single line
int gcd(int a, int b){
return b == 0 ? a : gcd(b, a % b);
}
int main(){
int a = 98, b = 56;
cout<<"GCD of "<<a<<" and "<<b<<" is "<<gcd(a, b);

return 0;
}
```

**Time Complexity: O(log(min(a,b)))** | **Auxiliary Space: O(log(min(a,b)))**

> Time Complexity is here O(log(min(a,b))) which is derivation for the worst case scenario. If we go to step by step up like: (1,1) (1,2) (2,3) (3,5) (5,8).
> We can notice the pattern like: for the nth step the numbers would be (fib(n), fib(n+1)). So, time complexity would be O(n) where a=> fib(n) and b=> fib(n+1).
> Now, Fibonacci series is an exponentially growing series where the ratio of nth/(n-1)the term approaches (sqrt(5)+1)/2 which is also called the golden ratio.
> So we can see that the time complexity hence time complexity would be log(min(a,b))

You can request to change here if you don't like it.

---

[Back](/NTCP/01_number_theory_for_cp.md "Number Theory") | [Home Page](/README.md "Free CS") | [Next Page: LCM](/NTCP/basics/02_lcm.md "LCM | Basics | Number Theory")

