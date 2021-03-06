๐ป [AWS] Amazon S3
==================
# ๐ก Amazon S3 

* Amazon S3(Simple Storage Service) : ๊ฐ์ฒด(Object) ์คํ ๋ฆฌ์ง ์๋น์ค
* **Bucket** ๋จ์๋ก ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ๋ฉฐ Bucket์ ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ ๋งํผ ๋น์ฉ์ด ์ฒญ๊ตฌ๋จ
* **์ ์  ์น ํ์ด์ง ํธ์คํ ๊ฐ๋ฅ**
* Regional Service
* IAM ์ ์ฑ์ ํตํด Bucket์ ๋ํ CRUD ๊ถํ ์ ์ด ๊ฐ๋ฅ
* AWS KMS ์๋น์ค๋ฅผ ํตํด Bucket์ ๋ฐ์ดํฐ๋ฅผ ์ ์ก ํน์ ์ ์ฅ ์ ๋ฐ์ดํฐ ์ํธํ ๊ฐ๋ฅ 
* Bucket์ ๋ฐ์ดํฐ ์๋ก๋ ํน์ ๋ค์ด๋ก๋ ๋ฑ์ ์ด๋ฒคํธ ๋ฐ์์(Trigger) ์๋ฆผ ์ ์ก ๊ฐ๋ฅ
  * AWS SQS, SNS, Lambda
* **CloudFront** ์๋น์ค์ ํตํฉ ๊ฐ๋ฅ
  * CloudFront์ ์ฃ์ง ๋ก์ผ์ด์๊ณผ S3 ๋ฒํท ๊ฐ ํ์ผ ์๋ก๋ ๋ฐ ๋ค์ด๋ก๋ํ๋ ๋ฐฉ์์ ํตํด ๋งค์ฐ ๋น ๋ฅธ ์๋๋ฅผ ๋ณด์ฅ
  * **CloudFront + S3 ์กฐํฉ์ผ๋ก ์ ์  ์น ํ์ด์ง๋ฅผ ํธ์คํ**


## ๐ S3 ์คํ ๋ฆฌ์ง ํด๋์ค

* S3 Standard
  * ๊ฐ์ฅ ๋ณดํธ์ ์ธ ์คํ ๋ฆฌ์ง ํด๋์ค
  * ์คํ ๋ฆฌ์ง ํด๋์ค์ค ๋ฐ์ดํฐ ์ก์ธ์ค๊ฐ ๊ฐ์ฅ ๋น๋ฒํ๊ฒ ์ผ์ด๋๋ ๊ฒฝ์ฐ์ ์ ์ 
  * ๋ฒํท์ ๊ฐ์ฒด๋ฅผ ์๋ก๋ํ  ๋ ์คํ ๋ฆฌ์ง ํด๋์ค๋ฅผ ์ง์ ํ์ง ์์ ๊ฒฝ์ฐ Default ๊ฐ์ผ๋ก S3 Standard๋ฅผ ์ฌ์ฉ
* S3 Intelligent-Tiering
  * ๋ฐ์ดํฐ๊ฐ ์ ์ฅ๋๋ ๊ณณ์ ๋ ๊ณ์ธต์ผ๋ก ๋๋์ด Frequent ๊ณ์ธต์๋ ๋ฐ์ดํฐ ์ก์ธ์ค๊ฐ ์ฆ์ ๋ฐ์ดํฐ๊ฐ ์ ์ฅ๋๊ณ  Infrequent ๊ณ์ธต์๋ ์๋์ ์ผ๋ก ๋ฐ์ดํฐ ์ก์ธ์ค๊ฐ ์ ์ ๋ฐ์ดํฐ๋ค์ **๋ถ๋ฆฌํ์ฌ ์ ์ฅ**
  * ๋ฐ์ดํฐ ์ก์ธ์ค๋ฅผ ํจํด์ ๋ชจ๋ํฐ๋งํ์ฌ ๋ ๊ณ์ธต ๊ฐ ๋ฐ์ดํฐ๋ฅผ ์๋์ผ๋ก ์ด๋
  * ๋ฐ์ดํฐ ์ก์ธ์ค๊ฐ ๋ถ๊ท์น์ ์ธ ๊ฒฝ์ฐ์ ๋ฐ์ดํฐ๋ฅผ ๋ถ๋ฆฌ ์ ์ฅํ์ฌ ๋น์ฉ์ ์ค์ด๊ณ ์ ํ  ๋ ์ฌ์ฉ
* S3 Standard-IA(Infrequent Access)
  * S3 Standard์ ๋์ผํ ์ฑ๋ฅ
  * S3 Standard๋ณด๋ค ๋ฐ์ดํฐ ์ก์ธ์ค๊ฐ ์ ๊ฒ ๋ฐ์ํ  ๊ฒฝ์ฐ์ S3 Standard-IA ๋ฅผ ์ ํํ์ฌ ๋น์ฉ์ ๋ฎ์ถ ์ ์์
  * ์์ฃผ ์ก์ธ์คํ์ง ์์ง๋ง ํ์ํ  ๋ ๋น ๋ฅด๊ฒ ๋ฐ์ดํฐ์ ์ก์ธ์คํ  ๋ ์ ํฉ
  * ์ฅ๊ธฐ์ ์ธ ๋ฐฑ์์ฉ ์คํ ๋ฆฌ์ง๋ก ์ ํฉ
* S3 One Zone-IA
  * ์ผ๋ฐ์ ์ผ๋ก S3์ ์คํ ๋ฆฌ์ง๋ค์ ์ต์ 3๊ฐ ์ด์์ ๊ฐ์ฉ ์์ญ์ ์ ์ฅ๋์ง๋ง S3 One Zone-IA๋ ํ๋์ ๊ฐ์ฉ ์์ญ์๋ง ๋ฐ์ดํฐ๋ฅผ ์ ์ฅ
  * ํ๋์ ๊ฐ์ฉ ์์ญ์๋ง ์ ์ฅํ๊ธฐ ๋๋ฌธ์ S3 Standard-IA์ ๋นํด ์๋์ ์ผ๋ก ๋น์ฉ์ด ์ ๋ ด
  * ๋น์ฉ์ ์๋์ ์ผ๋ก ์ ๋ ดํ๋, ํ๋์ ๊ฐ์ฉ ์์ญ์๋ง ๋ฐ์ดํฐ๊ฐ ์ ์ฅ๋๊ธฐ ๋๋ฌธ์ ๊ฐ์ฉ์ฑ์ด ๋จ์ด์ง๊ฒ ๋๋ค๋ ๋จ์ . ๋ฐ๋ผ์ ๊ฐ์ฉ์ฑ์ด ๋ฎ์๋ ํฐ ๋ฌธ์ ๊ฐ ์๋ ๋ฐ์ดํฐ๋ค์ S3 One Zone-IA์ ์ ์ฅํ์ฌ ๋น์ฉ์ ๋ฎ์ถ ์ ์์
* S3 Glacier / Deep Archive
  * S3 Glacier๋ ์ฅ๊ธฐ๊ฐ ์ ๋น์ฉ ๋ฐ์ดํฐ ๋ณด๊ด์ด ๊ฐ๋ฅํ๋ฉฐ ์ฃผ๋ก **์์นด์ด๋ธ** ๋ชฉ์ ์ผ๋ก ์ฌ์ฉ๋ฉ๋๋ค.
  * ๋ฐ์ดํฐ๋ฅผ ๊ฐ์ฒด๊ฐ ์๋ ๋ณผํธ(Vault)๋จ์์ ์ปจํ์ด๋๋ก ์ ์ฅ
  * ๋ค๋์ ๋ฐ์ดํฐ๋ฅผ ์ฅ๊ธฐ๊ฐ ์ ์ฅํด์ผ ํ  ๊ฒฝ์ฐ์ ์ ํฉ


### S3 ์ ๊ทผ ๊ด๋ฆฌ

* S3์ ์ ๊ทผํ๊ณ ์ ํ๋ Principal์ Policy๋ฅผ Customํ์ฌ Attachํ  ๋ ์ ์์ 
```json
1. "Action": "ListAllMyBuckets"
2. "Action": "ListBucket"
```
* ์ 1๋ฒ์ ๊ณ์  ๋ด ์กด์ฌํ๋ ๋ฒํท์ ๋ฆฌ์คํธ๋ฅผ ์กฐํํ๋ Action
  * `ls bucket` 
* ์ 2๋ฒ์ ๋ฒํท ๋ด ์กด์ฌํ๋ ๊ฐ์ฒด(Object)์ ๋ฆฌ์คํธ๋ฅผ ์กฐํํ๋ Action
  * `ls object` 
* ๋ฐ๋ผ์, ์ ์ฑ์ ํ ๋นํ  ๋ `ListAllMyBuckets`์ผ๋ก ๋ฒํท ๋ฆฌ์คํธ๋ฅผ ์กฐํํ  ์ ์๋๋ก ํ๊ณ  `ListBucket` + ํน์  bucket name์ ํตํด ํน์  ๋ฒํท์ object๋ค๋ง ํ์ธํ  ์ ์๋๋ก ํ ๋น
  * `ListAllMyBuckets` ๋ฅผ ํ์ฉํ์ง ์์ผ๋ฉด `ListBucket` ๋ฅผ ๋ชจ๋  ๋ฒํท์ ํ์ฉํด๋ ๋ฒํท ๋ฆฌ์คํธ ์์ฒด๊ฐ ์กฐํ๊ฐ ๋์ง ์๊ธฐ ๋๋ฌธ์ ์๋ฌด๊ฒ๋ ๋ณผ ์ ์๋ค.


### S3 Website Hosting

  * S3๋ฅผ ์นํ์ด์ง๋ก ์ฌ์ฉํ๊ณ ์ ํ  ๋ ์ค์  ํ  ์ ์์
    * ๋ฒํท ์์ฑ ์์๋ ์ต์์ด ์๊ณ  ์๋ฌด ๋ฒํท์ด๋ ์์ฑํ ํ์ ์๊ธฐ๋ ๋ฏ?