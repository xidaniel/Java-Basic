+++

## Background

There are two methods to implement sorting for **_Custom Class_** in Java.

- **Comparable< T >**

  - It is an interface

  - < T > - the type of objects that this object may be compared to

  - It has only method:  

    ```java
    int compareTo(T o) {
      "do something"
    }
    ```

  - [Java doc reference](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html)

- **Comparator< T >**

  - It is an interface

  - < T > - the type of objects that may be compared by this comparator

  - We usually use one method

    ```java
    int compare(T o1, T o2) {
      "do something"
    }
    ```

  - [Java doc reference](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html)	

---

## Why Use It?

- 我们需要对自定义的类排序时,但是Java内部没有实现这样的接口

- 比如我们自定义一个类叫Dog, 要求根据dog的年龄进行排序

- ```java
  public class Dog {
      String name;
      int age;
      
      public Dog(String name, int age) {
          this.name = name;
          this.age = age;
      }
      
      @Override
      public String toString() {
          return "Dog{" +
                  "name='" + name + '\'' +
                  ", age=" + age +
                  '}';
      }
  }
  ```

- Output 会报错:

  ```java
  public class Main {
      public static void main(String[] args) {
          Dog[] dogs = {new Dog("David", 3), new Dog("Bill", 1)};
          Arrays.sort(dogs);
          System.out.println(Arrays.toString(dogs));
      }
  }
  /*
  Exception in thread "main" java.lang.ClassCastException: com.algoxi.my_error.comparable.Dog cannot be cast to java.lang.Comparable
  	at java.util.ComparableTimSort.countRunAndMakeAscending(ComparableTimSort.java:320)
  	at java.util.ComparableTimSort.sort(ComparableTimSort.java:188)
  	at java.util.Arrays.sort(Arrays.java:1246)
  	at com.algoxi.Main.main(Main.java:12)
  */
  ```

  

---

## How To Use It?

1. 用comparable

   - Dog类直接实现 comparable
   - Dog类里面也要实现compareTo的方法

   ```java
   public class Dog implements Comparable<Dog> {
       String name;
       int age;
   
       public Dog(String name, int age) {
           this.name = name;
           this.age = age;
       }
   
       @Override
       public String toString() {
           return "Dog{" +
                   "name='" + name + '\'' +
                   ", age=" + age +
                   '}';
       }
   
       @Override
       public int compareTo(Dog o) {
           if (this.age == o.age) {
               return 0;
           }
           return this.age < o.age ? -1 : 1;
       }
   }
   ```

   - Output:

   ```java
   public class Main {
       public static void main(String[] args) {
           Dog[] dogs = {new Dog("David", 3), new Dog("Bill", 1)};
           Arrays.sort(dogs);
           System.out.println(Arrays.toString(dogs));
       }
   }
   
   /*
   [Dog{name='Bill', age=1}, Dog{name='David', age=3}]
   */
   ```

2. 用Comparator

   - 原来的Dog保持不变

   ```java
   public class Dog {
       String name;
       int age;
   
       public Dog(String name, int age) {
           this.name = name;
           this.age = age;
       }
   
       @Override
       public String toString() {
           return "Dog{" +
                   "name='" + name + '\'' +
                   ", age=" + age +
                   '}';
       }
   }
   ```

   - 创建一个DogComparator类

   ```java
   import java.util.Comparator;
   
   public class DogComparator implements Comparator<Dog> {
   
       @Override
       public int compare(Dog o1, Dog o2) {
           if (o1.age == o2.age) {
               return 0;
           }
           return o1.age < o2.age ? -1 : 1;
       }
   }
   ```

   - Output:
   - 要对comparator进行new的操作

   ```java
   public class Main {
       public static void main(String[] args) {
           Dog[] dogs = {new Dog("David", 3), new Dog("Bill", 1)};
           Arrays.sort(dogs, new DogComparator());
           System.out.println(Arrays.toString(dogs));
       }
   }
   /*
   [Dog{name='Bill', age=1}, Dog{name='David', age=3}]
   */
   ```

---

## Anonymous Inner Class

- Anonymous Example

- ```java
  PriorityQueue<Dog> minHeap = new PriorityQueue<>(new Comparator<Dog>() {
    @Override
    public int compare(Dog o1, Dog o2) {
      if (o1.age == o2.age) {
        return 0;
      }
      return o1.age < o2.age ? -1 : 1;
    }
  });
  ```
- lambda
- ```java
  PriorityQueue<Dog> minHeap = new PriorityQueue<>((o1, o2) -> o1.age - o2.age));
  ```

- Normal Example

- ```java
  PriorityQueue<Dog> minHeap = new PriorityQueue<>(new DogComparator());
  ```

- ```java
  public class DogComparator implements Comparator<Dog> {
      @Override
      public int compare(Dog o1, Dog o2) {
          if (o1.age == o2.age) {
              return 0;
          }
          return o1.age < o2.age ? -1 : 1;
      }
  }
  ```

- Another Tips:
  
  - We can use **Collections.reverseOrder()** in PriorityQueue's constructor to implement **maxHeap**.

---

## "==" and equals

- For Object

  - check value: **o1.equals(o2)**

  - check address: o1 == o2

  - ```java
    public static void main(String[] args) {
      String s1 = new String("abc");
      String s2 = new String("abc");
      System.out.println(s1 == s2);
      // false
      System.out.println(s1.equals(s2));
      //true
    }
    ```

    - because constant pool, they are created in same address

  - ```java
    public static void main(String[] args) {
      String s1 = "abc";
      String s2 = "abc";
      System.out.println(s1 == s2);
      // true
      System.out.println(s1.equals(s2));
      //true
    }
    ```

- For Primitive Type

  - check value: i1 == i2

end.
