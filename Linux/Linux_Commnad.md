๐ป Linux Command
===============
# ๐ก Linux Commnad 

* Linux/Unix Command ๋ชจ์
* ์์ฃผ ์ฌ์ฉํ๋ Command + ์์ฃผ ์ฌ์ฉํ์ง ์๋๋ผ๋ ์๊ณ  ์์ผ๋ฉด ์ ์ฉํ Command
* ํ์คํธ ํ๊ฒฝ์ MacOS ํฐ๋ฏธ๋ or Ubuntu์์ ์งํ


### cut
* ํ์ผ์ด๋ ๋ฌธ์์ด์ Slice
* ์ต์
  * `-c, --characters` : ๋ฌธ์์ด ๊ธฐ์ค์ผ๋ก cut
  * `-d, --delimiter` : ๊ตฌ๋ถ์ ์ง์ . ์ง์ ํ ๊ตฌ๋ถ์๋ฅผ ๊ธฐ์ค์ผ๋ก ์ผ์ชฝ๋ถํฐ ํ๋๊ฐ์ด 1๋ฒ์ด ๋จ
  * `-f, --fileds` : ํ๋๊ฐ์ ๊ธฐ์ค์ผ๋ก cut
* ์์

`text.txt`
```
EC2-AutoScaling
VPC-NATGateway
RDS-Aurora
```
`$ cut -c 2-7 text.txt`
```
C2-AutoS
PC-NATGa
DS-Auror
```
`$ cut -d '-' -f 2 test.txt`
```
AutoScaling
NATGateway
Aurora
```

### nc
* Netcat : TCP/UDP์ Connection ๋ฐ Listen Check
  * ํด๋ผ์ด์ธํธ์ ์๋ฒ ๊ฐ ํต์ ์ด ์๋  ๋ ์ ๊ฒ ์ฉ๋๋ก ๋ง์ด ์ฌ์ฉ
* `$ nc [options] host port`
* ์ต์
  * `-v` : ๋ ๋ง์ ์ ๋ณด๋ฅผ ํ์ธํ  ์ ์์(?)
  * `-z` : ์ต์ํ์ ๋ฐ์ดํฐ๋ง ์ ์ก(?)
* ์์
```
$ nc -vz google.com 443

Connection to google.com port 443 [tcp/https] succeeded!
```

### nohup

*  ์ธ์ ์ข๋ฃ ์์๋ ํ๋ก์ธ์ค ๋ฌด์ค๋จ
* `wget` ์ด๋ `curl` ๋ช๋ น์ด๋ฅผ ์ฌ์ฉํ์ฌ ์ฉ๋์ด ํฐ ํ์ผ์ ๋ค์ด๋ก๋ ๋ฐ์ ๋, ํฐ๋ฏธ๋ ๋ก๊ทธ์ธ ์ธ์ ์๊ฐ์ด ์ข๋ฃ๋๋ฉด Parents Shell์๊ฒ **SIGHUP(HUP)** Signal์ ๋ณด๋ด๊ณ  ํ๋ก์ธ์ค๊ฐ ์ข๋ฃ๋จ
* ์ด ๋ `nohup` ๋ช๋ น์ด์ `&` ๋ฅผ ์กฐํฉํ์ฌ ์ธ์ ์๊ฐ ์ข๋ฃ ํ์๋ ๊ณ์ํด์ ๋ค์ด๋ก๋๋ฅผ ์งํ(Background)
* ์์
```
$ nuhup 
```


### more

### grep

### du


### lsblk

### arp