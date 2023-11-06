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

![Image](bug2.png)

No bug:
![Image](bug.png)

Fix the bug:

The code before with the bug is 

```java
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

The correct code should be:
```java
static void reverseInPlace(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[n - i - 1];
        arr[n - i - 1] = temp;
    }
}
```

Explanation:

The fix addresses the issue by ensuring that the division in the average calculation is performed as double division. In the buggy code, integer division was used, which resulted in truncating the fractional part and causing incorrect results. By changing (array.length - 1) to (array.length - 1.0), we ensure that the division is done in double precision, providing accurate averages that exclude the lowest element.
