curl -s http://public-dns.info/nameserver/br.csv | cut -d, -f1 | shuf | tail -n 50 | xargs -i timeout 1 ping -c1 -w 1 {} | grep "time=" | awk '{print substr($7, 6, length($7)) " " substr($4, 1, length($4) -1)}' | sort -n | awk '{print $2 " " $1 "ms"}' | head -n 10

curl -s http://public-dns.info/nameserver/br.csv

![Screenshot from 2022-03-24 21-03-26](https://user-images.githubusercontent.com/59451084/159953281-9ee2ce77-f9f5-4f1c-8f8b-4c398405c939.png)

cut -d, -f1

![Uploading Screenshot from 2022-03-24 21-03-26.png…]()

curl -s http://public-dns.info/nameserver/br.csv | cut -d, -f1 | shuf

![Uploading Screenshot from 2022-03-24 21-11-03.png…]()
