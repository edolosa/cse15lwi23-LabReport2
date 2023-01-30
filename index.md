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

![Image](https://media.discordapp.net/attachments/717860504093327450/1068680518746513418/image.png)

Similarly to the last input, we are calling upon the method handleRequest() and the helper method within it,
incrementList(), however, we are using the argument "/add-message?s=Journey Heavensward". Although incrementList()
is called, it doesn't actually change anything within the code because the condition set inside it (size < list.length/1.2)
is false.

After the code runs:

```
list = {"Hello!", "Journey Heavensward", null, null, null}

size == 2
```

## Part 2: Symptoms and Bugs

Failure inducing input for buggy reverseInPlace() :

```
@Test
  public void testReversedSmall() {
    int[] input1 = {1, 2, 3};
    assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input1));
  }
```

Non-Failure inducing input for buggy reverseInPlace() :

```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```

Symptom of running the two tests:

![Image](https://media.discordapp.net/attachments/717860504093327450/1069714019851702323/image.png)

Buggy reverseInPlace() :

```
// Changes the input array to be in reversed order
static void reverseInPlace(int[] arr) {
  for (int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - 1 - i];
  }
}
```

After code change:

```
// Changes the input array to be in reversed order
static void reverseInPlace(int[] arr) {
  int[] copy = new int[arr.length];
  for(int i = 0; i < arr.length; i++) {
    copy[i] = arr[i];
  }
  for(int i = 0; i < arr.length; i++) {
    arr[i] = copy[arr.length - 1 - i];
  }
}
```

The reason that this code change addresses the issue of the buggy reverseInPlace() is that in the original version,
we were changing arr with the contents of arr. This meant that as we were changing the elements that we wanted to
refer to when we "reverse" the elements. With the code change, we point towards a copy of the inital array so that
when we change the contents within the array, we can still refer to the original values of the array within the copy.

## Part 3 - Closing statements

One thing I learned from these past two weeks was how to fork a repository on github. I have used github before for downloading things
for my video games, but this is the first time I have been using it as a creater and editor. Rather than downloading the contents on github,
I can now create repositories of my own and edit them as I choose with forking.
