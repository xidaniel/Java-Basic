# Array in Java
## Occupies consecutive memory and the elements in the array can be referenced via the index in O(1) time.
- Create array:
   - int[] array = new int[3]; // {0,0,0}
   - int[] array = {1,2,3};  // {1,2,3}
   - int[] array = new int[]{1,2,3,4,5};  // {1,2,3,4,5} 
- Arrays are objects
             
             |___________________Memory________________________| 
             |                                                 |   
             |        Stack                       Heap         |
             |   |------------|            |----------------|  |
             |   |            |            |  ____________  |  |
             |   |int[] array |------------|->|  {0,0,0}  | |  |
             |   |            |            |  |length = 3 | |  |
             |   |            |            |  |___________| |  |
             |   |            |            |                |  |
             |   |____________|            |________________|  |
             |                                                 |
             |_________________________________________________| 
