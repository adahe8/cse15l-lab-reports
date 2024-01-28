# Week 2 & 3: URLs & Servers, VS Code and the Local Machine
## Lab 2 Blog

### Part 1: Building a Server

I drew from the NumberServer class we practiced with during lab section, the informational article linked in the NumberServer.java file, and JavaDoc to write the code for `ChatServer.java`.
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler{
    //state on the server
    String chat="";
    
    public String handleRequest(URI url) {
        if(url.getPath().equals("/")){
            return String.format("%s", chat);
        }else {
            if(url.getPath().contains("/add-message")){
                String[] info = url.getQuery().split("[&=]");
                String text = "";
                if(info[0].equals("s")){
                    text = info[1];
                    if(info[2].equals("user")){
                        chat += info[3] + ": " + text+"\n";
                        return String.format("%s",chat);
                    }
                }
            }
            return "404 not found";

        }
    }

}

public class ChatServer {
    public static void main(String[] args) throws IOException{
        if(args.length==0){
            System.out.println("Missing port number! Try any number between 1024 and 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
**Server in action:**\

