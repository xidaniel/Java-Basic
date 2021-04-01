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
[reference](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)
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

  ```

- Can do sorting for Map directly, add entry.set() to a list, then using collections to sort list

```java
public List<Map.entry<Character, Integer> sortByValue() {
  Map<Character, Integer> map = new HashMap<>();
  map.put('a', 2);
  map.put('v', 1);
  map.put('s', 5);
  map.put('t', 4);
  
  //put entryset to a list
  List<Map.Entry<Character, Integer>> array = new ArrayList<>(map.entrySet());
  Collections.sort(array, (a, b) -> b.getValue().compareTo(b.getValue()));
  return array;
}
```

## TreeMap

- TreeMap is sorted map
- default is ascending

```java
Map<Character, Integer> map = new TreeMap<>((a, b) -> b.compareTo(a));
```

```java
public int compare(Student p1, Student p2) {
    if (p1.score == p2.score) {
        return 0;
    }
    return p1.score > p2.score ? -1 : 1;
}
```

