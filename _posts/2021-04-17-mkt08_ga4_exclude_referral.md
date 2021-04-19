---
layout: post
permalink: /mkt/ga4-exclude-referral/
title: 'GA4 추천 제외 설정 - 소셜로그인, PG도메인 제외'
date: 2021-04-17 11:30:00 +09:00
image: '/img/posts/016/mkt_ga01_thumbnail.jpg'
categories:
  - mkt
tags: [GA4, 추천제외, 리퍼러]
description: GA4 '원치않는 추천나열'로 추천제외 설정하기
content_id: 'CM00007'
featured: true
---

정확도 높은 데이터 수집을 위해 GA 설치 시 필수적으로 추가 해야하는 [추천 제외] 기능이 드디어 GA4에도 업데이트 되었습니다.<br>



### 📌 추천 제외란?

**: 무의미한 도메인을 제외하는 것**

구글 애널리틱스는 우리 사이트로 트래픽이 유입되기 직전의 위치를 자동으로 인식하여 보고서에 **이전 사이트의 도메인 이름을 추천 트래픽 소스로 표시**하는데, 이때, 결제시스템(PG)또는 소셜 로그인처럼 추천(리퍼로)으로 **집계되면 안되는 무의미한 도메인을 제외하는 것**을 **추천 제외**라 합니다.<br>

![ga4 추천제외 예시 순서도](/img/posts/016/GA4-추천제외00.jpg)

예를들어 페이스북을 통해 우리 웹사이트에 방문한 사용자가 네이버 간편 로그인으로 회원가입을 하게 되면 중간에 [네이버]에 들렀다 웹사이트에 되돌아오는 과정을 거치게 되는데, 이렇게 되면 분석자가 기대한 결과와 다른 데이터가 쌓이게 됩니다. (같은 사용자임에도 세션이 2번 집계되고, 보고서에는 회원가입 이벤트가 발생한 소스/매체를 페이스북이 아니라, [nid.naver.com/referrer](http://nid.naver.com/referrerfh) 로 집계함)

이를 방지하기 위해 **네이버 로그인 페이지를 추천제외 리스트에 등록**하면 네이버에 들렀다온 과정이 무시됩니다. (nid.naver.com 추천제외 > 세션이 새로 시작되지 않아 세션은 1, 회원가입 목표는 [[facebook.com](http://facebook.com)]으로 정상 집계함)

![ga4 추천제외 예시 보고서](/img/posts/016/GA4-추천제외01.jpg)



------

### 📌 구글 애널리틱스 4 추천 제외 설정 방법

아래 1-4 과정을 통해 등록 후 저장하면 GA4에서도 추천 제외 기능을 활용할 수 있습니다.

1. [관리] - [속성] - [데이터스트림] - [등록된 도메인]
   ![ga4 추천제외 방법1](/img/posts/016/GA4-추천제외02.jpg)<br>
   ![ga4 추천제외 방법2](/img/posts/016/GA4-추천제외03.jpg)<br><br>
2. [웹 스트림 세부정보] 최하단 [추가설정]에 [태그 설정 더보기] 메뉴 클릭
   ![ga4 추천제외 방법3](/img/posts/016/GA4-추천제외04.jpg)<br><br>
3. [태그 설정 더보기] 최하단 [원치 않는 추천 나열] 클릭
   ![ga4 추천제외 방법4](/img/posts/016/GA4-추천제외05.jpg)<br><br>
4. 도메인 [입력] - [조건 추가] 후 [저장하기] 클릭
   ![ga4 추천제외 방법5](/img/posts/016/GA4-추천제외06.jpg)<br>![ga4 추천제외 방법6](/img/posts/016/GA4-추천제외07.jpg)<br><br>



------

### 🚨 주의사항

다만, 추천 제외 등록 이전의 데이터에는 반영되지 않으므로, 제외 후에도 이전 기간의 보고서에는 그대로 표기되는 부분을 염두에 두고 데이터를 분석해야 합니다. 

또, 추천 제외 목록은 포함 연산자를 기본으로 사용하기 때문에 도메인을 등록하면, 하위 도메인도 함께 제외된다는 점과 (ex- nohze.com을 제외하는 경우, test.nohze.com도 제외됨) 아래와 같은 경우는 제외 도메인으로 등록한 후에도 보고서에 표기될 수 있다는 점을 유념해야 합니다.

- 도메인 B가 첫 번째 세션에 기여하는 경우
- 사용자가 직접 사이트를 다시 방문하는 경우(예: 북마크를 통해).
- 마지막 간접 클릭 기여 모델로 인해 도메인 B가 이 두 번째 세션에도 기여한 경우

<br>

------

### 🔖 자주 사용되는 추천 제외 리스트

추천 제외 목록은 비즈니스 사용 과정과 관련된 도메인을 기준으로 만들면 되는데, 주로 사용하는 제외 리스트는 아래와 같습니다. (간편로그인, 결제 시스템, 상담을 통해 연결되는 도메인 등) 

[간편로그인]

- [kauth.kakao.com](http://kauth.kakao.com) 카카오 간편 로그인
- [accounts.kakao.com](http://accounts.kakao.com/) 카카오 간편 로그인
- [nid.naver.com](http://nid.naver.com) 네이버 간편로그인
- [accounts.google.com](http://accounts.google.com) 구글 간편로그인
- [appleid.apple.com](http://appleid.apple.com) 애플 아이디 로그인

[결제]

- [pg-web.kakao.com](http://pg-web.kakao.com) 카카오페이
- [inicis.com](http://inicis.com) 이니시스
- [payco.com](http://payco.com) 페이코
- [kcp.cp.kr](http://kcp.cp.kr) KCP
- [pay.naver.com](http://pay.naver.com) 네이버페이 결제형
- [innopay.co.kr](http://innopay.co.kr) 이노페이(SMS 결제 솔루션)
- [allatpay.com](http://allatpay.com) KG 모빌리언스(=구올앳)
- [mup.mobilians.co.kr](http://mup.mobilians.co.kr/) KG 모빌리언스

[상담톡]

- [api.channel.io](http://api.channel.io) 채널톡

<br>

------

### 📚 참고 자료

- [구글 도움말 - 추천제외](https://support.google.com/analytics/answer/2795830)
- [구글 도움말 - 교차도메인](https://support.google.com/analytics/answer/1034342)
- [구글 도움말 - [GA4] Identify unwanted referrals](https://support.google.com/analytics/answer/10327750)
- [구글 도움말 - [GA4] 교차 도메인 측정 설정하기](https://support.google.com/analytics/answer/10071811)
- [구글 도움말 - 캠페인 및 트래픽 소스](https://support.google.com/analytics/answer/6205762)
- [구글 도움말 - 웹 세션의 정의](https://support.google.com/analytics/answer/2731565)
- [구글 도움말 - 도메인 간 활동 측정하기](https://support.google.com/tagmanager/answer/6164469)

------

실무에서 GA4를 다루며, 개인적으로 학습한 내용을 정리한 글입니다. 사실과 다른 내용이나, 문의사항이 있으시다면 댓글 또는 홈페이지 우측하단의 메신저를 보내주세요! [CONTACT](https://nohze.com/contact) 페이지를 통해 메일을 보내실 수도 있습니다. 감사합니다.<br><br>