---
id: j95xd7tjl2d4vmcvnqfhkjz
title: Angular
desc: ''
updated: 1668223274483
created: 1533453322000
---

## 개요

- Angular란?
  - Google이 만든 오픈소스 기반의 다이나믹 웹 애플리케이션 프레임워크
  - 프론트엔드 코드를 단순하고 명료하게 하기 위해 HTML, CSS 그리고 JavaScript를 하나로 조합하는 방법을 제공
  - 2014년 10월에 처음 소개되어 2018년 6월 기준으로 v6.0.4까지 릴리즈됨
- Angular에서 사용하는 언어는 TypeScript
  - Microsoft에서 개발한 자바스크립트의 확장된 언어
  - JavaScript ES6의 기능에 엄격한 타입 체크와 객체지향적 기능을 추가
  - 브라우저는 TypeScript를 해석할 수 없기에, TSC라는 transpiler를 이용하여 TypeScript를 JavaScript로 변환하여 배포 필요
- Angular 아키텍처
  "https://angular.io/guide/architecture"
  - Component를 이용하여 Template과 Service를 관리
    - Template은 View 자체 (UI 화면; HTML)
    - Component는 View를 제어 (class; TypeScript)
      "- Components are the fundamental building blocks of Angular applications. They display data on the screen, listen for user input, and take action based on that input.
      - Components shouldn't fetch or save data directly and they certainly shouldn't knowingly present fake data. They should focus on presenting data and delegate data access to a service."
    - Service는 애플리케이션의 공통 로직 (class; TypeScript)
      - database access, http 통신
      - Services are a great way to share information among classes that don't know each other. 
  - 상세 내용은 별도로 학습 필요; 이게 Angular의 핵심
- 개발을 위해 Angular CLI를 이용해야 함
  - 예를 들어, 새로운 class를 하나 만드려고 할 때 IDE에서 생성하는 것이 아니라 CLI(Command Line Interface)를 통해 만들어야 함
    - Angular는 class의 skeleton code를 생성해주고,  
    - 빌드에 관한 설정까지 자동으로 처리해 줌 (Goood!) 
- 실습
  - Angular CRUD application 
  - Tour of Heroes application
    - https://infoscis.github.io/2017/07/21/angular-tutorial-introduction/
- 기타
  - 요새 핫한 웹 개발 프레임워크로 구글의 Angular, 페이스북의 React, 그리고 Angular와 React를 짬뽕해놓은 Vue.js라는 넘들이 있음
    - 각각의 프레임워크가 책 한 권 분량
  - 각각의 프레임워크가 장단점이 있기에 웹 서비스 개발 시 프레임워크를 선정 후 해당 프레임워크 위에서 개발
    - 규모가 있는 개발팀에서 대규모 웹 서비스 개발에는 Angular가 주로 사용된다고 함
      - 인천공항에 돌아다니는 LG 로봇의 관제 시스템도 Angular로 개발했다는 썰이.. (by LG CNS)
      - 스타트업에서는 페이스북이 만든 React가 더 널리 사용됨
  - Angular는 배우는 데 러닝 커브가 있으나 단계를 넘어서면 React보다 생산성이 더 좋다고들 함
    - 진입 장벽이 높은 이유는 1) Angular Architecture와 구성 요소들, 그리고 각 요소들의 관계를 이해해야 하고 2) 비동기 HTTP 처리를 위해 Reactive 기술을 이해해야 하며, 3) 무엇보다 TypeScript로 개발을 해야 함
    - 생산성이 좋아지는 이유는 Angular가 Architecture를 꽉 붙잡고 개발에 필요한 API들을 대부분 제공하기에, 개발자는 주어진 가이드만 따라서 로직만 개발하면 되기 때문
      - 예를 들어, 설정, 빌드 및 배포 등 개발자가 귀찮아하는 부분은 Angular가 알아서 척척~
      - 또한, 자체 라이브러리가 빵빵하므로 별도의 3rd party 라이브러리를 갖다 쓸 필요가 없음
  - 개인적으로는, SmartRM에 Angular를 선호하지는 않으나 그렇다고 다른 대안은 없음;;
    - 일단 TypeScript가 친숙하지 않고 
    - SmartRM이 정형화된 대규모 서비스를 제공하는 단계도 아니며
    - 향후 유지 보수를 위해 개발팀 전원이 Angular를 따로 학습해야 하는, 배보다 배꼽이 더 큰 문제가 있음


## 참고 자료

- Official https://angular.io/guide/quickstart
- Architecture https://angular.io/generated/images/guide/architecture/overview2.png
- 강의 자료
https://blog.naver.com/vega2k
https://github.com/vega2k/spring-boot-angular
https://github.com/vega2k/angular-user-form-app
https://github.com/vega2k/Angular6-toh-app

- Angular style gude
https://angular.io/guide/styleguide

- TypeScript guidelie
https://github.com/Microsoft/TypeScript/wiki/Coding-guidelines

- ES6 Promise 객체
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise

- RxJS Observable 객체
http://xgrommx.github.io/rx-book/index.html

- Learn rxjs
https://www.learnrxjs.io/

- Understanding Lettable Operators
https://blog.angularindepth.com/rxjs-understanding-lettable-operators-fe74dda186d3

- Understaning Subject Objects
https://medium.com/@luukgruijs/understanding-rxjs-subjects-339428a1815b
​
- angular 6 version 
https://blog.angular.io/version-6-of-angular-now-available-cc56b0efa7a4
​
- User 관리 : angular - boot 연동 (Angular Form) 예제
https://github.com/vega2k/userApp-boot-angular

- Angular 6 Example App + Angular CLI + Angular Material + Docker + Angular Example Library
https://github.com/Ismaestro/angular6-example-app

- Angular CLI
https://github.com/angular/angular-cli/wiki
```
npm install -g @angular/cli

ng new my-project
cd my-project
ng serve
```

- angular6-example-app
https://github.com/Ismaestro/angular6-example-app

- 책
https://www.amazon.com/ng-book-Complete-Angular-Nathan-Murray/dp/1985170280/ref=sr_1_3?s=books&ie=UTF8&qid=1531925325&sr=1-3&keywords=ng-book&tag=chrome-extensions-20&dpID=51Vld%252BPmHwL&preST=_SY291_BO1,204,203,200_QL40_&dpSrc=srch

http://www.yes24.com/24/goods/58054234