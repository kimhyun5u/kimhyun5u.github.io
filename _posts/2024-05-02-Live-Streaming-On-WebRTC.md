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

<p>
    <img src="https://private-user-images.githubusercontent.com/38347891/327313964-2b0e7298-d854-4da9-9a73-013b29dd10f9.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTQ2NTQ1ODMsIm5iZiI6MTcxNDY1NDI4MywicGF0aCI6Ii8zODM0Nzg5MS8zMjczMTM5NjQtMmIwZTcyOTgtZDg1NC00ZGE5LTlhNzMtMDEzYjI5ZGQxMGY5LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDA1MDIlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwNTAyVDEyNTEyM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWMzNDYyMmYxYTdhNWU2NGE4OWIwYmRmODM1MWZiMmVjODI5NjJiODhjNzBiMzA5NWQ1NWYyYjNmNGFlZjdmMWEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.Np4pQwc1JaUzLOe97tBpyRKEIah0eSDcjlGWkeVz-i0" alt>
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
