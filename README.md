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
#### Printing the line with the word "Test" in the given file :
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
#### Grab every line that end with numbers :
```
root@tuttu-Inspiron:~# awk '/[0-9]$/ { print }' test.txt 
Testing 1
```
#### Grab every line that first coulmn mataches with value 123 :
```
root@tuttu-Inspiron:~# awk '{if ($1 ~ /123/) print}' test.txt 
123 Testing
```
#### I'm adding more contents to my testfile.txt to illustrate the -F: parameter in the awk comand
```
root@tuttu-Inspiron:~# cat test.txt
Frank: neymar
Testing 1: testing1
Hello World: Hi world
TesT: Testing
```
#### Overiding white spaces by adding -F: parameter 
```
root@tuttu-Inspiron:~# awk -F: '{ print $2 }' test.txt 
 neymar
 testing1
 Hi world
 Testing
 ```
 #### Example 2 :
#### My testfile.txt contents :
```
~$ cat test.txt
test,red,white,black,1000,2
123,758,brown,large,3000,3
300,400,700,800,4000,67
test,bkm,apple,cake,880,1
```
#### Printing line only with the values 400 and brown :
```
$ awk '/400|brown/' test.txt
123,758,brown,large
300,400,700,800
```
#### Adding the contents in the specific column and add the total :
```
$ awk -F "," '{x+=$2} END { print x }' test.txt
1158
~$ awk -F "," '{x+=$5} END { print x }' test.txt 
8000
```
#### Adding the contents in the specific column and displaying the total :
```
$ awk -F"," '{x+=$5;y+=$6;print} END{print"Total,"x,y}' test.txt
test,red,white,black,1000,2
123,758,brown,large,3000,3
300,400,700,800,4000,67
yrc,bkm,apple,cake,880,1
Total,8880 73
```
#### To find the count of entries repeated in every column :
```
$ awk -F, '{a[$1]++;}END{for(i in a)print i, a[i];}' test.txt 
123 1
300 1
test 2
```
#### In this exapmle the word 'test' is occuring twice so using this command test is displsyed only once by rejecting the second occurance.
```
$ awk -F, '!a[$1]++' test.txt
test,red,white,black,1000,2
123,758,brown,large,3000,3
300,400,700,800,4000,67
```
 
