![img.png](img.png)

- used when object creation is heavy task.
- prototype allows us to create the object once and simply clone it when required instead of 
creating the object again and again.
- improves performance and saves time.

Ways to implement in Java:

**Copy Constructor:**
- create new object by copying data of existing object

example: In games we have bot payers, trees and cars that look alike.

![img_1.png](img_1.png)

- In the main class we have created 5 objects
- upon execution total execution time is > 10 s
![img_2.png](img_2.png)

To reduce this time we implement the prototype pattern:
- Create copy constructor, make it private to not be able to call from outside
![img_3.png](img_3.png)

- Create a clonnable interface
![img_5.png](img_5.png)

make gamebot class implement this interface and implement the customizedClone() method
![img_7.png](img_7.png)

- this refers to the current object ( object that is calling the customizedClone() method)
- gbc1 is the new object created
- gbc2 calls the clone method and passed the the gbc1 obj
- this refers to gbc1 in the constructor and returns a copy of this object.
- point to be noted is that the heavy constructor containing characters and animations was never called.

![img_8.png](img_8.png)

- Clone and print all the objects:
![img_9.png](img_9.png)

![img_10.png](img_10.png)

- All the characters are bot1

**How to allow/change different values of fields in prototype pattern**

- add setter methods in the class
- 
![img_12.png](img_12.png)
![img_11.png](img_11.png)

**Shallow copy vs Deep copy**
![img_14.png](img_14.png)

- what we implemented is shallow copy dealing with primitive types
![img_15.png](img_15.png)
- problem arises with mutable fields - List or reference of another class.

![img_16.png](img_16.png)

added sniper in bot5 weapon adds it everywhere.
![img_17.png](img_17.png)
![img_18.png](img_18.png)

![img_19.png](img_19.png)

- Deep copy implementation
- everytime a clone is created a new memory localtion is allocated although the value is same as the original object

![img_20.png](img_20.png)

