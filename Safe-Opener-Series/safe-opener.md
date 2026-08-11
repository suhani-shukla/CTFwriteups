# Safe Opener

## Challenge
Reverse engineering challenge — a Java program (`SafeOpener.java`) checks an entered password against a hardcoded base64-encoded string. Recover the password and wrap it in the picoCTF flag format.

## Hints
TODO

## Solution
Read through `SafeOpener.java`:

```java
import java.io.*;
import java.util.*;  
public class SafeOpener {
    public static void main(String args[]) throws IOException {
        BufferedReader keyboard = new BufferedReader(new InputStreamReader(System.in));
        Base64.Encoder encoder = Base64.getEncoder();
        String encodedkey = "";
        String key = "";
        int i = 0;
        boolean isOpen;
        

        while (i < 3) {
            System.out.print("Enter password for the safe: ");
            key = keyboard.readLine();

            encodedkey = encoder.encodeToString(key.getBytes());
            System.out.println(encodedkey);
              
            isOpen = openSafe(encodedkey);
            if (!isOpen) {
                System.out.println("You have  " + (2 - i) + " attempt(s) left");
                i++;
                continue;
            }
            break;
        }
    }
    
    public static boolean openSafe(String password) {
        String encodedkey = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz";
        
        if (password.equals(encodedkey)) {
            System.out.println("Sesame open");
            return true;
        }
        else {
            System.out.println("Password is incorrect\n");
            return false;
        }
    }
}
```

The program base64-encodes whatever you type and compares it against a hardcoded encoded string (`cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz`) — no need to guess passwords or run it three times, just base64-decode that hardcoded value directly:

```bash
echo "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz" | base64 -d
```
```
pl3as3_l3t_m3_1nt0_th3_saf3
```

## Flag
```
picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
```