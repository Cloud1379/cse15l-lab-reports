James Goodwin
1/30/23
Lab Report 2

# Part 1
StringServer code:
<br>
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    
    ArrayList<String> strings = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            String stringList = "";
            for(int i = 0; i < strings.size(); i++){
                stringList += strings.get(i);
                stringList += "\n";
            }
            return stringList;
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    strings.add(parameters[1]);
                    String stringList = "";
                    for(int i = 0; i < strings.size(); i++){
                        stringList += strings.get(i);
                        stringList += "\n";
                    }
                    return stringList;
                }
            }
        }
        return "404 Not Found!";
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
<br>
![Image](https://i.imgur.com/fGq3yRc.png)
<br>
In this screenshot, the methods handleRequest and main are called. The relevant arguments are "Hello" which is the messsage being added, "/add-message" to 
signify that a string is being added, "=" to split up the parameters, and "s" to represent the first parameter. There is also the entire url, which is 
http://localhost:4000/add-message?s=Hello In this class, I have an arrayList of strings, and in this screenshot "Hello" is being added to the end of it. 
This arrayList is then copied over to a single string with multiple lines and returned. In this case, since only "Hello" has been added so far, only "Hello" 
shows up on the screen. 
<br>
![Image](https://i.imgur.com/PZrtBIq.png)
<br>
In this screenshot, the methods handleRequest and main are called. The relevant arguments are "How are you" which is the messsage being added, 
"/add-message" to signify that a string is being added, "=" to split up the parameters, and "s" to represent the first parameter. There is also the entire 
url, which is http://localhost:4000/add-message?s=How%20are%20you In this class, I have an arrayList of strings, and in this screenshot "How are you" is 
being added to the end of it. This arrayList is then copied over to a single string with multiple lines and returned. In this case, now there are two items in the arrayList, "Hello" and "How are you" so both of them are shown on the screen. 
<br>
# Part 2
I have chosen the method reverseInPlace in the file ArrayExamples.java. Here is a failure-inducing input:
```
@Test 
public void testReverseInPlaceUnequalValues() {
  int[] unequalValueInput = { 0, 2, 4, 6, 8, 10 };
  ArrayExamples.reverseInPlace(unequalValueInput);
  assertArrayEquals(new int[]{ 10, 8, 6, 4, 2, 0 }, unequalValueInput);
}
```
<br>
Here is an input that doesn't induce error:
```
@Test 
public void testReverseInPlaceSymmetricValues() {
  int[] symmetricValueInput = { 0, 1, 2, 1, 0 };
  ArrayExamples.reverseInPlace(symmetricValueInput);
  assertArrayEquals(new int[]{ 0, 1, 2, 1, 0 }, symmetricValueInput);
}
```
<br>
The symptom of running the two tests:
![Image](https://i.imgur.com/ZjheVey.png)
<br>
Code before fixing:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
<br>
Code after fixing:
```
static void reverseInPlace(int[] arr) {
    int[] arrCopy = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arrCopy[i] = arr[arr.length - i - 1];
    }
    arr = arrCopy;
  }
```
<br>
The most interesting thing that I learned was how to set up a server. I learned how to get the path and the query in order to change the site according
to the inputs in the path.
