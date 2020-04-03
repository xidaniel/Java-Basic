# Queue & Stack & Deque
  - Queue: FIFO
    - Keep to use same type API
    
    | Type of Operation    | throw expection | return special value(null) |  
    |-------------------------|-----------|-------------------------------|
    | Insert  |   add()    |           offer()                |
    | Remove  |   remove()    |           poll()                |
    | Examine |   element()    |           peek()                |

  - Deque: FIFO & LIFO

    |  Type of Operation   | throw expection | return special value(null) | throw expection | return special value(null)  
    |-------------------------|-----------|-------------------------------|-----------|-------------------------------|
    | Insert  |   addFirst() / pusth()|           offerFirst()            | addLast() | offerLast()
    | Remove  |   removeFirst() / pop()|           pollFirst()            | removeLast() | pollLast()
    | Examine |   getFirst() / peek()    |           peekFirst()          | getLast() | peekLast()
  
    - other useful methods: isEmpty(), size()
    - Most popular implementation class: <b>LinkedList and ArrayDequeue (no null value in deque)</b>
    - If want to implement stack, perfer to use deque class
## Implement queue and deque
  - LinkedList
  - Circular array
