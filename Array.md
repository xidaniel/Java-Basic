# Array in Java
## Occupies consecutive memory and the elements in the array can be referenced via the index in O(1) time.
- Create array:
   - int[] array = <b>new</b> int[3]; // {0,0,0}
   - int[] array = {1,2,3};  // {1,2,3}
   - int[] array = new int[]{1,2,3,4,5};  // {1,2,3,4,5} 
- Arrays are objects
  - each of the arrays created is an instance of that class
             
             |_____________________Memory______________________| 
             |                                                 |   
             |       Stack                        Heap         |
             |    (references)                  (objects)      |
             |   |------------|            |----------------|  |
             |   |            |            |  ____________  |  |
             |   |int[] array |------------|->|  {0,0,0}  | |  |
             |   |      .     |            |  |length = 3 | |  |
             |   |      .     |            |  |___________| |  |
             |   |      .     |            |       .        |  |
             |   |____________|            |       .        |  |
             |                             |       .        |  |
             |                             |       .        |  |
             |                             |________________|  |
             |                                                 |
             |                                                 |
             |_________________________________________________| 
 
 - Arrays vs. array
   - Arrays is helper class
 - "length" is a field of the array object
 - array length can not be changed after the array object is created.(final)
 
 
 ## Coding example. SelectionSort

______________________________________________________________________________________
   public class SelectionSort {

       public int[] sort(int[] array){
           if (array == null || array.length <= 1){
               return array;
           }

           for (int i = 0; i < array.length; i++){
               int globalMin = i;
               for(int j = i + 1; j < array.length; j++){
                   if (array[j] < array[globalMin]){
                       globalMin = j;
                   }
               }
               swap(array, i, globalMin);
           }
           return array;
       }

       private void swap(int[] array, int i, int j){
           int temp = array[i];
           array[i] = array[j];
           array[j] = temp;

       }

       public static void main(String[] args){
           int[] array = {4,2,3,7,8,5,1};
           SelectionSort ob = new SelectionSort();
           int [] ans = ob.sort(array);
           System.out.println(Arrays.toString(ans));
       }
   }
____________________________________________________________________________________
