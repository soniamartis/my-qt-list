# Patterns

##Numbers
- Prime number
- Divisible by itself and 1
- To find if a number is prime or not, we need to find if the number is divisible by any numbers less than or equal to its sqrt.
- If the number is not a perfect square and is not prime, eg 20, it will have a number less than its sqrt and greater than its sqrt that will multiply to give the number eg 4*5

- Digit extraction
- To get the least sgnificant, do num %10
- To get all others, do num/10
```java
int extractDigits(int num){
  int cnt = 0
  int n = num;
  while(n!=0){
    n = n/10;
    cnt++
  }

return cnt;

}
```
