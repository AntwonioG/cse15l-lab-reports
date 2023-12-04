# Lab Report 5

## Part 1

*Original Post*

Student: I'm having an issue compiling my program using a bash script test.sh, here is the error

![image](https://raw.githubusercontent.com/AntwonioG/cse15l-lab-reports/main/screenshots/Labrep5sc1.png)

*Response*

TA: I think you're doing it wrong, try not doing that. Also you need JUnit probably

*Learned*

I think I know the issue, I should just do it on VSCode without JUnit

![image](https://raw.githubusercontent.com/AntwonioG/cse15l-lab-reports/main/screenshots/Labrep5sc2.png)

*Last Part*

1. File structure contains ListExamples.java and TestListExamples.java with a test.sh file
2. Before fixing the bug
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index1 += 1;
    }
    return result;
  }


}
```
3. `test.sh`
4. Get JUnit to fix the bug
## Part 2

I think most of the labs really taught me something new, even the ones based around topics I have experience in had a little extra tips that definitely made me better overall. One really important thing this class and tutors helped me with was setting up my github and vscode because both those things are going to continue to be useful in the future, despite the rarer errors i experienced while doing so. Overall great class and I think it's a great crash course for people getting in to tech.
