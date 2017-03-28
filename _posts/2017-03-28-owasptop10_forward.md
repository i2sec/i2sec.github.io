
yout: entry
title: 검증되지 않은 리다이렉트 및 포워드
author: 박용운
author-email: asdf@i2sec.co.kr
description: 포워드 취약점의 원리는 무엇인가?
publish: true
---

### 시작하며.

현업 컨설턴트 중 “A10 검증되지 않은 리다이렉트 및 포워드” 취약점 항목을 모르는 사람은 없을것이라 생각한다. 리다이렉트에 관한 자료는 많지만 포워드에 대한 예시가 없어 해당 문서를 작성한다. 즉, 해당 문서의 핵심은 리다이렉트가 아닌 포워드이다. 


![owasp](/images/2017-03-28/1.png)


위 “OWASP Top 10 한글 설명서” 요약 페이지의 마지막에 나와있듯이 취약점 분포가 드물고, 탐지 가능성 쉬움으로 평가가 되어 있는 취약점이다. 

현업 컨설턴트인 저자의 입장에서 기술적 측면으로 관심이 높지 않았다. 기술적으로 탐지하기 편하기 때문이다. 파라메타에 application명 이나 도메인 주소가 포함되어 있는지 육안으로 구분이 되기 때문에 선 분석, 후 공격이 가능하기 때문이다. 


“검증되지 않은 리다이렉트 및 포워드” 취약점 항목을 굳이 세분화 하자면 2가지라 생각한다.

1.	검증되지 않은 리다이렉트
2.	검증되지 않은 포워드

첫째, 검증되지 않은 리다이렉트 취약점은 이미 수 많은 예시 코드들이 나와있고 취약점이 직관적이라 충분히 이해를 할 수 있다.

### 안전한 URL 리다이렉트 예시 코드

Java
```
response.sendRedirect("http://www.mysite.com");
```

PHP
```<?php
 /* Redirect browser */
 header("Location: http://www.mysite.com/");
 ?>
```

ASP.NET
```
Response.Redirect("~/folder/Login.aspx")
```

Rails
```
redirect_to login_path
```


### 취약한 URL 리다이렉트 예시 코드

Java
```
response.sendRedirect(request.getParameter("url"));
```

PHP
```
$redirect_url = $_GET['url'];
 header("Location: " . $redirect_url);
```

C#
```
string url = request.QueryString["url"];
 Response.Redirect(url);
```

Rails
```
redirect_to params[:url]
```

### Exploit 예시 
```
http://example.com/example.php?url=http://malicious.example.com
```



매우 심플하다. 사용자가 넘겨준 매개변수로 각 언어별로 리다이렉트 처리시 취약점이 발생하여 악의적 URL로 렌더링 될 수 있다는 것이다.

둘째, 검증되지 않은 포워드 취약점의 예시 코드를 먼저 살펴 보겠다. 유일한 형태의 예시라 보면된다. 


### 검증되지 않은 포워드 예시 코드
```
public class ForwardServlet extends HttpServlet 
{
  protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    String query = request.getQueryString();
    if (query.contains("fwd")) 
    {
      String fwd = request.getParameter("fwd");
      try 
      {
        request.getRequestDispatcher(fwd).forward(request, response);
      } 
      catch (ServletException e) 
      {
        e.printStackTrace();
      }
    }
  }
}
```

여기서부터 궁금증이 생겼다. 

리다이렉트와 같이 사용자에게 전달받은 값으로 포워딩을 해서 발생한다는 취약점의 예시로는 맞다고 본다. 

하지만 리다이렉트와 포워딩의 차이만으로 이러한 취약점이 어떻게 발생하는지 시원하게 풀리지 않았다. 

가장 근본적인 나의 궁금증은 이러했다. 


```
http://www.example.com/admin.jsp 
```

위와 같은 요청시 관리자 메뉴 페이지가 접근이 되고 제어가 가능하다면 이 취약점은 “URL 강제요청”, “URL Jumping”, “A7 접근통제 누락” 과 같은 취약점이 되겠지만, 지금과 같은 상황에서는 당연히 “접근 권한이 없습니다.”를 출력한다는 것이고, 아래와 같은 포워딩 어플리케이션을 이용할 경우 접근제어 우회가 된다라고 익히 알려져있다.

```
http://www.example.com/function.jsp?fwd=admin.jsp
```

그렇다면 “접근제어가 우회된다.” 라는 의미는 접근제어를 하지 않는다라는 표현이 아닌 접근제어가 있지만 통과 된다라는 말이다.

자 그렇다면 웹의 포워딩이라는 기술이 어떻게 동작이 되었기에 접근제어가 우회가 가능한지 생각해보았다. 이 궁금증을 풀기 위해서는 리다이렉트와 포워딩을 비교가 필요했다.


![redirect&forward](/images/2017-03-28/2.png)


##Forward

Web Container 차원에서 페이지 이동만 있다. 실제로 웹 브라우저는 다른 페이지로 이동했음을 알 수 없다. 그렇기 때문에, 웹 브라우저에는 최초에 호출한 URL이 표시되고 이동한 페이지의 URL 정보는 볼수 없다. 동일한 웹 컨테이너에 있는 페이지로만 이동할수 있다. 현재 실행중인 페이지와 Forward에 의해 호출될 페이지는 request와 response 객체를 공유한다.

##Redirect

Web Container 는 Redirect 명령이 들어오면 웹 브라우저에게 다른 페이지로 이동하라고 명령을 내린다. 
그러면 웹 브라우저는 URL을 지시된 주소로 바꾸고 그 주소로 이동한다. 다른 웹 컨테이너에 있는 주소로 이동이 가능하다. 
새로운 페이지에서는 request 와 response 객체가 새롭게 생성된다.

역시는 역시인가 OTL. 아주 새로운 측면의 원하는(?) 내용은 없었다. 풀리지 않았다. 오랜시간 구글여행을 통해 가장 근접한 유일한 답변을 찾았다.


http://forum.spring.io/forum/spring-projects/security/1672-jsp-forward-bypasses-acegi

해당 블로그의 핵심은 내용은 바로 이것이다.

```
Security constraints only work on the original request URI, not on calls made via a RequestDispatcher (which include <jsp:include> and <jsp:forward>).
```

```
보안 제약 조건은 RequestDispatcher (<jsp : include> 및 <jsp : forward> 포함)를 통한 호출이 아니라 원래 요청 URI에서만 작동합니다. 
```

검증되지 않은 포워드의 발생원인은 바로 Include 또는 forward시 보안 제약 조건이 동작하지 않으므로 발생하는 것이다. 

여기서 말하는 보안 제약 조건이라 함은 1990년대 초창기 acegi 라고 불리는 보안 서비스 프로젝트가 이름이 변경되어 지금의 Spring Security를 부른다. 

스프링 시큐리티(Spring Security)는 스프링 서브 프로젝트 중 하나로 스프링 기반의 어플리케이션을 보호하기 위한 필수적인 프레임워크이다.

즉 Spring Security의 보안필터가 보안 제약 조건이 성립이 되지 않아 동작되지 않으므로 접근제어가 우회가 되는 것이 이 취약점의 핵심이다.

마지막으로 현재 저자의 결론은 자바 플랫폼에서만 국한적으로 발생하는 취약점이라 생각한다. 억지로 구현해낸 취약점이 아니고서는 말이다. 

현업 컨설턴트 분들에게 도움이 되었으면 한다. 

1탄은 여기서 마무리하겠다. 2탄은 더욱 어그로를 끌 수 있는 무언가를 준비하겠다. 

떡밥을 남겨두고 떠난다.


###2탄 리스트

1. 1탄을 이어서 취약점 구현해보기

2. Javascript Drive by Download with ransomware 최신 동향 및 실시간 샘플 수집&분석

3. APT 신호탄 : 피싱 메일 악성코드 제작(백신 탐지 zero)




댓글에 관심도를 반영하겠다. 

끝까지 읽어줘서 고맙다. :D







