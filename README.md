# Project_CoTo
19.04.02 ~ 

모바일 환경에서의 컴파일을 제공하는 다목적 코딩 플랫폼 프로젝트  
  
개발환경(장비) : Windows 10, Cygwin, Android SDK 6.0 Mashmellow  
Samsung Galuxy Tab 8.0,  
Amazon Web Service Free Tier Account, Server version Linux Ubuntu 16.04 LTS, Amazon Free Tier RDS Service    
BootStrap 4.04, MySQL 8.0 SE, Nginx(Revers Proxy), Node.js + Express, React.js(Vue.js), JavaScript ES6  
Webpack4, Babel7  
  
1. 로그인 기능 구현  
JavaScript를 통해 웹 페이지를 구현하고 DB연동을 통한 데이터 교환에 따른 로그인 기능 구현 
Google API를 통한 Google 로그인 기능 구현  
Facebook API를 통한 Facebook 로그인 기능 구현목표   
<--------------------------------------19.04.09 수정사항-------------------------->  
로그인 구현은 Android Native 환경으로 구성할 것  
Linux Ubuntu 16.04로 만들어진 Amazon EC2 인스턴스 내에 Node.js와 Express.js를 사용하여 WebServer를 구성예정  
Android 상에서 Webserver를 통해 HTTP Req/Res 방식으로 로그인  
로그인 정보는 RDS Service를 이용하여 MySQL 테이블에 저장  
*_암호화 방식은 SHA - 256방식을 사용할 예정 https://victorydntmd.tistory.com/144 _*  
Galuxy Tab을 사용하여 테스트 빌드  
<--------------------------------------19.04.19 수정사항 ----------------->  
19.04.26까지의 시험기간이 끝나고 돌입예정....  
<--------------------------------------19.05-15 수정사항 ----------------->  
근시일 내에 하기 어려울 거라고 생각합니다  
아마도 방학..
<--------------------------------------19.06.10 참고사항 ----------------->  
https://okky.kr/article/563210  

CRUD React 게시판 구현   
https://forest71.tistory.com/183  

CRUD Express 게시판 구현  
https://develtraining.tistory.com/category/%EC%9B%B9%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/Node%20+%20Express%20+%20Mysql%20%EC%9D%84%20%EC%9D%B4%EC%9A%A9%ED%95%9C%20%EA%B2%8C%EC%8B%9C%ED%8C%90%20%EB%A7%8C%EB%93%A4%EA%B8%B0  

CRUD Express 게시판 구현  
https://victorydntmd.tistory.com/29  

CRUD Vue 게시판 구현  
https://gmground.tistory.com/entry/Vuejs%EB%A1%9C-List%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-CRUD-Pagination-Search-%EA%B5%AC%ED%98%84  

2. 반응형 웹페이지 구현  
BootStarp을 사용  
  
3. 웹페이지를 웹뷰로 안드로이드에서 제공  
4. 무료 컴파일러나 웹 컴파일러를 이용한 텍스트 컴파일 기능
5. 이미지 텍스트 추출 및 분류에 따른  파일 생성 
6. 생성된 파일이나 텍스트를 통한 컴파일 결과값 제공 
7. 결과값 반환 
