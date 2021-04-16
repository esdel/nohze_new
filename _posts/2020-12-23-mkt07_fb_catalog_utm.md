---
layout: post
permalink: /mkt/facebook-catalog-utm/
title: '페이스북, 인스타그램 카탈로그 광고 - UTM 설정하기'
date: 2020-12-23 13:30:00 +09:00
image: '/img/posts/015/mkt_facebook03_thumbnail.jpg'
categories:
  - mkt
tags: [페이스북, 카탈로그, utm]
description: 카탈로그 링크를 수정하지 않고, 광고에만 UTM을 설정하는 방법
content_id: 'CM00006'
featured: true
---

광고 성과를 구분하기 위해 디지털 마케터들이 광고 URL에 필수적으로 붙이는 UTM.

그러나 페이스북 카탈로그 광고에는 누락되는 경우가 종종있다. 이유는 **카탈로그 등록 단계에서 설정한 기본 URL이 광고 설정단계에서도 그대로 이용**되기 때문이다. 그래서 문제를 인지한 실무자들은 이를 해결하기 위해 **[물품 수정]** 기능을 통해 링크를 변경하기도 하는데, 이 조치에는 아쉽게도 2가지 한계점(자동업데이트, 광고 외 노출위치에 대한 데이터 오류)이 존재한다.

### ⚠️ 한계점1 - 자동업데이트

카탈로그는 대부분 '픽셀'을 통해 추가하는데, 이 경우 웹사이트와 카탈로그의 정보 일치를 위해 페이스북에서는 주기적으로 카탈로그의 정보를 업데이트 한다. 때문에 [물품 수정]을 통해 링크를 변경해도 업데이트가 되면 다시 원본 URL로 돌아가 버린다.

이를 방지하기 위해 자동 업데이트를 해제할 수 도 있지만, 이렇게되면 추가적으로 변경되는 최신 정보(가격, 재고 등)를 받아올 수 없어 웹사이트와 광고게시물의 차이가 생겨 더 큰 문제를 유발할 수도 있다.<br>

![카탈로그 자동 업데이트 해제](/img/posts/015/02.jpg)

*참고 : 카탈로그 자동 업데이트 해제 방법*

<br>

### ⚠️ 한계점2 - 광고 외 노출 위치

또한 카탈로그 자체의 URL을 변경해버리면, 광고 뿐 아니라 카탈로그를 사용하는 모든 위치(ex. 쇼핑태그, shop 등) 에서 영향을 받게 된다. 이렇게 되면 광고 노출이 아님에도 구글 애널리틱스에는 소스/매체가 광고 노출로 잡히거나 undefined가 잡히는 등 제대로 된 데이터를 쌓을 수 없게 된다.

------

### 💡 해결방법 - 매개변수에 UTM 추가하기

그래서 카탈로그에 제대로된 UTM을 붙이려면 카탈로그 URL을 수정하는 것이 아니라 **광고 단계**에서 매개변수를 추가 해야한다. 매개변수는 페이스북 광고 설정 수준의 가장 하위인 '광고' 단계에서 설정할 수 있으며, 광고의 가장 하단에 있는 **[추적]** 영역에 있다.

**👉 1. 추적영역 찾기** 

: 페이스북 광고 - [만들기] 또는 [수정] - 스크롤 다운 - 최하단 영역

![카탈로그 링크 수정](/img/posts/015/03.jpg)<br>

<br>

**👉 2. URL 매개변수 입력란 찾기** 

: [추적] 영역 최하단 - URL 매개변수 입력란

![URL 매개변수 입력](/img/posts/015/04.jpg)<br>

<br>

**👉 3. UTM 추가**

: UTM 정책에 맞게 key값(utm_source) 입력하기

![카탈로그 링크 수정](/img/posts/015/05.jpg)<br>

<br>

이렇게 광고에 URL 매개변수를 입력하는 방식으로 UTM을 붙여주면, 페이스북은 UTM 매개변수가 붙은 URL로 광고를 연결해준다. 그럼 GA에는 카탈로그 광고로 부터 유입된 데이터가 구분되어 쌓인다.

이때, 앞선 글에서 소개한 동적 파라미터를 활용하면 더욱 편리하게 정보를 입력받을 수 있으므로, 여기에도 동적 파라미터를 이용하는 것이 효율적이다. (참고글 : [URL 하나로 페이스북, 인스타그램 광고 성과를 자동 구분해주는 동적 파라미터](https://nohze.com/mkt/fb01_FacebookUTM/))

🚨 단, 여기에서 주의해야할 점은 URL 매개변수 입력란에는 기존 광고 URL을 추가할때 처럼 https://로 시작하는 URL을 전부 입력하는 것이 아니라, **utm_source로 시작하는 UTM 키부터 넣어야 한다는 것이다.**

**아래 내용을 URL 매개변수 입력란에 그대로 복사 붙여넣으면 곧바로 적용**할 수 있다.

{%raw%}

`utm_source={{site_source_name}}&utm_medium=display`
`&utm_campaign={{campaign.name}}&utm_content={{adset.name}}&utm_term={{ad.name}}`

{%endraw%}

<br>

------

##### 📚 참고문서

- [페이스북 도움말 - 카탈로그](https://www.facebook.com/business/help/1275400645914358)
- [페이스북 도움말 - 광고 URL 매개변수](https://www.facebook.com/business/help/1016122818401732)
- [Facebook Dynamic UTM Tagging, Nomenclature & Examples](https://kasperbergholt.org/facebook-utm-dynamic-tagging)

------

실무에서 페이스북 광고와 GA를 다루며, 개인적으로 학습한 내용을 정리한 글입니다. 사실과 다른 내용이나, 문의사항이 있으시다면 댓글 또는 홈페이지 우측하단의 메신저를 보내주세요! [CONTACT](https://nohze.com/contact) 페이지를 통해 메일을 보내실 수도 있습니다. 감사합니다.<br><br>