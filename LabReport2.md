Avetis Gasparian Lab Report 2

## 1

**First Screenshot**
![Image](https://media.discordapp.net/attachments/1087096047064588378/1165825388786761839/image.png?ex=65484280&is=6535cd80&hm=8c558212812775abe194442615e52da8f143cc68e61b00479e51a1db9120f4d9&=&width=978&height=112)

A lot of the code is fluff due to it being a copy of the NumberServer we previously used, but the main components and values to keep track of are daString, and the query requests. In the first call originally daString is initialized to nothing aka "", after the query is put the code goes through the pathing. First it checks the slash, then continues, then checks the type of query in this case its "/add-message" then it checks if the parameters are right (if s is an s), lastly if all thats true it sets daString to what it was before + the new parameter + creates a new line, so the first call means ""(empty) + "hi+two" +"\n" new line. then prints it to the page

**Second Screenshot**
![Image](https://media.discordapp.net/attachments/1087096047064588378/1165824231909621821/image.pngex=6548416c&is=6535cc6c&hm=6c57de0f8c0d0b23c39d2c039632c71f531c98c3e1e1ca5912e6f6090d3db91c&=&width=1342&height=208)

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

**Screenshot of pub and priv key directories**

![image](https://media.discordapp.net/attachments/1087096047064588378/1165828622435754004/image.pngex=65484583&is=6535d083&hm=d08515f42d3a6272656bd4a18e3f667823d55358d16515401fe1c842e50f0940&=&width=866&height=716)

**Screenshot of logging in**

![image](https://media.discordapp.net/attachments/1087096047064588378/1165833756016398396/image.pngex=65484a4b&is=6535d54b&hm=75bae627bc9c83e01f7c2d5bdb8162ec66d9980ec8fd8083ff3b3c1997e32953&=&width=1262&height=397)

## 3

It's difficult to write about what I learned because this lab has been a like a mystical journey for me. Things kept going wrong, I installed java on my computer and found that theres a difference between the JDK and JRE versions where one can compile .java files and the other can't. I also learned about how default vs code doesn't come with WSL so i couldn't do any linux commands ( touch specifically ) so i just had to log in to the ucsd server and use edstem to access the commands.
