Array Methods

I'll provide an example of a bug from week 4's lab and follow the requested format for a failure-inducing input, a non-failure-inducing input, symptoms, bug, and a code change to fix the issue. 

I'll consider a bug in a hypothetical Java program where a method to calculate the average of an array of integers, `averageWithoutLowest`, has a bug. The bug is that it does not correctly exclude the lowest element when calculating the average.

Failure-Inducing Input:

JUnit Test for the Bug:
```java
@Test
public void testReverseInPlace_Bug() {
    int[] inputArray = {1, 2, 3, 4, 5};
    ArrayExamples.reverseInPlace(inputArray);
    assertArrayEquals(new int[]{5, 4, 3, 2, 1}, inputArray);
}
```

JUnit Test for the no Bug:
```java
@Test
public void testReverseInPlace_Bug() {
    int[] inputArray = {1, 2, 3, 4, 5};
    ArrayExamples.reverseInPlace(inputArray);
    assertArrayEquals(new int[]{5, 4, 3, 2, 1}, inputArray);
}
```
Symptom:

With bug:

![Image](bug1.png)

No bug:
![Image](bug.png)
