**Part 1**

Failure Inducing Input:
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3 4 5 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```

Non-failure Inducing Input:
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```

Symptom: Before
![Image] (lab3/lab3p1.jpg)

Symptom: After
![Image] (lab3/lab3p2.jpg)

Bug: Before
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
    }
}
```

Bug: After
```
static void reverseInPlace(int[] arr) {
  int[] copyArr = arr.clone();
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = copyArr[arr.length - i - 1];
  }
}
```

The fix involves fixing the issue of `reverseInPlace` mirroring the back half of the original array due to the `reverseInPlace` calling elements within the array and changing elements of the same array. By creating a clone of the original array and changing the original array based on the indexes of the cloned and not the original array, the method no longer has the problem.
