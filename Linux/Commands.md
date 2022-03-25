# Linux Assignment
---------------------------------------------------------------------

## curl -s http://public-dns.info/nameserver/br.csv | cut -d, -f1 | shuf | tail -n 50 | xargs -i timeout 1 ping -c1 -w 1 {} | grep "time=" | awk '{print substr($7, 6, length($7)) " " substr($4, 1, length($4) -1)}' | sort -n | awk '{print $2 " " $1 "ms"}' | head -n 10

## curl -s http://public-dns.info/nameserver/br.csv

cURL, which stands for client URL, is a command line tool that developers use to transfer data to and from a server.

-s --> silent mode i.e. It doesn't show any progessbar or progress indicators.

 http://public-dns.info/nameserver/br.csv -> url to transfer data
 
![Screenshot from 2022-03-24 21-03-26](https://user-images.githubusercontent.com/59451084/159953281-9ee2ce77-f9f5-4f1c-8f8b-4c398405c939.png)

## cut -d, -f1

    The cut command is a command-line utility for cutting sections from each line of a file. It writes the result to the standard output. 
    It's worth noting that it does not modify the file, but only works on a copy of the content.
-d option means that the default delimiter is the tab character. here delimiter is ,
returns back the 1st field(-f1).

![Screenshot from 2022-03-24 21-08-53](https://user-images.githubusercontent.com/59451084/159955196-c9edd695-4d99-44fd-a2c4-04b682c64d22.png)

## shuf

The shuf command in Linux writes a random permutation of the input lines to standard output. It pseudo randomizes an input in the same way as the cards are shuffled.

![Screenshot from 2022-03-24 21-11-03](https://user-images.githubusercontent.com/59451084/159955171-b3aca848-7d88-4412-bdac-5e6f5ad035f8.png)

## tail -n 50

print the last N number of data of the given input. where N is 50

![Screenshot from 2022-03-24 21-15-54](https://user-images.githubusercontent.com/59451084/159955699-a26faf78-4c9f-4e90-8581-1a9a7d7f340e.png)

## xargs -i timeout 1 ping -c1 -w 1 {}

xargs -> reads streams of data from standard input, then generates and executes command lines; meaning it can take output of a command and passes it as argument of another command
-i →  The -I option changes the way the new command lines are built. Instead of adding as many arguments as possible at a time, xargs will take one name at a time from its input, look for the given token ({} here) and replace that with the name.
timeout 1 →  Start COMMAND, and kill it if still running after DURATION. of 1 second
ping → check the network connectivity between host and server/host.
ping -c1 → wait for all responses from broadcast.
ping -c1 -w1   ping wait one second at a time

![Screenshot from 2022-03-24 21-17-53](https://user-images.githubusercontent.com/59451084/159956037-dae44fb5-706d-492c-bb9f-3cc53cf91ad0.png)

## grep "time=" 

grep →  search for a string in groups of files.

![Screenshot from 2022-03-24 21-19-52](https://user-images.githubusercontent.com/59451084/159956491-1bddbf1d-408e-425d-9741-fdf4e98b388e.png)

## awk '{print substr($7, 6, length($7)) " " substr($4, 1, length($4) -1)}' 
 
 Awk is mostly used for pattern scanning and processing. It searches one or more files to see if they contain lines that matches with the specified patterns and then perform the associated actions.
substr(s, a, b) : it returns b number of chars from string s, starting at position a. The parameter b is optional, in which case it means up to the end of the string.
print substr($7, 6, length($7))  →  $7 - string  - prints seventh word of line
6 - starting position
Length($7) → ending position
print substr($7, 6, length($7)) " " substr($4, 1, length($4) -1)  →  print result of substring and give space and print result of second substring
substr($4, 1, length($4) -1)  →  $4 -string  prints fourth word of file
1 → starting position
Length($4)-1  →  print till the second last character
 
 
 ![Screenshot from 2022-03-24 21-21-51](https://user-images.githubusercontent.com/59451084/159956830-4becba20-ef0a-432d-a14b-8c622cfc20a2.png)

## sort -n

Numeric sorting is different from alphabetical sorting. For numeric sorting option 'n' is used along with the column number if required.

![Screenshot from 2022-03-24 21-23-09](https://user-images.githubusercontent.com/59451084/159957125-3cd7b17b-1cd5-4222-87ed-5958c05d49d6.png)

## awk '{print $2 " " $1 "ms"}' 

awk: Allows users to use variables, string functions, and logical operators without compiling.
{print $2 " " $1 "ms"}: print second column then first column, the delimiter is by default whitespace.

![Screenshot from 2022-03-24 21-25-53](https://user-images.githubusercontent.com/59451084/159957764-e3521e47-5a92-4394-9dd9-830844eb0a51.png)

## head -n 10

how the top 10 lines with head command.

![Screenshot from 2022-03-24 21-27-33](https://user-images.githubusercontent.com/59451084/159958321-1fe9b1d4-f64f-4f42-9276-d192d63c1ff4.png)

# Final output

Displays 10 Hosts and the reponse time of each Host. The Host IP's are provided by the given URL. 

![Screenshot from 2022-03-24 21-27-33](https://user-images.githubusercontent.com/59451084/159961425-318627b1-6ad3-45be-a8a3-f701dba72c10.png)



