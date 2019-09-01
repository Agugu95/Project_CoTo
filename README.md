# Project_CoTo
19.04.02 ~ 19.04.19 중단  
19.09.01 재시작 모바일 -> 웹 환경 변경 

## 웹 환경에서의 컴파일을 제공하는 다목적 코딩 플랫폼 프로젝트  
  
>개발환경(장비) : Windows 10, Cygwin, ~~Android SDK 6.0 Mashmellow~~, ~~Galxy Tab 8.0~~    
Amazon Web Service Free Tier Account, Server version Linux Ubuntu 16.04 LTS, Amazon Free Tier RDS Service  
BootStrap 4.04, MySQL 8.0 SE, HeidiSQL, ~~Nginx(Revers Proxy)~~, Node.js + Express, ~~Vue.js~~, JavaScript ES6, Webpack4, Babel7  

## Client Side
### 1. 로그인 기능 구현  
JavaScript를 통해 웹 페이지를 구현하고 DB연동을 통한 데이터 교환에 따른 로그인 기능 구현 
Google API를 통한 Google 로그인 기능 구현  
Facebook API를 통한 Facebook 로그인 기능 구현목표   
~~<--------------------------------------19.04.09 수정사항-------------------------->  
로그인 구현은 Android Native 환경으로 구성할 것~~  
Linux Ubuntu 16.04로 만들어진 Amazon EC2 인스턴스 내에 Node.js와 Express.js를 사용하여 WebServer를 구성예정  
~~Android 상에서 Webserver를 통해 HTTP Req/Res 방식으로 로그인~~  
~~로그인 정보는 RDS Service를 이용하여 MySQL 테이블에 저장~~  
*_암호화 방식은 SHA - 256방식을 사용할 예정 [SHA-256](https://victorydntmd.tistory.com/144 )_*  
Galuxy Tab을 사용하여 테스트 빌드  

>CRUD React 게시판 구현 예제  
[링크](https://forest71.tistory.com/183)  

>CRUD Express 게시판 구현  예제
[링크](https://develtraining.tistory.com/category/%EC%9B%B9%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/Node%20+%20Express%20+%20Mysql%20%EC%9D%84%20%EC%9D%B4%EC%9A%A9%ED%95%9C%20%EA%B2%8C%EC%8B%9C%ED%8C%90%20%EB%A7%8C%EB%93%A4%EA%B8%B0)  

>CRUD Express 게시판 구현  예제
[링크](https://victorydntmd.tistory.com/29)  

>CRUD Vue 게시판 구현  예제
[링크](https://gmground.tistory.com/entry/Vuejs%EB%A1%9C-List%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-CRUD-Pagination-Search-%EA%B5%AC%ED%98%84)  

2. 반응형 웹페이지 구현  
BootStarp을 사용한 Tablet / PC / Mobail 테스팅 
  
3. 웹페이지를 웹뷰로 안드로이드에서 제공  

## Server Side  
1. 웹 컴파일러를 이용한 컴파일 결과 생성  
2. Ajax를 이용한 컴파일 결과 반환, 혹은 웹 소켓을 사용해도 될 것 같다.  
   - 근본적으로 웹 소켓과 Ajax는 HTTP의 지속성 문제를 해결하기 위한 기술들이지만 WebSocket이 좀 더 문제해결의 정답에 가깝다.  
     아마 이러면 Node.js를 사용하게 될 것 같다, 같은 이벤트 구동방식이긴 하지만 내가 아직 Netty에 대해서 잘 모르기 때문에..
     > [관련링크](https://glqdlt.tistory.com/145)  
3. 이미지 내 텍스트 추출  
    - [AWS Image Rekognition API](https://docs.aws.amazon.com/ko_kr/rekognition/latest/dg/text-detection.html) 최대 50개 단어 탐지, 텍스트는 가로축 +- 90 degrees 이내에 있어야 함.  
    50개의 단어라 실제로 테스트를 해보아야할듯  
    ```
    #include <stdio.h>  
    
    int main(){  
    
    return 0;
    }  
    ```  
    이미지로 할 때는 어떻게 이정도의 기본 구조를 제공해줄지도 고민해봐야할듯   
    
4. 게시판 CRUD    
### gcc 컴파일러를 이용한 웹 컴파일러 구현  
- 사실상 이 부분이 이 프로젝트의 알파이자 오메가요, 시작이자 끝인 부분이다.  
  웹 컴파일러의 구현 그러니까 알 수 없는 클라이언트에서 온 소스코드를 서버의 os에서 돌리는 이 상황을 어떻게 안전하고 빠르게 제공할 것인가?  
- 가장 중요한 문제인 보안  
  '알 수 없는 클라이언트'에서 온 소스코드를 실행한다.. 서버 입장에서는 이보다 짜릿한게 있을까?  
  만약 '알 수 없는 클라이언트'가 Root 권한을 소유했다면?  
  만약 '알 수 없는 클라이언트'가 접근했을 때 리소스 용량에 제한이 없다면?  
  만약 '알 수 없는 클라이언트'가 준 소스코드가 Boxing 되어있지 않다면?  
  관련해서 알아보니 보통 코드는 파일로 전송받고, Docker와 같은 가상화 컨테이너를 이용해 SandBoxing시킨다고 한다.  
  뭐 Docker에서도 빠져나올 수는 있겠지만..  
  
