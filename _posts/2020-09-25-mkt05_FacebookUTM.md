---
layout: post
permalink: /mkt/fb01_FacebookUTM/
title: 'URL 하나로 페이스북, 인스타그램 광고성과 자동 구분하기'
date: 2020-09-25 13:30:00 +09:00
image: '/img/posts/013/mkt_gtm05_thumbnail.jpg'
categories:
  - mkt
tags: [페이스북, UTM]
description: 페이스북, 인스타그램 광고는 사실 UTM을 분리할 필요없이 URL 하나만으로 광고 성과를 자동 구분할 수 있다.
content_id: 'CM00005'
featured: true
---

> 페이스북, 인스타그램 광고를 통해 우리 웹사이트에 방문한 고객들은 과연, 얼마만큼의 매출을 일으키고, 어떤 행동을 할까?

페이스북 광고를 운영하는 마케터를 항상 따라다니는 이 질문에 답을 찾기 위해서는 우리는 가장 먼저 페이스북 광고를 통해 들어온 고객들은 '구분' 해내야 한다. 이는 다른 광고 채널은 물론이고, 고객들이 미처 상상치 못한 다양한 경로로 유입되기 때문인데, 실제로 구글 애널리틱스 보고서를 살펴보면 적게는 수십 개에 많게는 수백 개에 이르는 다양한 경로를 통해 사용자가 유입되고 있음을 확인할 수 있다.

*[예시]* *구글애널리틱스 데모 계정 - 86개에 이르는 소스/매체로 사용자가 유입되고 있다.*

![구글 애널리틱스 데모 계정](/img/posts/013/01.png)
<br>

그래서 광고를 담당하는 대부분의 마케터들은 URL 뒤에 소스(source), 매체(medium), 캠페인(campaign) 정보를 담은 'UTM 태그'를 붙여 특정 채널(ex.페이스북)의 광고만을 구분 해내는데, 형태는 다음과 같다.

**[예시]** *나의 URL이 https://nohze.com 인 경우 **?부터 캠페인까지가 UTM 태그**다.*

`https://nohze.com?utm_souce=소스&utm_medium=매체&utm_campaign=캠페인`

그리고 여기서 조금 더 세밀하게 어떤 광고 소재에 들어온 고객인지 구분하고자 할 때에는 추가로 광고 소재에 대한 정보를 붙여주기도 한다.

`https://nohze.com?utm_souce=소스&utm_medium=매체&utm_campaign=캠페인&utm_content=광고콘텐츠&utm_term=키워드`

이를 활용하면 구글 애널리틱스를 통해 페이스북 또는 인스타그램을 통해 방문한 고객 중 특정 광고 소재를 클릭한 고객들을 구별 해낼 수 있게 된다. 예를 들어 아래와 같이 UTM태그를 붙이면, 구글 애널리틱스에서는 소스, 매체, 캠페인, 광고 콘텐츠가 분리되어 수집된다.

`https://nohze.com?utm_source=facebook&utm_medium=display&utm_campaign=traffic&utm_contnet=all&utm_term=summerSale`

- 소스 : facebook
- 매체 : display
- 캠페인 : traffic
- 광고 콘텐츠 : all
- 키워드 : summerSale

UTM에 대한 더 자세한 정보는 [구글 도움말](https://support.google.com/analytics/answer/1033863#parameters) 또는 [UTM 빌더](https://ga-dev-tools.appspot.com/campaign-url-builder/)에서 확인할 수 있다.

<br>

------

### <br>⚠️ 효율 저하와 데이터 분석 문제

그런데, 문제는 이렇게 수기 또는 반자동으로 UTM을 작성하면, 광고 관리의 효율이 떨어지고 데이터 분석에 오류가 생길 수 있다.

1. **효율저하 문제<br>: 광고의 수가 많아져 반복작업이 늘어나는 경우**<br>
   페이스북은 광고 소재를 테스트하기 위한 용도로 사용하는 경우가 많다. 따라서, 소재가 많아질 수 밖에 없는데, 성과 구분을 하려면 소재마다 URL을 새로 생성해야 한다. 게다가 광고 시스템에서도 캠페인 - 세트 - 광고의 이름을 각각 지정하고, 이를 매칭해서 UTM을 생성하기 때문에 생성한 사람이 아니라면, 나중에 일일히 매칭해 찾아야 하는 불편함이 생긴다. 때문에 UTM Builder를 활용하거나, 엑셀 또는 구글 시트에 함수를 걸어두고 URL을 쌓는 반자동 방식으로 URL을  생성, 관리하는 경우가 많은데, 이 또한 반복 수기 작업은 피할수 없다.<br><br>
2. **데이터 분리 문제<br>: 하나의 세트에서 여러가지 매체를 함께 집행하는 경우**<br>
   두번째는 1개의 세트에서 모든 노출 위치를 지정하는 경우 발생하는 문제다. 이 경우, 구글 애널리틱스에서는 '페이스북, 인스타그램, 오디언스 네트워크' 중 트래픽이 어떤 매체에서 유입 되었는지 구분할 수 없다. 때문에 많은 실무자들이 'facebook'과 'instagram'세트를 분리해 집행하는 경우가 많은데, 이렇게 되면 같은 소재의 같은 광고를 2번 걸어야 하는 수고로움이 생기며, 비용 측면에서도 효율이 떨어진다. 실제로 페이스북에서도 효율적인 광고 운영을 위해 시스템에 의한 노출 위치 자동화를 권고하고 있다.

<br>

------

### <br>💡 그렇다면 이 문제를 어떻게 해결할 수 있을까?

{%raw%}

방법은 페이스북에서 제공하는 **'동적 URL 매개변수(dynamic URL parameter)'를 이용하면 URL을 하나만 사용해 광고 성과를 자동으로 구분**할 수 있다. 그동안 쓰던 '단어'를 '동적 URL 매개변수'를 바꿔 주기만 하면 된다.

`https://nohze.com?utm_source={{site_source_name}}&utm_medium=display&utm_campaign={{campaign.name}}&utm_content={{adset.name}}
&utm_term={{ad.name}}`

예를들어 utm_source에는 그동안 쓰던 'facebook'이라는 단어 대신에 {{site_source_name}}을 쓰면 되고, utm_campaign에는 그동안 써두었던 'traffic' 이라는 단어 대신에 {{campaign.name}}을 쓰면 된다. 그럼 데이터는 광고가 노출되는 플랫폼, 지정된 캠페인 이름에 따라 '자동으로 구분되어' 구글 애널리틱스에 쌓인다.

그리고 이 중에서도 특히 {{site_source_name}}는 플랫폼을 자동으로 구분해 (fb, ig, msg, an) 데이터를 넣어주기 때문에, 이 변수를 활용하면 하나의 세트에 모든 노출 위치를 지정 했을 때 어떤 플랫폼에서 들어오는지 알 수 없었던 문제가 말끔히 해결된다.

[예시] *utm_source에 {{site_source_name}}을 쓰면 >>  fb,  ig 로 자동 구분된다.*

![소스 자동 구분](/img/posts/013/02.jpg)

이 밖에도 페이스북이 제공하는 동적 URL 매개변수는 총 8개로 필요에 맞게 활용하면 된다.

- 소스(플랫폼) = {{site_source_name}}
- 게재 위치 = {{placement}}
- 광고ID = {{ad.id}}
- 광고 세트ID = {{adset.id}}
- 캠페인ID = {{campaign.id}}
- 광고 이름 = {{ad.name}}
- 광고 세트 이름 = {{adset.name}}
- 캠페인 이름 = {{campaign.name}}

이 중에는 클릭된 게재 위치(Facebook_Desktop_Feed, Facebook_Mobile_Feed, Instagram_Feed, Instagram_Stories 등)정보를 제공하는 {{placement}} 변수도 있어서, 개제 위치에 대한 정보가 필요할 때 유용하게 사용할 수 있다.

반면에 {{ad.name}}, {{adset.name}}  {{campaign.name}} 변수는 최초 생성 시 설정한 이름으로만 데이터가 쌓이며, 이후에는 이름을 수정해도 함께 변경되지 않기 때문에 주의해야 한다. 변경한 이름으로 데이터를 쌓고 싶다면 새로 만들어야만 하며, 그대로 사용하려면 최초 설정한 이름을 유지해야 한다.

매개변수 관련 내용은 도움말 또는 페이스북 '광고' 설정 화면에서 맨 끝까지 스크롤을 내리면 보이는 'URL 매개변수' 입력란 바로 아래 'URL 매개변수 만들기'를 누르면 바로 확인할 수 있다.

![페이스북 광고 하단](/img/posts/013/03.png)

![페이스북 광고 하단](/img/posts/013/04.png)

소재 별로 여러 개의 URL을 생성할 필요 없이 단 1개의 URL로 소재별 성과를 구분하고 싶거나, 하나의 세트에서 플랫폼별 성과를 구분해 보고 싶다면 동적 URL 매개변수 활용은 매우 유용한 해결책이다. 아래 URL을 복사해 도착 URL만 바꿔주면 곧바로 적용할 수 있으니, 아래 URL을 복사해 **[도착 URL] 부분을 운영중이 비지니스의 URL로 바꾸어 적용**해보고 자신에게 맞는 변수나 순서로 응용해보길 추천한다.

`[도착 URL]?utm_source={{site_source_name}}&utm_medium=display
&utm_campaign={{campaign.name}}&utm_content={{adset.name}}&utm_term={{ad.name}}`

{%endraw%}

<br>

------

##### 📚 참고문서

- [페이스북 도움말 - 매개변수](https://ko-kr.facebook.com/business/help/1016122818401732)
- [페이스북 도움말 - 매개변수 사양](https://www.facebook.com/business/help/2360940870872492)
- [Facebook introduces URL dynamic parameters](https://newsfeed.org/facebook-url-dynamic-parameter/)
- [Auto UTM tagging in your Facebook Ads](https://www.linkedin.com/pulse/how-get-auto-utm-tagging-your-facebook-ads-campaigns-van-jaarsvelt)

------

실무에서 페이스북 광고와 GA를 다루며, 개인적으로 학습한 내용을 정리한 글입니다. 사실과 다른 내용이나, 문의사항이 있으시다면 댓글 또는 홈페이지 우측하단의 메신저를 보내주세요! [CONTACT](https://nohze.com/contact) 페이지를 통해 메일을 보내실 수도 있습니다. 감사합니다.<br><br>
