#### Grep is a command-line utility that can search and filter text using a common regular expression syntax.

```
$ cat test2.txt 
I'm hoping to write a sample ltter
which contains the number of orders 
to be provisioned for the next week
a bunch of flowers for the shop
bunch.txt
txt.bunch
```
#### Sample output :

```
$ grep contains test2.txt
which contains the number of orders 
```

#### Output only the matching segment of each line, rather than the full contents of each matched line :

```
$ grep -o to test2.txt
to
to
```

#### Print the line number of each matched line :
```
$ grep -n to test2.txt
1:I'm hoping to write a sample ltter
3:to be provisioned for the next week
```
#### To highlight the matched search pattern, we can use ‘color’ with grep command :
```
$ grep --color bunch test2.txt
a bunch of flowers for the shop
bunch.txt
```

#### To print all the lines as output on screen which starts with the search pattern :
```
$ grep ^bunch test2.txt
bunch.txt
```
#### To print all the lines that end with the search pattern, use ‘$’ symbol :
```
$ grep bunch$ test2.txt
txt.bunch
```

#### You can use the grep command to print N number of lines before/after a search string from a file. The search result also includes the line of text containing the search string :

```
~$ grep -A 1 contains test2.txt
which contains the number of orders 
to be provisioned for the next week

$ grep -B 1 contains test2.txt
I'm hoping to write a sample ltter
which contains the number of orders 

$ grep -C 1 contains test2.txt
I'm hoping to write a sample ltter
which contains the number of orders 
to be provisioned for the next week
```

#### To display the results which matches the whole word :
```
~$ grep -w contain test2.txt
tuttu@tuttu-Inspiron:~$ 


$ grep -w contains test2.txt
which contains the number of orders
```

#### Example : 2

````
$ cat test3.txt
10.185.248.71 - - [09/Jan/2015:19:12:06 +0000] 808840 "GET /inventoryService/inventory/purchaseItem?userId=20253471&itemId=23434300 HTTP/1.1" 500 17 "-" "Apache-HttpClient/4.2.6 (java 1.5)"
10.78.243.12 - - [09/Jan/2015:20:12:06 +0000] 808840 "POST /inventoryService/inventory/purchaseItem?userId=20253471&itemId=23434300 HTTP/1.1" 200 17 "-" "Apache-HttpClient/4.2.6 (java 1.5)"
10.64.25.78 - - [09/Jan/2015:20:12:06 +0000] 808840 "POST /inventoryService/inventory/purchaseItem?userId=20253471&itemId=23434300 HTTP/1.1" 404 17 "-" "Apache-HttpClient/4.2.6 (java 1.5)"
10.73.87.90 - - [09/Jan/2015:20:12:06 +0000] 808840 "POST /inventoryService/inventory/purchaseItem?userId=20253471&itemId=23434300 HTTP/1.1" 404 17 "-" "Apache-HttpClient/4.2.6 (java 1.5)"
````

#### To get the output of the IP address of the visitor and the path of the requested file for successful requests :

````
$ grep -Eo "^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}.* 404" test3.txt
10.64.25.78 - - [09/Jan/2015:20:12:06 +0000] 808840 "POST /inventoryService/inventory/purchaseItem?userId=20253471&itemId=23434300 HTTP/1.1" 404
10.73.87.90 - - [09/Jan/2015:20:12:06 +0000] 808840 "POST /inventoryService/inventory/purchaseItem?userId=20253471&itemId=23434300 HTTP/1.1" 404
````

#### To get the outpout of the count of the unsuccessful attempts to access content (404) :

```
$ grep -Eoc "^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}.* 404" test3.txt
2
```

#### The following command generates a list of all IP addresses that have attempted to connect to your web server :

````
$ grep -Eo "^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}." test3.txt | uniq
10.185.248.71 
10.78.243.12 
10.64.25.78 
10.73.87.90
````

