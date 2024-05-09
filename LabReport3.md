# Lab Report 3

## Part 1 - Bugs

1. A failure-inducing input for the buggy program
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
  int[] input2 = {1, 2, 3};
  ArrayExamples.reverseInPlace(input2);
  assertArrayEquals(new int[]{3, 2, 1}, input2);
}
```

2. An input that doesn't induce a failure
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```

3.The symptom, as the output of running the two tests above
* Test Fail Screenshot:

  ![Image](testFail.png)

* Test Pass Screenshot:

  ![Image](testPass.png)

4. The bug, as the before-and-after code change required to fix it
* before
```
static void reverseInPlace(int[] arr){
  for(int i = 0; i < arr.length; i += 1){
    arr[i] = arr[arr.length - i - 1];
  }
}
```
* after
```
static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[i];
    }
}
```
5. Briefly describe (2-3 sentences) why the fix addresses the issue.
   
## Part 2 - Researching Commands
* -c: This prints only a count of the lines that match a pattern.
```
audreyliu@Audreys-MacBook-Pro technical % grep -c -r "search" | head -n 5
./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt:0
./government/About_LSC/Progress_report.txt:4
./government/About_LSC/Strategic_report.txt:5
./government/About_LSC/Comments_on_semiannual.txt:0
./government/About_LSC/Special_report_to_congress.txt:1
```



Source: https://www.geeksforgeeks.org/grep-command-in-unixlinux/
