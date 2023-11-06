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

Reason:
The issue was that the reverseInPlace method was improperly swapping the values at the different indexes of the array, so the left hand side was being changed while the right wasn't, then the entire thing overlapped after the halfway point and the right hand side is filled with the wrong numbers. The fix just uses a simple temp varaible to store what the original arr[i] was, then it replaces both the right and left sides and doesn't do an extra pass by stopping at the halfway mark.


# Part 2

**Using the FIND command**

_Link for Find docs_
[Link](https://man7.org/linux/man-pages/man1/find.1.html)

_Link for random article "10 ways to use the Find command"_
[Link](https://www.redhat.com/sysadmin/linux-find-command)

*-name*

1.

```
gaspa@antwonlenovo MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)        
$ find technical -name "rr37.txt"
technical/biomed/rr37.txt
```

If you know the name of a file or don't know it's path you can use the find - name to search for it and have all directories containing it listed.

2.

```
gaspa@antwonlenovo MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)        
$ find technical -name "rr196.txt"
technical/biomed/rr196.txt
```

Another helpful thing about -name is that you can use *.txt or name.* to find all the related files or even directories that could be in different places, for the purpose of the lab and the hundreds of files I didn't paste it.

*-type*

1.

```
gaspa@antwonlenovo MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)        
$ find technical -type d
technical
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```

The type can be used to find different types of things in the main directory, in this case type -d finds all the directories that stem from technical including sub directories

2.

```
gaspa@antwonlenovo MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)        
$ find technical/government -type d
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
```

You can also use the type to find files, by using type -f, you can use this to list or output all the specific types of files you want, but there are too mant to list for this lab

*-path*

1.

```
gaspa@antwonlenovo MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)        
$ find technical -path "*rr37.txt*"
technical/biomed/rr37.txt
```

The path line argument finds the path to a specific input you specify in the directory you specify, so it finds the path to rr37.txt from technical, to its sub directory, then to the file, useful for finding a whole path

2.

```
gaspa@antwonlenovo MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)        
$ find technical -path "*commission_report.txt*"
technical/government/About_LSC/commission_report.txt
```

The path argument is a pretty linear command, it just returns the full path of a file or directory from the initially specified start point to the end point that comes after the command line argument, can be used for more than txt files

*-size*

1.

```
$ find technical -size -1k
technical
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```

The find size argument is very helpful because it can list all the files or directories that take up more or less tha the specified amount, in this case the listed things are all less than 1 kb

2.

```
gaspa@antwonlenovo MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)        
$ find technical -size +100k
technical/911report/chapter-1.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-3.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/biomed/1471-2105-3-2.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/State_Planning_Report.txt
technical/government/Env_Prot_Agen/bill.txt
technical/government/Env_Prot_Agen/ctm4-10.txt
technical/government/Env_Prot_Agen/multi102902.txt
technical/government/Env_Prot_Agen/tech_adden.txt
technical/government/Gen_Account_Office/ai9868.txt
technical/government/Gen_Account_Office/d01376g.txt
technical/government/Gen_Account_Office/d01591sp.txt
technical/government/Gen_Account_Office/d0269g.txt
technical/government/Gen_Account_Office/d02701.txt
technical/government/Gen_Account_Office/gg96118.txt
technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
technical/government/Gen_Account_Office/im814.txt
technical/government/Gen_Account_Office/May1998_ai98068.txt
technical/government/Gen_Account_Office/pe1019.txt
technical/government/Gen_Account_Office/Sept27-2002_d02966.txt
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt  
```

The size command line argument can also be used to find files that are greater than a certain amount, in this case it lists files greater than 100 kb, this could be helpful in clearing up space or trying to optimize storage





