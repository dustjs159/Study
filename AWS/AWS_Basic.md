๐ป [AWS] AWS Basic
=================
# ๐ก AWS ๊ธฐ๋ณธ ๊ฐ๋
* AWS ์๋น์ค๋ฅผ ์ฌ์ฉํ๊ธฐ ์  ๊ธฐ๋ณธ์ ์ธ Concept์ ๋ํ ์์ฝ
* ๋ชฉ์ฐจ
  * ๋ฃจํธ ๊ณ์ (Root Account)๊ณผ ์ผ๋ฐ ์ฌ์ฉ์(IAM User)
  * ๋ฆฌ์ ผ(Region) & ๊ฐ์ฉ์์ญ(Availability Zone)
  * Service Endpoint
  * ARN(Amazon Resource Name)

## ๐ Root Account & IAM User
* Root Account : AWS์ ํ์ ๊ฐ์ ํ ์ต์ด์ ๋ก๊ทธ์ธํ๊ฒ ๋๋ ๊ณ์ 
<img width="319" alt="แแณแแณแแตแซแแฃแบ 2022-05-29 แแฉแแฎ 6 20 20" src="https://user-images.githubusercontent.com/57285121/170861140-3fabad14-196a-4615-91f9-1b641d342936.png">
  * Root Account๋ ๋๋ฌด ๋ง์ ๊ถํ์ ๊ฐ๊ณ  ์๊ธฐ์ ์ต์ด ๋ก๊ทธ์ธํ๋ ๊ฒฝ์ฐ์ ์ต์ด์ IAM User ๋ฅผ ์์ฑํ๋ ๊ฒฝ์ฐ๋ฅผ ์ ์ธํ๋ฉด ์ฌ์ฉํ์ง ์๋ ๊ฒ์ ๊ถ๊ณ 
  * ๊ณ ์ ํ Account ID (ํน์ Owner ID)๋ฅผ ๊ฐ์ง๊ณ  ์์
  * Account ๋ด์ ์ฌ๋ฌ ์๋น์ค๋ฅผ ์์ฑํ๊ณ  ๋ค๋ฅธ Account๊ฐ์ ์ ๊ทผ์ด ๋ถ๊ฐ๋ฅ 

* IAM User
  * Account ๋ด์ ์์ฑ๋๋ ์ฌ๋ฌ ๊ณ์ 
  * ์กฐ์ง ๋ด์์ Root Account๋ก Admin User๋ฅผ ์์ฑํ๊ณ  Admin User๋ก ์ฌ๋ฌ ๋ค๋ฅธ ๊ณ์ ์ ๋ง๋ค์ด์ ๊ด๋ฆฌ
  * ์ด ๋ ๊ฐ IAM User๋ค์๊ฒ ๋ถ์ฌ๋๋ ๊ถํ์ ์ต์ ๊ถํ ๋ถ์ฌ ์์น์ ์ํด ์ต์ํ์ ๊ถํ๋ง์ ๋ถ์ฌํ๋ค

## ๐ Region & Availability Zone
* Region : ๋ฌผ๋ฆฌ์ ์ธ ๋ฐ์ดํฐ ์ผํฐ๊ฐ ์์นํ ์ง์ญ
* Availability Zone(AZ) : ๋ฆฌ์  ๋ด ๋ฌผ๋ฆฌ์  ๋ฐ์ดํฐ ์ผํฐ๋ฅผ ๋ผ๋ฆฌ์ ์ผ๋ก ๋๋ ๋์ ๊ตฌ์ญ 
  * ๋ฆฌ์ ๋ง๋ค AZ์ ์๊ฐ ๋ค๋ฅด๋ค(์์ธ์ 4๊ฐ)
  * ๊ฐ์ฉ์ฑ์ ๋ณด์ฅํ๊ธฐ ์ํจ
* AWS์ ์๋น์ค๋ค์ ํฌ๊ฒ 3 Level๋ก ๋๋ ์ ์๋ค. ๊ฐ Level๋ง๋ค ์๋น์ค๋ค์ด ์์ฑ๋๋ ์์น๊ฐ ๋ค๋ฆ
  * Global
  * Regional Level
  * AZ Level

## ๐ Service Endpoint
* API ์ฌ์ฉ์ ์ ๊ทผํ๋ AWS ์๋น์ค ์์ฒด์ Endpoint

`protocol://service-code.region-code.amazonaws.com`
  * protocol : http or https
  * service-code : AWS ์๋น์ค ๊ณ ์ ์ ์ฝ๋. e.g. EC2, CloudWatch, S3 ๋ฑ
  * region-code : region ๋ณ ๊ณ ์  ์ฝ๋. e.g ap-northeast-2, us-east-2 ๋ฑ


## ๐ ARN(Amazon Resource Name)


