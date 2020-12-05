---
layout: post
permalink: /mkt/gtm04_GTM_Facebook/
title: '구글 태그매니저로 페이스북 픽셀 설치하기'
date: 2020-08-11 20:30:00 +09:00
image: '/img/posts/012/mkt_gtm04_thumbnail.jpg'
categories:
  - mkt
tags: [페이스북, GTM]
description: 구글 태그매니저를 활용해 웹사이트 코드 수정없이 페이스북 픽셀 설치하는 방법을 소개합니다.
content_id: 'CM00004'
featured: true
---

전환부터 리타게팅까지. 페이스북 광고를 제대로 집행하기 위해서는 반드시 웹사이트에 설치해야하는 '페이스북 픽셀(Facebook Pixel)'. 웹사이트에 직접 코드를 넣어주는 방법으로 설치할 수 도 있지만 앞서 소개한 GA와 마찬가지로 GTM을 이용하면 보다 간편하게 설치할 수 있다.

> ►참고글 1 : [구글 태그매니저로 GA 설치하기](https://nohze.com/mkt/gtm03_GAInstall/)
>
> ►참고글 2 : [Facebook Developers Guide](https://developers.facebook.com/docs/facebook-pixel/implementation)

특히 GTM 설치가 이미 완료된 경우라면 더욱 간단하다. (참고글 : [웹사이트에 GTM 설치하기](https://nohze.com/mkt/gtm02_GTMInstall/)) 또한, 추후 수정사항이 생겼을때에도 픽셀 사용자(ex.마케터)가 자유롭게 수정할 수 있다. 그래서 이 글에서는 편의성이 높은 방법인 GTM을 이용해 페이스북 픽셀을 설치하는 방법을 소개한다.

먼저 페이스북 비즈니스에 들어가서 나의 기본 픽셀코드를 확인한다.

------

### 페이스북 기본 픽셀 코드 확인하기

1. [페이스북 비즈니스](https://business.facebook.com/) > 이벤트 관리자 탭에 접속한다.
   ![페이스북 비즈니스 이벤트관리자](/img/posts/012/01.jpg)
   <br>

2. 기존에 생성해두었던 픽셀이 있는 경우에는, 적합한 픽셀을 선택한 후 [Add Events] 드롭다운 메뉴를 누르고 > [From a New Website] 를 선택한다.

   ![페이스북 이벤트 관리자 픽셀코드 확인](/img/posts/012/02.jpg)

   <br>

   새로 픽셀을 만들어야 하는 경우에는, 데이터 소스 연결 또는 비즈니스 설정에서 픽셀 추가 버튼을 눌러 신규 픽셀을 생성한다.

   ![페이스북 신규 픽셀 설치하기](/img/posts/012/03.jpg)
   <br>

3. 다음으로 팝업 모달의 메뉴에서 코드 직접 설치 단추를 누르고, 왼쪽 위에 보이는 Copy base code 하단에 있는 '코드 복사' 버튼을 누른다. <br>
   *1) 코드 직접설치 선택*

   ![페이스북 신규 픽셀 설치하기](/img/posts/012/04.jpg)

   *2) 기본 코드 복사*

   ![페이스북 신규 픽셀 설치하기](/img/posts/012/05.jpg)

   <br>

------

여기까지 준비가 됐다면,  구글 태그 매니저에 접속해 태그를 만들면 된다.

아쉽게도  페이스북 픽셀은 구글 애널리틱스와 달리 태그유형과 변수가 기본으로 제공되지 않기 때문에 맞춤 설정에 있는 **맞춤 HTML 태그**를 이용해 변수를 만들어야 한다.

<br>

------

### GTM을 이용해 페이스북 픽셀 설치하기

1. **GTM 태그만들기**
   ![GTM에서 GA기본태그 만들기](/img/posts/012/06.jpg)

   GTM에 접속해 작업화면에서 [태그] 탭을 누른 후 [새로 만들기] 버튼을 누른다.<br>

   ![GTM에서 GA기본태그 만들기](/img/posts/012/07.jpg)

   태그 이름은 '페이스북 픽셀'등 관리자가 식별하기 편한 이름으로 적어주고, 태그 유형은 [맞춤 HTML] 로 선택한다. <br>

   ![GTM에서 GA기본태그 만들기](/img/posts/012/08.jpg)
HTML 입력창에는 페이스북에서 복사한 기본코드를 붙여넣어 준다.

2. **트리거 설정 후 저장하기**

   ![GTM 트리거 만들기](/img/posts/012/09.jpg)

   트리거는 구글 태그매니저 기본태그와 마찬가지로 어떤 페이지로 들어오던 유입되는 시점에 태그가 실행되어야 하므로, 기본 트리거 중 [All Pages]를 선택한다. <br>

   ![GTM 트리거 만들기](/img/posts/012/10.jpg)

   선택 후 다시 태그화면으로 돌아오면 [저장] 해주면 연결이 끝난다.<br><br>


------

연결 후에는 문제 없이 실행되고 있는지 3가지 방법으로 확인할 수 있다.

1. **GTM - 미리보기**<br>
   먼저 GA와 마찬가지로 구글 태그매니저의 [미리보기] 기능을 활용해 확인할 수 있다. 미리보기 버튼을 누른 후 태그를 설치한 우리 웹사이트에 들어가보자.<br>

   *1) 미리보기 버튼*
   ![GTM 미리보기](/img/posts/012/11.jpg)<br>

   *2) 웹사이트에서 확인하기*

   ![GTM 미리보기](/img/posts/012/12.jpg)<br>

   웹사이트 내에 Tags Fireed 부분에 우리가 설치한 '페이스북 픽셀'태그가 보인다면, 잘 작동되고 있는 것이다.

   <br>

2. **페이스북 - 이벤트 테스트**<br>
   페이스북 비즈니스 계정에서도 별도로 디버거를 제공하고 있어서 페이스북에서도 확인할 수 있다. <br>![GTM 미리보기](/img/posts/012/13.jpg)<br>

   픽셀 코드를 확인한 화면을 닫아주고, 같은 화면에 있는 2번째 탭 [이벤트 테스트] 탭에서 브라우저 이벤트 테스트 밑에 URL을 넣고 [웹사이트 연결] 버튼을 눌러준다. <br>

   ![GTM 미리보기](/img/posts/012/14.jpg)<br>

   문제 없이 설치된 경우 위 화면과 같이 PageView 이벤트가 수신된다.
   <br>

3. **페이스북 - Facebook Pixel Helper**<br>
   마지막으로 크롬 확장 프로그램인 페이스북 픽셀 헬퍼를 통해서도 확인할 수 있다.
   ► 설치 바로가기 : [Facebook Pixel Helper](https://chrome.google.com/webstore/detail/facebook-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc)

   ![GTM 미리보기](/img/posts/012/15.jpg)<br>

   설치 후 픽셀을 설치한 웹사이트에 접속하면 컬러가 활성화되며, 누르면 PageView 이벤트가 활성화 되었음을 확인할 수 있다.

<br>

------

### 제출 및 게시하기

모두 확인했다면, 구글 태그 매니저에 돌아와 태그를 [ 제출 ] 한다.

앞선 글에서도 강조했지만, 구글 태그매니저는 작업 후 반드시 [ 제출 ] 버튼을 누른 후 버전 정보를 입력해 [ 게시 ] 해야 한다. 게시가 완료되어야 웹사이트에 작업내역이 반영된다. <br>

<br>

------

##### 📚 참고문서

- [구글 태그매니저 도움말 - 맞춤 HTML](https://support.google.com/tagmanager/answer/9334084)
- [구글 태그매니저 도움말 - 맞춤 태그 만들기](https://support.google.com/tagmanager/answer/6107167)
- [페이스북 픽셀 developer guide](https://developers.facebook.com/docs/facebook-pixel/implementation)
- [Facebook Pixel Helper](https://chrome.google.com/webstore/detail/facebook-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc)

------

실무에서 GTM을 다루며, 개인적으로 학습한 내용을 정리한 글입니다. 사실과 다른 내용이나, 문의사항이 있으시다면 댓글 또는 홈페이지 우측하단의 메신저를 보내주세요! [CONTACT](https://nohze.com/contact) 페이지를 통해 메일을 보내실 수도 있습니다. 감사합니다.<br><br>
