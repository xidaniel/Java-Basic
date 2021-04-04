## Greatest Common Divisor && Least Common Multiple

1. Euclidean Algorithm

   ```markdown
   a     b     r
   18    8    18 % 8
   8     2    8 % 2
   2     0
   
   if (b == 0) ---> return a
   ```

2. GCD code

   ```java
   public int gcd(int a, int b) {
     return b == 0 ? a : gcd(b, a % b);
   }
   ```

3. LCM code

   ```java
   public int lcm(int a, int b) {
     return a * b / gcd(a, b);
   }
   ```

4. Find a GCD in an array

   - input: [4, 2, 6, 10, 8]
   - output: 2

   ```java
   public int arrayGCD(int[] array) {
       if (array == null || array.length == 0) {
       	return -1;
       }
       if (array.length == 1) {
       	return array[0];
       }
       
       int lastGCD = gcd(array[0], array[1]);
       
       for (int i = 2; i < array.length; i++) {
          lastGCD = gcd(lastGCD, array[i]);
       }
       
       return lastGCD;
   }
   ```

   
