SOLID Principle:

**1. Single Responsibility:**

![img_89.png](images/img_89.png)

Bad example:

Putting all operations in the OrderService class:

createOrder(), processPayment(), sendEmail(), generateInvoice()

![img_90.png](images/img_90.png)

- reduces redability
- creates conflicts between devs
- Unit tests needs to be changed again and again

Solution:
- create separate service classes for each function.
- Every class should have only single reason to change.

![img_91.png](images/img_91.png)

**2. Open Closed Principle:**

![img_92.png](images/img_92.png)

Example:

Initially we have a method for processing UPI payments only.

![img_93.png](images/img_93.png)


- We want to add more payment methods, we are adding new code to the existing class having UPI functionality already 
tested. This introduces uncertainity as it can break what is working
- we should not change existing class to add new functionality


fix: Keep abstraction

make payment interface and implement different payments methods by extending from the parent class.
![img_95.png](images/img_95.png)

![img_94.png](images/img_94.png)


**3. Liskov Substitution Principle:**

![img_96.png](images/img_96.png)

-Child1 and Child2 inherit Parent and have their own methods
![img_98.png](images/img_98.png)

- Now if class client method receives parent as an argument it should work even if we pass child object which is inheritance
behaviour
- So why do we need Liskov principle

![img_99.png](images/img_99.png)

![img_100.png](images/img_100.png)

![img_101.png](images/img_101.png)

![img_102.png](images/img_102.png)

![img_103.png](images/img_103.png)

Main:
![img_104.png](images/img_104.png)

Output: no issue

![img_105.png](images/img_105.png)

**scenario**: crypto implements payment interface, but it does not support the refund method

![img_106.png](images/img_106.png)

A child class can add a functionality without issue, but when it tries to reduce a functionality given 
in the parent class that caused an issue.

On passing crypto object to client we get error:

![img_107.png](images/img_107.png)

Since client is talking to interface only and it expects all methods to work.
Crypto should never be a child class of payment 

Solution there should be a interface NonrefundablePayments.
![img_108.png](images/img_108.png)

Crypto now implements NonrefundablePayments:

![img_109.png](images/img_109.png)

make Payment extend NonrefundablePayments and remove pay method as it will be given in NonrefundablePayments interface.

![img_110.png](images/img_110.png)

![img_111.png](images/img_111.png)

![img_112.png](images/img_112.png)

**4. Interface Segregation Principle:**

![img_113.png](images/img_113.png)

84



