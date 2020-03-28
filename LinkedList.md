# LinkedList

## Create ListNode
    public class ListNode {
        public int value;
        public ListNode next;

        public ListNode(int value){
            this.value = value;
            this.next = null;
        }
    }


## Lists(Arraylist, LinkedList) semantic
  - An ordered collection(sequence)
  - Lists can contain duplicate elements
  - List interface: 
    - It has methods declared without implementation
    - We cannot instantiate an object by interface, because there is no implemented method in it.
    
          interface Dictionary{
            public integer get(int index);
          }

          class DictionaryImpl implements Dictonary{
            public interger get(int index){
            }
          }
