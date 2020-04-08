# PriorityQueue
## Method

| Operation| Time Complexity |  
|---------|-----------|
| offer()  |   O(logn)  |
| poll()   |   O(logn)  |
| peek()   |   O(1)     |
| size()   |   O(1)     |
| isEmpty()|  O(1)      |

## Comparable interface vs Comparator interface
  - comparable interface is natural order in calss
  - we can restructure order by creat comparator interface
  
  
## KSmallest
  - Analyze minHeap and maxHeap
    - Time complexity:
      - minHeap: O((n + k)logn)
      - maxHeap: O((n + k)logk)
    - Space complexity:
      - minHeap: O(n)
      - maxHeap: O(k)
    - Conclusion:
      - n == k, either is ok
      - n > k, maxheap is better
  - minHeap coding
  
        public class KSmallest {
          public int[] KSmallestMin(int[] array, int k){
              if (array.length == 0 || k == 0){
                  return new int[0];
              }
              PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>();
              for (int i = 0; i < array.length; i++){
                  minHeap.offer(array[i]);
              }
              int[] result = new int[k];
              for (int j = 0; j < k; j++){
                  result[j] = minHeap.poll();
              }
              return result;
          }
        }

  - maxHeap coding
  
        public class KSmallest {
          public int[] KSmallestMax(int[] array, int k){
          if (array.length == 0 || k == 0){
              return new int[0];
          }
          PriorityQueue<Integer> maxHeap = new PriorityQueue<Integer>(Collections.reverseOrder());
          for (int i = 0; i < array.length; i++){
              if (i < k){
                  maxHeap.offer(array[i]);
              } else if (array[i] < maxHeap.peek()){
                  maxHeap.poll();
                  maxHeap.offer(array[i]);
              }
          }
          int[] result = new int[k];
          for (int i = k - 1; i >= 0; i--){
              result[i] = maxHeap.poll();
          }
          return result;
          }
        }
  
