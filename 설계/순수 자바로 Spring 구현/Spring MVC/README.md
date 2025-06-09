<img src="https://github.com/user-attachments/assets/b7c8e977-8240-4c2e-80cb-3b1cec298281">

## 순수 자바로 스프링 프레임워크 구현하기

<p>순수 자바를 이용해서 스프링 프레임워크를 구현하는 과정에서 Spring MVC를 구현하게 되었고 Spring MVC의 핵심 기술인 DispatcherServlet과 다양한 구현체들을 구현할 기회가 있었습니다.</p>

<p>이런 상황에서 DispatcherServlet뿐만 아니라 Spring MVC에서 자주 사용하는 @PathVariable, @RequestParam, @RequestBody를 처리하기 위해 HandlerAdapter를 도입하고, HandlerAdapter에서 처리한 값을 바탕으로 어떤 템플릿 엔진을 기반으로 페이지를 렌더링할 것인지 정하는 ViewResolver를 도입한 뒤 실제 템플릿 엔진으로 값을 던져주는 View를 구현하게 되었습니다.</p>

## 느낀 점

<p>강의로, 책으로만 알고 있었던 Spring MVC의 구현체들을 직접 손으로 구현해보면서 더 가슴에 와닿았던 점이 너무 마음에 들고 만족스러웠습니다. 특히 제가 만든 스프링 프레임워크가 JSP 페이지를 렌더링할 때의 쾌감은 정말 잊지 못할 경험이었습니다.</p>

<p>IoC 컨테이너의 개발 이후에 Spring MVC를 구현하게 되었는데 앞으로 AOP와 JDBCTemplate, Validation, ExceptionHandler 등 다양한 기능을 구현할 때를 위해 초석을 다진 것 같아 매우 뿌듯하고 만족스러운 공부였습니다.</p>

## 블로그 포스팅
[순수 자바로 Spring MVC구현하기](https://coding-review.tistory.com/596)
