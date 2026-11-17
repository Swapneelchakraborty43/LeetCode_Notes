Definition

![img.png](img.png)

- We have a interface that multiple classes are implementing
- Client should not be creating the object instead we introduce a factory class that will
define the object creation logic for these clients
- Ex Food delivery app and there is a notification flow with two classes sma and email
- After Order is placed sms and email is sent from Order service itself
- ![img_1.png](img_1.png)
- problem is code is tightly coupled and adding new functionality will create change in the existing code
- Create interface Notification and make both the classes(Email and SMS) implement this interface
- ![img_2.png](img_2.png)
- New implementatiom
- ![img_3.png](img_3.png)
- still object creation logic shouls not be there in the client class
- if some other class is sending notification then tne same logic need to be written agian leading to code duplicacy
- Create notificationFactory
![img_5.png](img_5.png)

- changes in client, Order service will directly use NotificationFactory which will give the object
- ![img_7.png](img_7.png)

- Incase client wants both the notification email and sms
- add a method that accepts a list of notification types and returns object based on each type
- ![img_10.png](img_10.png)

![img_11.png](img_11.png)

