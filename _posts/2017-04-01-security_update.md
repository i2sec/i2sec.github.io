---
layout: entry
title: 보안업데이트의 중요성
author: 김동현
author-email: kdh@i2sec.co.kr
description: 보안업데이트는 왜 중요한가?
publish: true
---

안녕하세요. 김동현입니다.<br>
이번 글은 기술적인 내용보다는, 보안업데이트에 대한 생각을 공유하려합니다.<br>
사실 프로젝트 투입전 휴가기간에 술병에 시달려, 조금 뇌를 맑게 해야겠다는 생각으로 주절주절 서술하려 합니다.<br>

### 시작하며

정보보안업계 또는 IT업계에서 일하다보면, 보안의 중요성에 대해 조금더 크게 느끼게 됩니다.<br>
정보보안 사고가 발생하면 금전적 피해, 고객 신뢰도 하락과 같은 피해 등 여러 골치아픈 일이 생기기 때문이죠.<br>
그래서 대부분의 기업들은 백신, 방화벽, 정보보안컨설팅, 각종 보안 솔루션 도입 등을 통해 보안사고를 방지하려 합니다.<br>
기업내부예산도 최근에는 크게 증가하는 추세죠. 그런데도 정보보안사고는 끊임없이 발생하고 있습니다. 그 이유는 무엇일까요?<br>
여러가지 이유가 있겠지만, 보안 업데이트에 대해 오늘은 이야기하려 합니다.<br> 

### 보안업데이트가 뭔데?

![update](/images/2017-04-01/windows_10_update_screen.png)

보안업데이트는 위 스크린샷처럼 볼 수 있는 업데이트 내의 업데이트 내용 중 일부라고 보면 됩니다.<br>
응용프로그램이나 OS 등의 취약점을 보완하는걸 보안 업데이트라고 말합니다.<br>
실생활에 조금 비유를 해 보자면, 보안 업데이트는 문단속을 잘 하는거라고 생각해도 될 것 같습니다.<br>

### 보안업데이트는 왜 중요해?

사례를 예로 들려고 합니다.<br>
2015년 클리앙 웹 사이트에서 대량으로 랜섬웨어가 유포가 되었는데요.<br>
이때 Internet Explorer의 취약점과 Adboe Flash 취약점이 함께 사용되어, 보안패치가 되어있지 않은 사이트 이용자들은 랜섬웨어에 감염되었습니다.<br>
실제로 랜섬웨어가 대량으로 유포되었던 첫 사례라 매우 큰 이슈가 되었었죠.<br>
[클리앙 랜섬웨어 악성코드 유포사건의 전말](http://www.boannews.com/media/view.asp?idx=46010)<br>
아무튼 이러하듯, 보안사고의 원인이 패치적용 미흡으로 인해 발생하는 사례가 많습니다.<br>
특히, 악성코드 유포 방식 중 하나인 [Drive By Download](https://ko.wikipedia.org/wiki/%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B8%8C_%EB%B0%94%EC%9D%B4_%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)에 악용이 되는 경우가 많죠.<br>
또한 공격자 입장에서도 알려지지 않은 취약점(0-day)를 발견하기는 쉽지 않기에 이미 알려진 취약점(1-day)를 활용해 공격하는 사례가 많아 보안 업데이트는 항시적으로 한다는 생각이이 필요합니다.<br>
고로, 내 PC 또는 내 인프라를 잘 보호하고 싶다면.. 보안 업데이트는 필수라고 말할 수 있습니다.<br>

### 기업에는 어떻게 적용해야 할까?

사실상 기업에서는 보안 업데이트 프로세스가 대부분 있습니다.<br>
주기적으로 컨설팅도 받아 자산에 대한 버젼을 점검받고, 그에 따른 업데이트를 권고받고 있죠.<br>
하지만, 금융권이나 국가기관처럼 폐쇄망이나 외부와 통신이 되지 않는 내부망의 경우 업데이트는 매우 힘들다고 볼 수 있습니다.<br>
외부 업데이트서버에 접속을 하기가 힘든 환경이기 때문이죠. 그래서 내부망이나 폐쇄망의 경우 PMS(Patch Management System)을 도입해 해결하고 있습니다.<br>
솔루션도 중요하지만, 보안 담당자의 마인드가 먼저 따라가야되는 부분인 것 같습니다.<br>


짧게 휴가기간 중 보안 업데이트에 대한 내용을 적어보았습니다.<br>
다음 글에는 기술적인 내용으로 돌아오도록 하겠습니다. :) <br>

감사합니다.