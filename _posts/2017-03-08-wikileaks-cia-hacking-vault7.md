---
layout: entry
title: 위키리스크의 CIA 도감청 이슈 공개(Valut7 Project)
author: 김동현
author-email: kdh@i2sec.co.kr
description: 위키리스크의 CIA 도감청 이슈 공개(Valut7 Project) 정리 글
publish: true
---

안녕하세요. i2sec의 김동현입니다.
위키리스크에서 CIA의 도감청이슈에 대해 공개해, 정리해봤습니다.
이번 글은 정리되는 포스트로 기술적 내용과는 조금 거리가 있습니다.
위키리스크는 엄청 오랜만에 듣는 이름이네요 :)

### 개요
Wikileaks는 Year Zero의 일환으로 Vault 7이란 첫 아카이브를 공개.
* 전체크기는 513MB로  8,716건의 문서가 포함
* iOS, Android, MS용으로 개발된 0-Day 포함

### CIA's 0-Day & Encryption bypass
WhatsApp, Signal, Telegram, Weibo, Confide, Clockman의 암호화를 우회해 음성메세지 및 텍스트 메세지를 확인할 수 있다.
* 암호화 우회 및 Decryption이 가능한 것으로 추정 됨.
CIA는 NSA, GCHQ(영국의 정보기관) 또는 민간 익스플로잇 거래 업체, 파트너기관 등과 거래한 내역이 확인 되었다.
스마트폰 해킹을 위한 0-Day와 악성코드를 개발한 정황이 확인되었다.
16년까지 CIA해킹부서에 등록된 사용자는 5000명이 넘었고, 0-Day, 악성코드 및 Exploit Weapon 등이 확인 되었다.

### Weeping Angel Attack
스마트 TV를 해킹 해 감청하는 프로젝트로, 스마트TV를 통해 대화를 녹음하고 CIA서버로 보내는 프로젝트
* 이미 2013년도부터, 스마트 TV해킹은 이슈화 되어 있었다.
* 이슈가 되었던 그 당시와 아키텍쳐를 많이 수정했다고 하지만...

### CIA에서 도감청한 Spy Applicaiton 목록
- VLC Player Portable
- Irfan View
- Chrome Portable
- Opera Portable
- Firefox Portable
- ClamWin Portable
- Kaspersky TDSS Killer Portable
- McAfee Stinger Portable
- Sophos Virus Removal
- Thunderbird Portable
- Opera Mail
- Foxit Reader
- Libre Office Portable
- Prezi
- Babel Pad
- Notepad++
- Skype
- Iperius Backup
- Sandisk Secure Access
- U3 Software
- 2048
- LBreakout2
- 7-Zip Portable
- Portable Linux CMD Prompt

### Valut7 특이사항
음성인식 기술을 도입한걸로 보임. Skype 음성 대화는 실시간으로 텍스트로 변환되고, 관심있는 내용을 스캔해 CIA 서버로 전송함
* Breaking: Skype voice conversations are converted into text in real-time, scanned for contents of interest and stored in CIA spy cloud.

### 제 2의 프리즘 프로젝트?
프리즘 프로젝트의 연장선으로 보임, 사실 위키리스크 측에서 '첫번째 공개'라고 했으니, 추가적인 공개가 얼만큼 될지 매우 '기대'되는 상황
사실상 프리즘 프로젝트는 이러한 사실이 하나씩 나오며 종료됬다고 보기는 힘들어 보임.
최근 개봉된 영화 또는 발간된 책 등 / 해외 기사 등을 종합해보면 무차별한 도 감청 또는 선별된 도 감청은 확실히 이루어지고 있다고 봐도 무방할 듯 싶음.

### HammerDrill v2.0: A Malware to Steal Data From Air Gapped PCs
MS, Linux, Solaris, MacOS를 타겟으로 한 악성코드(크로스플랫폼환경으로 개발된)
망분리 환경을 타겟으로 했으며, 개발 중 테스트코드 완성도도 상당히 높아 보임
* 특정 차량 해킹내용도 들어가 있으며, 탐지할 수 없는 살인(사고 위장)이 가능하다고 제안

### 마무리하며
Goverment에서 하는 정보기관/해킹/보안활동 등이 미치는 영향은 민간에 상당한듯 싶습니다.
이러한 민간사찰 이슈는 일반인들에게 매우 가깝게 느껴질 수 밖에 없으며, 보안업계에서 일하는 저희 역시도 한번쯤은 더 생각해보게 되네요.
기술을 좋아하는 입장으로, 해머드릴 프로젝트, 스파이 앱, Weeping Angel Attack 이런 프로젝트를 보면 CIA가 참 부럽다는 생각도 좀 드네요.

### Reference
- [https://wikileaks.org/ciav7p1/][wikileaks]
- [https://file.wikileaks.org/torrent/WikiLeaks-Year-Zero-2017-v1.7z.torrent][file-wikileaks]
- [http://thehackernews.com/2017/03/wikileaks-cia-hacking-tool.html][thehackernews]
- [https://www.bleepingcomputer.com/news/security/vault-7-cia-developed-24-decoy-applications-to-spy-on-targets/][bleepingcomputer]

[wikileaks]: https://wikileaks.org/ciav7p1/
[file-wikileaks]: https://file.wikileaks.org/torrent/WikiLeaks-Year-Zero-2017-v1.7z.torrent
[thehackernews]: http://thehackernews.com/2017/03/wikileaks-cia-hacking-tool.html
[bleepingcomputer]: https://www.bleepingcomputer.com/news/security/vault-7-cia-developed-24-decoy-applications-to-spy-on-targets/
