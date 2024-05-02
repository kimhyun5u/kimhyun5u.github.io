---
layout: post
category: dev
title: "Live Streaming On WebRTC"
toc: true
---

## 개요

HLS를 사용하는 기존 스트리밍 서비스의 지연 시간(20s)을 해결하기 위해 WebRTC를 활용해 스트리밍 서비스를 구현해봄.

## 구조

### P2P

<center>
<p>
    <img src="https://kimhyun5u.github.io/assets/img/p2p.png" alt>
    <em>Live Streaming On WebRTC P2P 구조</em>
</p>

</center>
현재 시그널링 서버와 클라이언트로 구성되어 스트리머가 시청자 1개당 1개의 PeerConnection을 생성하는 구조로 구성되어있다. P2P 통신으로 구성되기 때문에 많은 시청자가 접속할 때 스트리머에서 큰 부하가 있다.

### SFU

<center>

<p>
    <img src="https://kimhyun5u.github.io/assets/img/%08sfu.png" alt>
    <em>Live Streaming On WebRTC sfu 구조</em>
</p>

</center>

그래서 위와 같은 구조를 통해 스트리머는 한개의 미디어 스트림을 서버로 보내고 서버와 클라이언트가 PeerConnection을 맺는 방식으로 구성한다.

그 결과 스트리머의 과도한 부하는 막을 수 있지만 서버의 부담이 조금 커진다.

## 계획

현재 구조를 SFU로 변경하고 서버의 부하를 최소화 할 수 있도록 미디어 Encoding 등 공부를 진행

## 코드

- [https://github.com/kimhyun5u/Live-Streaming-On-WebRTC](https://github.com/kimhyun5u/Live-Streaming-On-WebRTC)
