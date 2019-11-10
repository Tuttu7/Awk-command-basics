#### I have a file name as testfile.txt with the following contents and I'm going to use the awk command to manipulate data.

```
root@tuttu-Inspiron:~# cat test.txt
Frank: neymar
Testing 1: testing1
Hello World: Hi world
TesT: Testing
123 Testing:679
```
#### Printing the values in everyline :
```
root@tuttu-Inspiron:~# awk '{ print }' test.txt 
Frank
Testing 1
Hello World
TesT
123 Testing
```
#### Printing the values in the first column :
```
root@tuttu-Inspiron:~# awk '{ print $1 }' test.txt 
Frank
Testing
Hello
TesT
123
```
#### Printing the values in the second column :
```
root@tuttu-Inspiron:~# awk '{ print $2 }' test.txt 

1
World

Testing
```
#### Printing the value named as Test in the given file :
```
root@tuttu-Inspiron:~# awk '/Test/ { print }' test.txt
Testing 1
123 Testing
```
#### Printing values using character classes :
```
root@tuttu-Inspiron:~# awk '/[a-z]/ { print }' test.txt
Frank
Testing 1
Hello World
TesT
123 Testing
```
#### Grab every line with numbers :
```
root@tuttu-Inspiron:~# awk '/[0-9]/  { print }' test.txt 
Testing 1
123 Testing
```
#### Grab every line that start with numbers :
```
root@tuttu-Inspiron:~# awk '/^[0-9]/ { print }' test.txt 
123 Testing
```
### Grab every line that end with numbers :
```
root@tuttu-Inspiron:~# awk '/[0-9]$/ { print }' test.txt 
Testing 1
```
### Grab every line that first coulmn mataches with value 123 :
```
root@tuttu-Inspiron:~# awk '{if ($1 ~ /123/) print}' test.txt 
123 Testing
```
### I'm adding more contents to my testfile.txt to illustrate the -F: parameterin the awk comand
```
root@tuttu-Inspiron:~# cat test.txt
Frank: neymar
Testing 1: testing1
Hello World: Hi world
TesT: Testing
```
### Overiding white spaces by adding -F: parameter 
```
root@tuttu-Inspiron:~# awk -F: '{ print $2 }' test.txt 
 neymar
 testing1
 Hi world
 Testing
 ```
