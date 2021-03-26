---
title: "Rails 최적의 서버 환경"
slug: "Rails Best Server deploy Condition"
categories: ["rubyonrails"]
tags: ["server", "deploy", "awsElasticBeanstalk"]
date: 2021-03-26T17:12:49+09:00
draft: false
---


## 레일즈 배포에 최적의 서버 환경

### AWS Elastic Beanstalk + RDS + S3

주로 AWS Elastic Beanstalk을 쓰고 있지만, beanstalk 환경이 자주 업데이트 되며 배포시 이전 환경을 찾지 못했다는 등 어려움이 많다. 

서버, db서버, image서버가 분리된 상태로 각각 최적의 환경에서 서비스 되어야 하는데 AWS Elastic Beanstalk은 배포가 불안하다 

일단 배포가 되면 안정적이지만, 배포에 어려움이 있다. 


