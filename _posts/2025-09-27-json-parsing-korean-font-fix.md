---
layout: post
title: "117일차 json파일 파싱과 한글 깨짐 오류 고침"
date: 2025-09-27 00:52:43 +0900
categories: [게임 개발, 미연시]
tags: [Unity, JSON, TextMeshPro, 한글 폰트]
description: "json 파일 파싱으로 대사를 출력하고, TMP 한글 폰트가 깨지는 문제를 Atlas 크기 조절로 해결했다."
---

json 파일을 간단하게 만들고 파서도 간단하게 만들었다.

사실 유니티 자체 기능이 있어서 구문도 길지 않았고 블로그 참고하며 금방 만들었다.

일단 당장 대사부터 출력 시키고 대사 넘기기라던가 캐릭터 이름 출력, 캐릭터 일러스트 출력이나 선택지는 후순위로 뒀다.

![대사 출력 결과](https://blog.kakaocdn.net/dna/dmqqbU/btsQTjAnQrj/AAAAAAAAAAAAAAAAAAAAAKH8gevvXMw3JPkjw_0EP_OKEjirN4ou4R68UkpKNpzf/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1793458799&allow_ip=&allow_referer=&signature=npZW300%2F4b9%2FJQMbBO9PFcHctzY%3D)

근데 출력은 성공했는데 한글 폰트가 깨진다. 한글 폰트로 따로 넣어서 했는데도 깨져서 이유가 무엇인가 했는데

![폰트 아틀라스 설정](https://blog.kakaocdn.net/dna/bk0IqX/btsQShDAVri/AAAAAAAAAAAAAAAAAAAAAFKHyPPmgvzqEQt1PJVGenRjZiatiBBFMcJb_uhgDsux/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1793458799&allow_ip=&allow_referer=&signature=dpx%2BNh%2BIQbfGUB9Jj9TXwWOifM0%3D)

폰트 아틀라스 크기가 문제였다.. 저렇게 4096으로 맞춰놔야 안 깨진다. 원래는 512였다. 그리고 Atlas population mode도 static에서 dynamic으로 맞추는게 좋은 듯 하다.

![수정 후 정상 출력](https://blog.kakaocdn.net/dna/I4xr6/btsQTksyX8G/AAAAAAAAAAAAAAAAAAAAAHymT9Qm1MDWtA1yoGDI5x_eDP1Ku34Getk9J5B9jwTX/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1793458799&allow_ip=&allow_referer=&signature=TJ%2F22PZzNGOsWkkvB32%2B0D9dEJ4%3D)

고친 후 실행하니 잘 나오는 모습이다. 내일은 다른 라인도 함께 출력하는 것과 스페이스바로 다음 대사 출력, 캐릭터 이름 출력, 선택지와 분기점 기능을 만들어 볼 것이다.
