# Software Technology Experiment Assignment 2

### Technical problems

###### Application using JPA

I first had some errors while trying to run my main method. After a lot of struggling, I found out that I was running an instance of my database in a separate command window. My application was therefore not able to connect.

###### Banking/Credit Card example JPA

I had an error when using embedded classes. I first trid to set pincode as embeddable and embedd it into creditcard, but didn't work. I therefore converteded pincode to an entity and made an unidirectional one to one relationship with creditcard.

### Link to code

###### [Experiment 1: Application using JPA](https://github.com/oddhus/DAT250-experiment2-jpa)

###### [Experiment 2: Banking/Credit Card example JPA](https://github.com/oddhus/DAT250-experiment2-banking)

### Inspecting the database

It is possible to inspect the database by opening the derby interactive scripting tool ij and use SQL.

![Image of table inspection](https://github.com/oddhus/DAT250-reports/blob/master/images/db-inspection.jpg)

![Image of database overview](https://github.com/oddhus/DAT250-reports/blob/master/images/db-inspection2.jpg)

### Pending issues

I didn't manage to find a solution on how to use embedded classes and entites together.
