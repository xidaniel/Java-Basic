## Set
  - HashSet: No guarantees the order of iteration
  - TreeSet: Implemented by BBST
    - There are elements are sorted.
    - TreeSet<Integer> set = new TreeSet<>(); practice: leetcode 220
    - APIs:
      - floor(E e) Returns the greatest element in this set less than or equal to the given element, or null if there is no such element.
      - ceiling(E e) Returns the least element in this set greater than or equal to the given element, or null if there is no such element.
  - LinkedHashSet: Guarantees the order
  
  
## Map <K,V>
  - HashMap
    - It can only has one null key, it is always mapped to bucket 0.
  - TreeMap
  - LinkedHashMap
  - APIs:
     - put()
     - get()
     - getOrDefault()
     - remove(K)
     - containsKey()
     - containsValue()
     - entrySet()
  - Generate a hashMap from a list or an array
```java
HashMap<Character, Integer> map = new HashMap<>();
//Method 1 in Java 8
for (char cur : s.toCharArray()) {
  Integer count = map.getOrDefault(cur, 0);
  map.put(cur, count + 1)
}

//Method 2
for (char cur : s.toCharArray()) {
  Integer count = map.get(cur);
  if (count == null) {
    count = 1;
  } else {
    count++;
  }
  map.put(cur, count);
}
```
  - Iterate each of the key, value pairs in a hashMap
  ```java
  for (Map.Entry<K, V> entry : map.entrySet()) {
      entry.getValue();
      entry.getKey();
}
