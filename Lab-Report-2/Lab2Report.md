# **Lab Report 2** #
---
There are three parts to this lab.
---
## Part 1 ##
---
The first part is to write a web server called `StringServer` that should keep track of a single string that gets added to by incoming requests.
Using the given code from lab two and my own implementation, I have the code for `StringServer.java` below
---
```
//Part 1 of The Lab 

import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    ArrayList<String> arr = new ArrayList<>();
    
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return makeString(arr);
        }
        else if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            arr.add(parameters[1]);
            return makeString(arr);
        }
        return "404 Not Found!";
    }

    // concatenate a new line (\n) and the string after = to the running string, 
    //and then respond with the entire string so far

    public String makeString(ArrayList<String> arr) {
        String str = "";

        for (int i = 0; i < arr.size(); i++) {
            str = str + arr.get(i) + "\n";
        }

        return str;
    }
}

//Similar to given code from NumberServer.java

public class StringServer {
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
---
When ran with `Server.java`, `StringServer.java` creates an online server that is able to store and display strings. 
Inputting specific paths allows strings to be added and displayed on the site.
- Here is two screenshots using `/add-message`

- Which methods in your code are called?
- What are the relevant arguments to those methods, and the values of any relevant fields of the class?
- How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

- Which methods in your code are called?
- What are the relevant arguments to those methods, and the values of any relevant fields of the class?
- How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.



