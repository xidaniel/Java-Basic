```java
import java.util.Arrays;
/*
APIs:
public:
        1. V put(K key, V value) synchronized
        2. V get(K key)  synchronized
        3. boolean containsKey()  synchronized
        4. boolean containsValue()  synchronized
        5. K remove(K key) synchronized
        6. int size() synchronized
        7. boolean isEmpty() synchronized
        8. void clear() synchronized
private:
        1. int hash(K key)
        2. int getIndex(int)
        3. boolean equalsKey(K key)
        4. boolean equalsValue(V value)
        5. boolean needRehashing()
        6. void rehash() synchronized         s 型曲线遍历
 */
public class MyHashMap<K, V> {
    //define entry class
    public static class Entry<K, V> {
        final K key;
        V value;
        Entry<K, V> next;
        public Entry(K key, V value) {
            this.key = key;
            this.value = value;
        }

        public K getKey() {
            return key;
        }

        public V getValue() {
            return value;
        }

        public void setValue(V value) {
            this.value = value;
        }
    }
    //define MyHashMap filed
    private static final int DEFAULT_CAPACITY = 16;
    private static final double DEFAULT_LOAD_FACTOR = 0.75;
    private static final double DEFAULT_SCALE_FACTOR = 1.5;
    private Entry<K, V>[] array;
    private int size;
    private double loadFactor;
    //define MyHash construct
    public MyHashMap() {
        this(DEFAULT_CAPACITY, DEFAULT_LOAD_FACTOR);
    }

    public MyHashMap(int capacity, double loadFactor) {
        if (capacity <= 0) {
            throw new IllegalArgumentException("capacity can not be <= 0");
            //java not allow to create generic array, must to be cast
            //this.array = (Entry<K, V>[]) (new Entry[capacity]);
            //this.loadFactor = loadFactor;
            //this.size = 0;
        }
    }

    public synchronized int size() {
        return size;
    }

    public synchronized boolean isEmpty() {
        return size == 0;
    }
    //clear hashmap, set Entry object to null and set size to 0
    public synchronized void clear() {
        Arrays.fill(array, null);
        size = 0;
    }

    private int hash(K key) {
        if (key == null) {
            return 0;
        }
        int code = key.hashCode();
        return code & 0x7FFFFFFF;
    }

    private int getIndex(int hash) {
        return hash % array.length;
    }

    private boolean equalsKey(K key1, K key2) {
        /*
        if (key1 == null && key2 == null) {
            return true;
        }
        if (key1 == null || key2 == null) {
            return false;
        }
        return key1.equals(key2);
         */
        return key1 == key2 || key1 != null && key1.equals(key2);
    }

    private boolean equalsValue(V v1, V v2) {
        return v1 == v2 || v1 != null && v1.equals(v2);
    }

    public synchronized V put(K key, V value) {
        //get hash code and index
        int index = getIndex(hash(key));
        Entry<K, V> cur = array[index];
        //case 1, key already in the hash, just update
        while (cur != null) {
            if (equalsKey(cur.key, key)) {
                V preValue = cur.value;
                cur.value = value;
                return preValue;
            }
            cur = cur.next;
        }
        //case 2, key not in hash, add to new entry in the head
        Entry<K, V> newHead = new Entry<>(key, value);
        // newHead.next = null;
        newHead.next = array[index];
        array[index] = newHead;
        size++;
        if (needRehash()) {
            rehashing();
        }
        return null;
    }

    private boolean needRehash() {
        //cast ratio to double type, because size and length are int.
        double ratio = (double)size / array.length;
        return ratio >= loadFactor;
    }

    private void rehashing() {
        Entry<K, V>[] oldArray = array;
        //create a new array
        //array = (Entry<K, V>)(new Entry[(int)(array.length * DEFAULT_SCALE_FACTOR)]);
        //rehash each entry to array
        for (Entry<K, V> entry : oldArray) {
            while (entry != null) {
                Entry<K, V> next = entry.next;
                int index = getIndex(hash(entry.key));
                entry.next = array[index];
                array[index] = entry;
                entry = next;
            }
        }
    }

    public synchronized V get(K key) {
        int index = getIndex(hash(key));
        Entry<K, V> cur = array[index];
        while (cur != null) {
            if (equalsKey(cur.key, key)) {
                return cur.value;
            }
            cur = cur.next;
        }
        return null;
    }

    public synchronized boolean containsKey(K key) {
        int index = getIndex(hash(key));
        Entry<K, V> cur = array[index];
        while (cur != null) {
            if (equalsKey(cur.key, key)) {
                return true;
            }
            cur = cur.next;
        }
        return false;
    }

    public synchronized boolean containsValue(V value) {
        if (isEmpty()) {
            return false;
        }
        for (Entry<K, V> entry : array) {
            while (entry != null) {
                if (equalsValue(entry.value, value)) {
                    return true;
                }
                entry = entry.next;
            }
        }
        return false;
    }

    public synchronized V remove(K key) {
        if (isEmpty()) {
            return null;
        }
        int index = getIndex(hash(key));
        Entry<K, V> prev = null;
        Entry<K, V> cur = array[index];
        while (cur != null) {
            if (equalsKey(cur.key, key)) {
                if (prev == null) {
                    array[index] = cur.next;
                } else {
                    prev.next = cur.next;
                }
                size--;
                return cur.value;
            }
            prev = cur;
            cur = cur.next;
        }
        return null;
    }
}

```

