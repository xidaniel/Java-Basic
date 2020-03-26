## Basic Concepts:
  - <b>class</b>
  - <b>object(instance)</b>
  - <b>reference:</b> address of objects, likes name card save in stack
  - <b>dereference:</b> find object base on address
  - <b>Primitive data types:</b> no reference, data directly stored in memory
    - boolean, char, byte, short, int, long, float, double
  - <b>Class type:</b> stored in heap, operated by references
  - <b>Constructure:</b> a special method to initialize objects, must have the same name as the class
    - this: It is this object
  - <b>null:</b> An empty reference
  - <b>final:</b> constants "Once assigned, can not be changed"
    - final class: A class that can not be drived.
    - final method: A method that can not be overridden.
    - final field: A variable that once assigned, can not be assigned again.
  - <b>field</b>: attributes of class
  - <b>static:</b> Members (fields, methods, classes) belong to class, not object.
  - <b>public:</b> everyone can access
  - <b>private:</b> only myself can access
  - <b>protected:</b> only my children and same package can access
  - <b>default:</b> only the same package can access
  
  - Class name == File name : There can only be one public class per .java file.
  - public static void main(String[] args) is the main entrance of any java program
  - print: System.out.println()
 
## Working with Objects
e.g.
Creat object: Student firstStudent = new Student("Daniel")
  - Declaration : Student firstStudent
  - Instantiation: firstStudent = new Student()
  - Initialization: call to a constructor
  
## Parameter Passing
  - <b>Java is always pass by value(copy value)</b>
     - primitive type: copy of the value itself
     - objects: copy of the object reference
 
## Memory in Java
   - Stack: store references
   - Heap: store objects

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
