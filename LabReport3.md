# Part 1

**Failure inducing input**

```
public void testReverseInPlace() {
    int[] input1 = { 3,4,5,6,7,8 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 8,7,6,5,4,3 }, input1);
	}
```


**Input without failure**

```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```


**The symptom**

![image](https://raw.githubusercontent.com/AntwonioG/cse15l-lab-reports/main/screenshots/image.png)

**The bug**

Before:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length-i-1];
      arr[arr.length-i-1]=temp;
    }
  }
```


# Part 2
