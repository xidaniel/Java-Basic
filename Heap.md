# Heap Data Structure

## Property
  - It is a complete tree
  - left and right donot have realationships
  - can be converted to an array
  - left_index = parent_index * 2 + 1
  - right_index = parent_index * 2 + 2
  - parent_index = (left/right index - 1) / 2
  
## Operations
  - offer()  O(logn)
    - percolateUp
  - poll()  O(logn)
    - percolateDown
  - <b>heapify</b>
    - Do percolateDown O(n)
      - Start at first non-leaf node (From bottom to up and right to left)
      - Find the last node  = ((n - 1) - 1) / 2 = n/2 - 1 (Just need to heapify every sub-heap in range [0, n/2-1])

                        Level 0            10
                        Level 1        11       7 
                        Level 2      2    8   4   6 
                        Level 3   13   1
                                  (k level full tree, n total number of nodes: 2^k - 1)
      - Time Complexity analyze:
        - 1 * 2^(k-2) + 2 * 2^(k-3) + 3 * 2^(k-4) + ... + (k-2) * 2^1 + (k-1)*2^0 = O(n)
        
    - Do percolateUp  O(nlogn)
      - S = 0 * 2^0 + 1 * 2^1 + 2 * 2^2 + ... + (h-1) * 2^(h-1) = O(h * 2^h) = O(logn * n) = O(nlogn)
      
## Heap Sort (Unstable sort)
  - Not suitable for industrial use (cannot use distribution system and parallel computing) 
  - Time Complexity: O(nlogn)
  - Space Complexity: O(1)
