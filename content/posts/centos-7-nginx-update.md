---
title: "Centos 7 Nginx Update"
date: 2023-10-18T13:05:03+09:00
draft: false
---

## 작업 순서 

```
// 의존성 설치 
sudo yum install yum-utils 

// 저장소 추가 
sudo vi /etc/yum.repos.d/nginx.repo

[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key

// 위 작업에서 에러가 나면
baseurl=http://nginx.org/packages/centos/7/$basearch/ 로 변경 

// statable 버전 활성화 
yum-config-manager --enable nginx-stable

// 버전 확인
yum info nginx

// 저장소 갱신 
sudo yum update 

// nginx 업데이트
sudo yum install -y nginx 

// nginx start
systemctl start nginx
```