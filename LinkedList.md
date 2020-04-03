# LinkedList
  - value only be interger object not primitive type

## Create ListNode
    public class ListNode {
        public int value;
        public ListNode next;

        public ListNode(int value){
            this.value = value;
            this.next = null;
        }


## Abstract
             |_____________________Memory______________________| 
             |                                                 |   
             |       Stack                        Heap         |
             |    (references)                  (objects)      |
             |   |------------|            |----------------|  |
             |   |            |            |  _______       |  |
             |   | reference  |------------|->|value |      |  |
             |   |      .     |            |  |refer |      |  |
             |   |      .     |            |   -|----       |  |
             |   |      .     |            |    |   _____   |  |
             |   |____________|            |    -> |value|  |  |
             |                             |       |refer|  |  |
             |                             | _____  ---|-   |  |
             |                             || null|    |    |  |
             |                             ||_____| <--     |  |
             |                             |________________|  |
             |                                                 |
             |                                                 |
             |_________________________________________________| 
