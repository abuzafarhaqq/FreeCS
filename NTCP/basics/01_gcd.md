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


