Avetis Gasparian Lab Report 2

## 1

**First Screenshot**

![Image](https://github.com/AntwonioG/cse15l-lab-reports/blob/main/screenshots/image%20(5).png)

A lot of the code is fluff due to it being a copy of the NumberServer we previously used, but the main components and values to keep track of are daString, and the query requests. In the first call originally daString is initialized to nothing aka "", after the query is put the code goes through the pathing. First it checks the slash, then continues, then checks the type of query in this case its "/add-message" then it checks if the parameters are right (if s is an s), lastly if all thats true it sets daString to what it was before + the new parameter + creates a new line, so the first call means ""(empty) + "hi+two" +"\n" new line. then prints it to the page

**Second Screenshot**

![Image](https://github.com/AntwonioG/cse15l-lab-reports/blob/main/screenshots/image%20(6).png)

For the next request it is almost completely the same except now when daString is made to equal itself + the parameters, there is actually something to add. This time it paths through the if statements checking if it's valid, then it sets daString to "hi+two" + "\n" + "(this one)"+ "\n" then returns it again.

**Code**
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    String daString = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Number: %d", num);
        } else if (url.getPath().equals("/increment")) {
            num += 1;
            return String.format("Number incremented!");
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    daString += parameters[1]+"\n";
                    return daString;
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

## 2

**Screenshot of pub key directory**

![image](https://github.com/AntwonioG/cse15l-lab-reports/blob/main/screenshots/image%20(7).png)


**Screenshot of priv key directory**

![image](https://github.com/AntwonioG/cse15l-lab-reports/blob/main/screenshots/image%20(8).png)


**Screenshot of pub key in ieng6**

![image](https://github.com/AntwonioG/cse15l-lab-reports/blob/main/screenshots/image%20(11).png)


**Screenshots of logging in**

![image](https://github.com/AntwonioG/cse15l-lab-reports/blob/main/screenshots/image%20(9).png)

![image](https://github.com/AntwonioG/cse15l-lab-reports/blob/main/screenshots/image%20(10).png)


## 3

It's difficult to write about what I learned because this lab has been a like a mystical journey for me. Things kept going wrong, I installed java on my computer and found that theres a difference between the JDK and JRE versions where one can compile .java files and the other can't. I also learned about how default vs code doesn't come with WSL so i couldn't do any linux commands ( touch specifically ) so i just had to log in to the ucsd server and use edstem to access the commands.
