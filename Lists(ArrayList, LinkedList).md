# Lists
  -  There are two methods to implement a lists.

|   Lists Operation       | ArrayList | LinkedList(double linkedList) |  
|-------------------------|-----------|-------------------------------|
| get index at head/tail  |   O(1)    |           O(1)                |
| get index in middle     |   O(1)    |           O(n)                |
| set index at head/tail  |   O(1)    |           O(1)                |
| set index in middle     |   O(1)    |           O(n)                |
| add index in middle     |   O(n)    |           O(n)                |
| add index at head       |   O(n)    |           O(1)                |
| add at tail             |O(n)/O(1)  |           O(1)                |
| remove index at head    |   O(n)    |           O(1)                |
| remove index tail       |   O(1)    |           O(1)                |
| remove index at middle  |   O(n)    |           O(n)                |
| size()                  |   O(1)    |           O(1)                |
| isEmpty                 |   O(1)    |           O(1)                |

## Notice:
1. Array expend: default 1.5 in java.  e.g. size = 10 expend to size = 15
   - add element method of amortized time: (nx1 + 1x0.5n) / (0.5n) = 3 = O(1)
2. Eager computation is used in LinkedList for getting size
3. null and empty
   - null: there is no array object associated with the reference
    - empty array list: there is an array/list object, but the array/list object doen not contain any element.
   
          e.g.
            int[] array = null;
            int[] array = new int[0];

## How to select which data structure to implement a Lists
   - ArrayList
     - a lot of random access
     - add/remove at the end
     - When the time complexity is similar for using ArrayList and LinkedList
     - need a Vector
   - LinkedList
     - need a stack
