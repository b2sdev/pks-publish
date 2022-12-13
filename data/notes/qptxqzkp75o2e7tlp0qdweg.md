
## 개요

- Java 진영에서 웹 애플리케이션 서버 구축를 위한 프레임워크로 Spring이란 넘이 있는데 그 넘의 lite 버전으로 이해해도 무방
- Java 언어로 REST Service API를 개발 가능
- Service API는 Tomcat 서버에 올려서 서비스 (HTTP 통신을 위해)
- 참고로, 웹 애플리케이션 서버 구축을 위한 프레임워크로는 아래와 같은 것들이 있음; 역시 각각의 기술이 책 한 권 분량; 기술 간에 장단점이 있으나 경험과 지식이 없으니 일단 가장 익숙한 언어로 시작해도 무방 
  - 전통 강자인 PHP
  - Spring - Java 
  - Django - Python
  - Ruby on Rails - Ruby
  - Express (Node.js) - JavaScript


## STS (Spring Tool Suite)
  - 서버 실행
    - 초록색 RUN 아이콘 클릭
  - 프로젝트 생성
    - http://start.spring.io/
    - 에서 Spring Boot Project를 생성하고 다운받아 STS에서 연다
      - STS :: File > Open Project From File System
  - pom.xml 설정 파일? 
    - 여기에 tomcat을 추가했었나..?
  - Model과 Controller 구현
    - Model : CRUD하는 데이터를 담은 Java Object
      - getter/setter
    - RestController : RESTful API 구현부
      - 예제에서는 storage가 아닌 memory로 구현
      - '@'로 시작하는 이런 저런 annotation을 알아야 할 듯..
  - application.properties에 로그 관련 config 추가
 
## Tomcat에 배포
  - 왼쪽 아래 Servers :: 마우스 오른쪽 > New > Server > Apache > Tomcat v8.5 Server
  - 기타 설정은 교재 참조 !!
