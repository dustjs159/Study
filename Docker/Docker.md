๐ป Docker
==================
# ๐ก Docker ๊ฐ๋
 
* ์ค์นํด์ผ ํ  ์๋ฒ์ ์๊ฐ ๋ง์ง ์์ ๊ฒฝ์ฐ์๋ ์ง์  ์์์์ผ๋ก ์ค์นํด๋ ํฐ ๋ฌธ์ ๊ฐ ์์ง๋ง, ์ค์นํด์ผ ํ  ์๋ฒ์ ์๊ฐ ์๋ฐฑ, ์์ฒ๋์ผ ๊ฒฝ์ฐ์๋ ์์์์ผ๋ก ์ค์นํ๊ธฐ ์ด๋ ค์
* Docker๋ ์ปจํ์ด๋๋ผ๋ ๋จ์์ ์๋ฒ ์ด์์ ํ์ํ ๊ตฌ์ฑํ์ ๋ด์ ๋ฐฐํฌ ๋ฐ ๊ด๋ฆฌํ๋ ๋ฆฌ๋์ค OS ๊ธฐ๋ฐ์ Tool

## ๐ ์ปจํ์ด๋(Container)

* Docker๋ **์ปจํ์ด๋ ๊ธฐ๋ฐ์ ์คํ์์ค ๊ฐ์ํ ํ๋ซํผ** 
  * ์ปจํ์ด๋ : ํธ์คํธ ๋ด ๊ฒฉ๋ฆฌ๋ ๊ฐ๊ฐ์ ์คํ ํ๊ฒฝ
  * Docker๋ ์ปจํ์ด๋๋ผ๋ ๋ผ๋ฆฌ์  ๋จ์์ ์ค์นํ๊ณ ์ ํ๋ ์๋ฒ์ ๊ตฌ์ฑ(lib, bin ๋ฑ)์ ๋ด์ ๋ฐฐํฌ ๋ฐ ๊ด๋ฆฌ๋ฅผ ์์ํ๊ฒ ํด์ค
  * ์ปจํ์ด๋ ๋ด APP๋ค์ ๋ผ๋ฆฌ์ ์ผ๋ก ๊ฒฉ๋ฆฌ๋ ํ๊ฒฝ์์ ์คํ

### โ๏ธ ์ปจํ์ด๋ ๊ฐ์ํ ๊ธฐ์ 
* ์ปจํ์ด๋๋ ์ผ์ข์ **๊ฐ์ํ** ๊ธฐ์ 
* VMware๋ VirtualBox์์ ์ฌ์ฉํ๋ ๊ฐ์ํ ๋ฐฉ์์ ํธ์คํธ OS ์์ ๊ฒ์คํธ OS ์ ์ฒด๋ฅผ ๊ฐ์ํํ๋ ๋ฐฉ์

![แแณแแณแแตแซแแฃแบ 2022-03-29 แแฉแแฎ 5 21 23](https://user-images.githubusercontent.com/57285121/160566837-0a9a0178-ff2a-435d-b9c2-bed283c9c6c9.png)

* ๊ธฐ์กด์ ๊ฐ์ํ ๋ฐฉ์์์ ๊ฒ์คํธ OS๋ ํธ์คํธ OS์ ๋ชจ๋  ํ๋์จ์ด ์์์ ๊ณต์ ํ๊ธฐ ๋๋ฌธ์ ๋ฌด๊ฒ๊ณ  ๋๋ฆฌ๋ค๋ ๋จ์ 
* ์ด๋ฌํ ๋จ์ ์ ๊ทน๋ณตํ๊ธฐ ์ํด ํธ์คํธ OS ์์ ๊ฒ์คํธ OS๋ฅผ ์ค์นํ๋ ๊ฒ์ด ์๋ Docker ์์ง์ ์ค์นํ๊ณ  ๊ทธ ์์์ App, Bin ํ์ผ ๋ฑ์ ์คํ
* VM ๋ณด๋ค ํจ์ฌ ๊ฐ๋ณ๊ณ  ๋น ๋ฆ


## ๐ ์ด๋ฏธ์ง(Image)

* ์ด๋ฏธ์ง๋ ์ปจํ์ด๋ ์คํ์ ํ์ํ ํ์ผ๊ณผ ์ค์ ๊ฐ(App, Config)์ ํฌํจ

![แแณแแณแแตแซแแฃแบ 2022-03-29 แแฉแแฎ 5 55 56](https://user-images.githubusercontent.com/57285121/160574048-9e59cac1-84a7-424e-b755-a24f0741011a.png)

* ๊ฐ์ ์ด๋ฏธ์ง์์ ์ฌ๋ฌ ์ปจํ์ด๋ ์์ฑ ๊ฐ๋ฅ
* ์ปจํ์ด๋๊ฐ ์ญ์ ๋๊ฑฐ๋ ๋ณ๊ฒฝ๋์ด๋ ์ด๋ฏธ์ง๋ ๊ทธ๋๋ก
* ๋ง๋ค์ด ๋์ ์ด๋ฏธ์ง๋ฅผ ๋ค์ด๋ฐ๊ณ  ์ปจํ์ด๋๋ฅผ ์์ฑํ๊ณ  ์คํํ๋ฉด ๋จ
* ๋์ปค ์ด๋ฏธ์ง๋ Docker Hub์ ๋ฑ๋กํ๊ฑฐ๋ Docker Registry ์ ์ฅ์๋ฅผ ๋ง๋ค์ด ์ง์  ๊ด๋ฆฌ ๊ฐ๋ฅ

# ๐ก Docker ์ฌ์ฉ๋ฒ

* Docker ์ค์น - Linux OS
* Docker Hub์ ์ด๋ฏธ์ง ์๋ก๋ & ๋ค์ด๋ก๋
* Docker Command

## ๐ Docker ์ค์น
* Ubuntu 20.04 LTS ์์ ์งํ
  * URL : https://docs.docker.com/engine/install/ubuntu/

Repository Set up
```bash
 $ sudo apt-get update
 
 $ sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
Docker GPG Key Add
```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
Repository Status set ``Stable``
```bash
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
Docker Engine Install
```bash
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```
Check Docker Engine Version List
```bash
$ apt-cache madison docker-ce
```
Install Specific Version
```bash
$ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```
Run Test
```bash
$ sudo docker run hello-world
```

## ๐ Docker Hub ์ฌ์ฉ๋ฒ

* Docker Hub์ ์ด๋ฏธ์ง ์๋ก๋ & ๋ค์ด๋ก๋
* Docker Hub ๊ฐ์
  * https://hub.docker.com
* Repository ์์ฑ

## ๐ Docker Command

```bash
$ docker pull  # Docker ์ด๋ฏธ์ง ๊ฐ์ ธ์ค๊ธฐ + Build๊น์ง ์ํ
$ docker push  # Docker ์ด๋ฏธ์ง ์๋ก๋
$ docker images # ๊ฐ๊ณ  ์๋ ์ด๋ฏธ์ง ํ์ธ
$ docker run    # pull๋ก ๊ฐ์ ธ์จ ์ด๋ฏธ์ง(Build๊น์ง ๋ค ๋)๋ฅผ ์ปจํ์ด๋๋ก ๋ง๋ค์ด ์คํ
$ docker ps     # ์คํ์ค์ธ ์ปจํ์ด๋ ํ์ธ
```  
