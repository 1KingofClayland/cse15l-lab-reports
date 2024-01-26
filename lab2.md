**Part 1**
Code:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class ChatServerHandler implements URLHandler{
    String handleRequest(URI url){
        if (url.getPath().equals("/add-message")){
            String[] parameters = url.getQuery().split("&");
            String output = parameters[1].substring(2)+": "+parameters[0].substring(5)+"\n";
            return output;
        }
    }
}
class ChatServer{
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new ChatServerHandler());
    }
}
```

Output:

**Part 2**
Output:

**Part 3**
During the labs in week 2 and week 3 I learned about creating web servers and learning how to run them. I learned the backend of creating web servers through creating java classes that take in the URL link and are able to execute functions/commands through taking in the path and query. I also learned about running web servers through creating a port for the server to run on.
