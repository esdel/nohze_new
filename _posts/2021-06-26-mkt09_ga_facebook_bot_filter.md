---
layout: post
permalink: /mkt/ga-facebook-bot-filter/
title: '페이스북, 인스타그램에서 유입되는 해외트래픽의 정체 - 검수봇 발라내기'
date: 2021-06-27 11:30:00 +09:00
image: '/img/posts/017/facebook-filter-thumbnail.png'
categories:
  - mkt
tags: [GA, 필터, 페이스북, 인스타그램]
description: 구글 애널리틱스(GA) 필터 기능을 이용해 미국, 아일랜드 등 해외에서 유입되는  페북, 인스타 광고 검수봇 트래픽을 제거하는 방법
content_id: 'CM00008'
featured: true
---

페이스북, 인스타그램 광고를 하고 있다면 한번쯤은 아래와 같은 이상한 상황을 겪게 됩니다.

{%raw%}

- 분명히 아직 검토중인데, GA에 페이스북/인스타그램을 통한 세션이 잡혔다.<br>

- 동적 매개변수 (dynamic URL Parameter)를 사용했는데, GA 소스/매체에 fb / display 나 ig / display 로 잡히지 않고, {{site_source_name}}로 과도하게 잡힌다. (참고글: [페이스북 동적 매개변수 설정 방법](https://nohze.com/mkt/fb01_FacebookUTM/)) <br>

![GA에서 페이스북,인스타그램 봇을 제외하는 방법1](/img/posts/017/GA-페북필터01.png)

<br>
이 트래픽을 조금더 자세히 살펴보면, 분명히 우리는 '대한민국'을 타겟팅 했음에도 해외(대부분 미국, United States)에서 유입되었고, 이탈율이 100%에 육박함을 발견할 수 있는데요, 정상적인 사용자 유입으로 보기 어려운 이 수상한 트래픽의 정체는?

![GA에서 페이스북,인스타그램 봇을 제외하는 방법1](/img/posts/017/GA-페북필터02.png)

> 바로, 광고 검수를 위한 <u>페이스북의 검수봇</u> 입니다.

따라서, 정확도 높은 광고 성과 분석을 위해서는 **<u>검수 봇</u>**을 발라내주는 것이 좋은데, GA 필터 기능을 사용하면 간단하게 제외할 수 있습니다.<br>

{%endraw%}



------

### 📌 GA 필터로 페이스북, 인스타그램 광고 검수봇을 제외하는 방법

1. **[관리] - [보기] - [필터] - [+필터추가] 버튼을 누릅니다.**<br>

   ![GA에서 페이스북,인스타그램 봇을 제외하는 방법1](/img/posts/017/GA-페북필터03.png)
   ![GA에서 페이스북,인스타그램 봇을 제외하는 방법1](/img/posts/017/GA-페북필터04.png)<br><br>

2. **필터 이름 입력 후 유형은 [맞춤]으로 선택하고, 필터 입력란을 [IP 주소]로 선택합니다.**<br>

   ![GA에서 페이스북,인스타그램 봇을 제외하는 방법1](/img/posts/017/GA-페북필터05.png)<br><br>

3. **필터 패턴에 정규표현식을 이용해 봇 IP 목록을 입력 후 [저장] 합니다.**<br>

   ![GA에서 페이스북,인스타그램 봇을 제외하는 방법1](/img/posts/017/GA-페북필터06.png)

   아래 정규식이 포함된 IP를 드래그한 후 복사해 그대로 필터 패턴에 입력해주세요.

   ```jsx
   ^173.252.87.*$|^173.252.95.*$|^173.252.127.*$|^31.13.115.*$|^31.13.127.*$|^66.220.149.*$|^67.171.251.*$
   ```

<br>

------

### ✅ 참고사항

##### 📍 국가별 봇 IP 목록

| 봇 IP           | 국가 정보 |
| --------------- | --------- |
| 173.252.87.XXX  | 미국      |
| 173.252.95.XXX  | 미국      |
| 173.252.127.XXX | 미국      |
| 67.171.251.XXX  | 아일랜드  |
| 66.220.149.XXX  | 아일랜드  |
| 31.13.127.XXX   | 미국      |
| 31.13.115.XXX   | 미국      |



##### 📍 정규표현식

필터 패턴에 표현된 정규표현식은 아래와 같은 의미입니다.

| 표현식  | 설명                                                         |
| ------- | ------------------------------------------------------------ |
| ^문자열 | [문자열]로 시작되는 경우                                     |
| 문자열* | 이전 0개의 항목과 일치 <br />(=뒤에 어떤 문자열이 붙어도 포함) |
| $       | 입력 패턴 종료(정규식 종료)                                  |
| \|      | 여러개의 정규식을 붙여주는 구문<br /> [or 연산자=또는]와 동일합니다. |

<br>

------

### 🚨 주의사항

GA에 필터기능은 데이터 적재 자체에 영향을 미칩니다. 따라서, raw data 보고서에 필터 적용은 권장하지 않습니다. 비지니스에 적용하시는 경우에는 보기를 별도로 만들어 적용하시길 권장합니다.<br><br>

------

### 📚 참고자료

- [구글 도움말 - 포함 및 제외 필터](https://support.google.com/analytics/answer/1034832)
- [구글 도움말 - 고급필터](https://support.google.com/analytics/answer/1034836)
- [구글 도움말 - 내부 트래픽 제외하기](https://support.google.com/analytics/answer/1034840)

------

실무에서 GA와 페이스북, 인스타그램 광고 시스템을 다루며, 개인적으로 학습한 내용을 정리한 글입니다. 사실과 다른 내용이나, 문의사항이 있으시다면 댓글 또는 홈페이지 우측하단의 메신저를 보내주세요! CONTACT 페이지를 통해 메일을 보내실 수도 있습니다. 감사합니다.<br><br>