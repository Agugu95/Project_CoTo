# Project_CoTo
19.04.02 ~ 

모바일 환경에서의 컴파일을 제공하는 다목적 코딩 플랫폼 프로젝트  
  
개발환경(장비) : Windows 10, Cygwin, Android SDK 6.0 Mashmellow, Samsung Galuxy Tab 8.0,  
Amazon Web Service Free Tier, Server version Linux Ubuntu 16.04 LTS, Amazon Free Tier RDS Service,  
BootStrap 4.04, MySQL 8.0 SE, Nginx(Revers Proxy),   
  
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
  
2. 반응형 웹페이지 구현  
BootStarp을 사용  
  
3. 웹페이지를 웹뷰로 안드로이드에서 제공  
4. 무료 컴파일러나 웹 컴파일러를 이용한 텍스트 컴파일 기능
5. 이미지 텍스트 추출 및 분류에 따른  파일 생성 
6. 생성된 파일이나 텍스트를 통한 컴파일 결과값 제공 
7. 결과값 반환 
