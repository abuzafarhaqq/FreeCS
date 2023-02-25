[Back](/NTCP/01_number_theory_for_cp.md "Number Theory") | [Home Page](/README.md "Free CS") | [Previous Topic: GCD](/NTCP/basics/01_gcd.md "GCD - Basics - Number Theory")

---

LCM(Least Common Multiple) of two numbers is the smallest number which can be divided by both numbers. For example: LCM of 15 and 20 is 60, and LCM of 5 and 7 is 35.

> Simple Solution is to find all prime factors[^prime_factor] of both numbers, then find union of all factors present in both numbers. Finally, return the product of elements in union.

> Efficient Solution is based on the below formula for LCM of two numbers 'a' and 'b': a X b = LCM(a,b)*GCD(a,b);LCM(a,b)=(a X b) / GCD(a, b). Implementation of GCD is:

```cpp
//c++ program to find LCM of two numbers
#include<bits/stdc++.h>
using namespace std;
long long gcd(long long int a, long long int b){
  if(b==0) return a;
  return gcd(b, a%b);
}
long long lcm(int a, int b){
  return (a / gcd(a,b))*b;
}
int main(){
  int a = 15, b = 20;
  cout<<"LCM of "<<a<<" and "<<b<<" is "<<lcm(a, b);

  return 0;
}
```

**Time Complexity: O(log(min(a,b)))** | **Auxliary Space: O(log(min(a,b)))**


---

[^prime_factor]:
Given number **n**, write an efficient function to print all prime_factors of n. Example: If the input number is 12, then the output should be "2 2 3" and if the input number is 315, then the output should be "3 3 5 7".
First Approach:
1. While n is divisible by 2, print 2 and divide n by 2.
2. Now, "n" must be odd. Now start a loop from i=3 to the square root of n. While i divides n , print i, and divide by n by i. After i fails to divide n, increment i by 2 and continue.
3. If n is a prime number and is greater than 2, then n will not become 1 by the above two steps. So print n if it is greater than 2.
Code:
```cpp
//C++ program to print prime factors.
#include<bits/stdc++.h>
using namespace std;
//function to print all prime factors of a given number n
void primeFactors(int n){
  // print the number of 2s that divide n
  while(n%2==0){
    cout<<2<<" ";
    n/=2;
  }
  // n must be odd at this point, So, skip one element (note: i +=2)
  for(int i=3;i<sqrt(n);i+=2){
    //while i divides n, print i and divide n
    while(n%i==0){
      cout<<i<<" ";
      n/=i;
    }
  }
  //This condition is to handle  the case when n is prime number greater than 2.
  if(n>2) cout<<n<<" ";
}
int main(){
  int n = 315;
  primeFactors(n);
  
  return 0;
}
```

Prime Factors another code:
```cpp
#include<bits/stdc++.h>
using namespace std;
void primeFactors(int n){
  int c=2;
  while(n>1){
    if(n%c==0){
      cout<<c<<" ";
      n/=c;
    }
    else c++;
  }
}
int main(){
  int n=315;
  primeFactors(n);

  return 0;
}
```
