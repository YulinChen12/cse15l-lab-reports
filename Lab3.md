Array Methods

I'll provide an example of a bug from week 4's lab and follow the requested format for a failure-inducing input, a non-failure-inducing input, symptoms, bug, and a code change to fix the issue. 

I'll consider a bug in a hypothetical Java program where a method to calculate the average of an array of integers, `averageWithoutLowest`, has a bug. The bug is that it does not correctly exclude the lowest element when calculating the average.


JUnit Test for the Bug:

@Test
public void testAverageWithoutLowest_Bug() {
    int[] inputArray = {4, 7, 2, 9, 1};
    double result = SomeClass.averageWithoutLowest(inputArray);
    assertEquals(5.75, result, 0.01);
}
