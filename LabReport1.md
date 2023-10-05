Avetis Gasparian Lab Report 1 (I love Kendrick lamar)
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$ cd lecture1/
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$ 
```

1. the first cd takes you from lecture1 to home because a directory wasn't listed and its not an error
2. the second cd takes you from home to lecture1 directory because that was specified, its not an error
3. the third cd starts in lecture1 and has an error because you passed it a file instead of a directory, which is not allowed


```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ ls messages/
en-ca.txt  en-uk.txt  en-us.txt  es-mx.txt  zh-cn.txt
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
[user@sahara ~/lecture1]$ 
```

1. the first ls is in the lecture1 directory so it lists all the folders and files stored there, there is no error
2. the second ls is starting in lecture1 but listing the files inside of the messages directory, there is no error because you pass it a folders name and that folder is within the current directory
3. the third ls starts in lecture1 and returns the name of the file you pass it because ls is supposed to list things inside of directories, so theres an error since you pass it a non directory

```
[user@sahara ~/lecture1]$ cat
^Z
[2]+  Stopped                 cat
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
[user@sahara ~/lecture1]$ cat README 
To use this program:

javac Hello.java
java Hello messages/en-us.txt
```

1. the first cat starts in the lecture1 directory and breaks the program because it wasn't passed any arguments so it's trying to open nothing and infinitely trying until you cancel the request, so its an error
2. the second cat starts in lecture1 and realizes that passing it a directory instead of a file isn't allowed so it displays "not a directory" and is an error, but it doesn't break everything
3. the third cat starts in lecture1 and works properly because it is passed a file that can be found in the lecture1 directory, so the result is the stuff in README and there is no error
