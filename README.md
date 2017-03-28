# i2sec tech blog

## Requirements (for testing)

- [Jekyll] 1.4.3+
- [RDiscount]

## Setup

### OSX
`$ ./install-mac.sh`

## How to write a post
1. _post 디렉토리 밑에 [Markdown] 문법으로 포스트를 작성합니다.[yyyy-mm-dd-제목.md]
2. 해당 내용을 커밋하고 메인 저장소에 푸시합니다.

        $ git add -A
        $ git commit -m "Add a post..."
        $ git push

## Testing

        $ jekyll serve

## Writing Tips
1. _post 폴더 내의 파일에서 YAML Front Matter block에 <code>author</code>와 <code>author-email</code>을 넣을수 있습니다. <code>author</code>는 작성한 사람, 그리고 <code>author-email</code>은 작성자 이메일, 이렇게 추가 정보를 입력할 수 있고 실제 포스트에는 mail링크가 걸리게 됩니다. ( <code>author</code>만 있으면 링크 없음 )
2. 역시 _post 폴더 내의 파일에서 YAML Front Matter block에 <code>publish</code>란에 <code>false</code>를 입력하면 게시물을 볼 수 없습니다. 포스팅 리스트에는 뜨지만 글 내용은 Coming Soon이 뜹니다. draft작업이 다 끝나면 <code>publish</code>를 <code>true</code>로 하거나 혹은 그냥 <code>publish</code> 자체를 지워주시면 됩니다.


## Tutorial
1. Github 계정생성 / 사용하기
- https://git-scm.com/book/ko/v2/GitHub-%EA%B3%84%EC%A0%95-%EB%A7%8C%EB%93%A4%EA%B3%A0-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0


2. 계정생성후, 가입한 이메일 벤에게 다이렉트메세지로 알려주기(블로그 관련)

3. git clone -b develop https://github.com/i2sec/i2sec.github.io


4. jekyll serve 로 로컬에서 깃 돌리기
- http://jekyllrb-ko.github.io/docs/usage/

5. MD문법으로 블로그 글 작성하기
- https://teragoon.wordpress.com/2012/04/04/github%EC%97%90%EC%84%9C-readmemd-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0markdown-%EB%AC%B8%EB%B2%95/
- 작성위치: _posts/ 에 블로그 글 작성
- 규칙: 년도-달-날짜-포스팅이름.md
- ex) 2017-03-22-blog_post_edit.md

6. DEVELOP BRACNH로 푸쉬
- git add *
- 또는 git add '업데이트된 포스트 파일 명(상대경로)'
- git commit -m "업데이트 설명"
- git push -u origin develop

## 이미지 첨부 방법
- 이미지위치: images/년도-월-일/ 내 이미지 삽입
- ex) images/2017-03-22/fig_1.png
- 포스트내에서 사용할 수 있는 방법은 아래와 같습니다.
```
![이미지설명](이미지경로)
![샘플이미지](/images/2016-03-22/fig_1.png)
```
## URL 관련파일은 영문이어야함.

## 블로그 글 상단에 아래와 같은 규칙으로 있어야함
layout: entry <br>
title: 글제목 <br>
author: 작성자이름(김동현, 문경곤, 박용운, 이창영) <br>
author-email: 작성자이메일(kdh@i2sec.co.kr, abc@i2sec.co.kr, asdf@i2sec.co.kry, lcy@i2sec.co.kr) <br>
description: 글설명 <br>
publish: true <br>


  [Jekyll]: http://jekyllrb.com
  [Markdown]: http://daringfireball.net/projects/markdown/
  [RDiscount]: http://dafoster.net/projects/rdiscount/
