# Weeks 4 & 5: Bugs and File System Navigation
## Part 1: Bugs
The method `reversed` in lab 4 is buggy; it yields error in testing.
- failure producing input: when we input the array `{5,6,7,8}`, the code returns an error
  ```
  @Test
  public void testReversed() {
    int[] input1 = {5,6,7,8};
    assertArratEquals(new int[]{8,7,6,5}
  }
  ```
- non failing input: inputting an array of zero makes it so the JUnit test does not fail; the code passes.
  ```
  @Test
  public void testReversed2(){
    int[] input1={0,0,0};
    assertArrayEquals(new int[]{0,0,0}, ArrayExamples.reversed(input1));
  }
  ```
- **the symptom:** error that value found is 0 when expected last number of input array thrown by testing reversed with an array of nonzero values; no error thrown for array of zeroes.
  ![Image](symptom.png)

- **the bug:** the bug lies in the array assignment and return. The reverse method is supposed to return an array with the values of the input array in reverse order, so the method creates a new array to do this, and the `for` loop is supposed to assign the values (from the last index to 0 index of the input array) to the new array from index 0 to the last index.
  **Buggy code before the fix**
  ```
   static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  ```
  **Code with bug fixed**
  ```
   static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  ```
  The bug is line `arr[i] = newArray[arr.length-i-1]`  and `return arr`! This means that the original array arr is being assigned with the values of newArray in reverse order rather than the other way around. However, `newArray` is just initialized within the method as a new int array with no arguments, so all its values are automatically zero. Thus, arr just gets populated with zeroes and returned, giving the “got 0” instead of the reversed array error. This is also why an input of an array with only zero values does not fail; the `newArray` returned is an array of the same length as the input array, also with only zero values.

##Part 2: Command Research
I choose to analyze special uses of the `grep` command.\
The standard use of the command follows the formula `grep <command> <file to search>`. Some of the command line options include:
- `grep -i `:  case insensitive search
- `grep -r`: recursive search through directories
- `grep -o`: displays only matching part of lines
- `grep -l`: display only file names of files with matching lines
