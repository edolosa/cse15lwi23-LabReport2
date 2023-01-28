# **Lab Report 2 - Servers and Bugs**
***

## Part 1 - String Server

The Code for StringServer.java:

![Image](https://media.discordapp.net/attachments/717860504093327450/1068679750639427615/image.png?width=643&height=663)

![Image](https://media.discordapp.net/attachments/717860504093327450/1068679884890722374/image.png?width=856&height=663)

Command Inputs:

![Image](https://media.discordapp.net/attachments/717860504093327450/1068680299178885141/image.png)

In this image, we are calling upon the method handleRequest() with the argument "/add-message?s=Hello!".
Within this method is the helper method incrementList() which is a no args helper method that allows me
to increase the size of the string list if it goes over 80% of its capacity.

Furthermore, while we are running the method handleRequest() we add a value to the variable "list" and we
incremented the value of the variable "size" by 1. The variable "list" and "size" is for the list of strings
that the user puts in and the amount of strings in the list respectively.

```
list = {"Hello!", null, null, null, null}

size == 1
```

![Image] (https://media.discordapp.net/attachments/717860504093327450/1068680518746513418/image.png)

Similarly to the last input, we are calling upon the method handleRequest() and the helper method within it,
incrementList(), however, we are using the argument "/add-message?s=Journey Heavensward". Although incrementList()
is called, it doesn't actually change anything within the code because the condition set inside it (size < list.length/1.2)
is false.

After the code runs:

```
list = {"Hello!", "Journey Heavensward", null, null, null}

size == 2
```
