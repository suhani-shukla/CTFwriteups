# Nice netcat

## Challenge
Connect to a program that "doesn't speak English" using `nc wily-courier.picoctf.net 54920`.

## Hints
1. Practice using netcat with the picoGym problem "what's a netcat?"
2. Practice reading and writing ASCII with the picoGym problem "Let's Warm Up".

## Solution
1. Connected to the service using `nc`:
```
   nc wily-courier.picoctf.net 54920
```
2. The service responded with a sequence of space-separated decimal numbers instead of plain text:
```
   112 105 99 111 67 84 70 123 103 48 48 100 95 107 49 116 116 121 33 95 110 49 99 51 95 107 49 116 116 121 33 95 49 57 53 102 101 125 10
```
3. Recognized these as ASCII character codes and converted them to text using `awk`:
```
   echo "112 105 99 111 67 84 70 123 103 48 48 100 95 107 49 116 116 121 33 95 110 49 99 51 95 107 49 116 116 121 33 95 49 57 53 102 101 125" | awk '{for(i=1;i<=NF;i++) printf "%c",$i; print ""}'
```
4. The conversion produced the flag directly.

## Flag
```
picoCTF{g00d_k1tty!_n1c3_k1tty!_195fe}
```