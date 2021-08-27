---
title: "SSL File 셍성방법"
slug: "Ssl File Create"
date: 2021-06-11T15:15:11+09:00
draft: false
---

## SSL

전송계층보안: 데이터를 중간에서 해킹당하지 않도록 암호화 해서 데이터를 서버로 전송

### 가비아

아래의 5개 파일을 전달받는다.

`Chain_RootCA_Bundle.crt` apache 서버용

`ChainCA1.crt`

`ChainCA2.crt`

`site_domain_cert.pem`

`RootCA.crt`

### Nginx

비밀번호가 해제된 private.key와 server.crt 키가 필요하다.

서버 비밀번호 해제하기

```
openssl rsa -in private.key -out nopass-private.key
비밀번호 입력
```

위 과정으로 nopass-private.key 키를 생성한다

server.crt 생성하기

```
cat site_domain_cert.pem Chain_RootCA_Bundle.crt > server.crt
```

server.crt 파일 열어 줄바꿈 확인

```
-----END CERTIFICATE----------BEGIN CERTIFICATE-----

enter를 쳐서 줄바꿈을 해준다
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
```

nginx 세팅

```
server {
        listen 443 ssl;
        server_name [도메인명];

        ssl on;
        ssl_certificate [세가지 인증서 합친 파일 경로];
        ssl_certificate_key [개인키 파일 경로];
}
```
