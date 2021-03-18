## Java Random

###  java.util.Random

- It is a class, 

- methods:
  - nextInt(), nextDouble(), nextLong()

```java
Random rand = new Random();

// generate random number from [0,100)
int randomNum = rand.nextInt(100);
double randomDouble = rand.nextDouble(100);
```

### Math.random

- It is a method of Math class
- return double type with a positive sign
- 0.0 =< Math.random < 1.0

```java
int min = 50;
int max = 100;
//generate random numbers from [50, 100]
// using below formula
int randomInt = (int)(Math.random() * (max - min + 1) + min);
double randomDouble = Math.random() * (max - min + 1) + min;
```

### ThreadLocalRandom

- It is a class

```java
import java.util.concurrent.ThreadLocalRandom;

int rand_int1 = ThreadLocalRandom.current().nextInt();
double rand_dub1 = ThreadLocalRandom.current().nextDouble();
```

