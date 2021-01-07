---
title: "TCP/IP 프로토콜이란?"
slug: "What-is-protocol"
date: 2021-01-07T10:30:55+09:00
draft: false
---

## TCP/IP 프로토콜이란?

TCP(Transmission Control Protocol): 신뢰있는 데이타 전송방법.

IP(internet protocol): 각각의 컴퓨터에 부여되는 고유주소.

전 세계에 총42억개의 IP가 가능하다.

프로토콜(protocol)은 정보를 주고 받기 위한 규칙

## TCP/IP 프로토콜의 5계층

### 물리층

link층에서 받은 frame을 signal로 바꾼다.

### 데이터 링크층

network츠에서 받은 datagram을 frame으로 캡슐하한다.

### 네트워크층

transport층에서 받은 TCP를 받아서 datagram으로 캡슐화 한다. ip주소를 써서 목적지를 찾아간다.

주요기능은 라우팅, 포워딩.

### 전송층

application층에서 받은 메세지를 segment(by TCP)와 같은 것들로 캡슐화 한다.

### 응용층

프로세스간 통신을 하는 층이다.
