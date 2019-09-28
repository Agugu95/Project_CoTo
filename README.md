# Project_CoTo  
## 웹 환경에서의 컴파일을 제공하는 다목적 코딩 플랫폼 프로젝트
19.04.02 ~ 19.04.19 중단  
19.09.01 재시작 모바일 -> 웹 환경 변경  
19.09.28 정해진 기간 내에 빠르게 완성해야 했기에 많은 부분에서 수정이 이루어졌음.  
  
## 개발환경  
- Windows 10, Cygwin, Linux Ubuntu Server 18.04 LTS
- Amazon Free tier EC2 Instance  
- Python 3  
- BootStrap  
- SqLite
~~- Oracle JDK 1.8 (JAVA 8)~~    
~~- Node.js 10.16 LTS~~    
~~- BootStrap 4.04~~   
~~- Mysql 8.0 SE~~  
~~- IntelliJ Ultimate Edition for Student~~  
- VSCode
- Pycharm 
~~> 기타 툴   
HeidiSQL, Webpack4, Babel7, Maven~~  

## Client Side
#### 1. 로그인 기능 구현   
Google API를 통한 Google 로그인 기능 구현  
Facebook API를 통한 Facebook 로그인 기능 구현   
Linux Ubuntu 18.04로 만들어진 Amazon EC2 인스턴스 내에 Node.js와 Express.js를 사용하여 WebServer를 구성예정  
*_암호화 방식은 SHA - 256방식을 사용할 예정 [SHA-256](https://victorydntmd.tistory.com/144 )_*    


#### 2. 반응형 웹페이지 구현  
- BootStarp을 사용한 Tablet / PC / Mobail 테스팅 
  
#### 3. 웹페이지  
- [Web Notification API(알림)](https://untitledtblog.tistory.com/107)  
Chrom 브라우저에서 제공, 웹 서버를 통한 HTML 파일에서만 동작  
- [HTTPS](https://medium.com/@sejongdekang/node-js%EC%97%90%EC%84%9C-lets-encrypt-%EB%AC%B4%EB%A3%8C-ssl-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0-fe337b87bfbb)  
백그라운드 환경에서 [serviceWorker](https://medium.com/@sejongdekang/node-js-fcm-%EC%9B%B9%EC%95%B1-%EC%84%9C%EB%B9%84%EC%8A%A4%EC%9B%8C%EC%BB%A4-%EC%9C%BC%EB%A1%9C-%ED%91%B8%EC%8B%9C-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-43c49b761dba)를 이용하여 웹 Push Notification을 주기 위해서는 https여야한다.  

## Server Side  
#### 1. 웹 컴파일러를 이용한 컴파일 결과 생성  
Ifream을 이용해 웹 컴파일러 사이트를 띄우는 것으로 타협  

#### ~~2. Ajax를 이용한 컴파일 결과 반환, 혹은 웹 소켓을 사용해도 될 것 같다.~~  
   - 근본적으로 웹 소켓과 Ajax는 HTTP의 지속성 문제를 해결하기 위한 기술들이지만 WebSocket이 좀 더 문제해결의 정답에 가깝다.  
     아마 이러면 Node.js를 사용하게 될 것 같다, 같은 이벤트 구동방식이긴 하지만 내가 아직 Netty에 대해서 잘 모르기 때문에..
     > [관련링크](https://glqdlt.tistory.com/145)  
   - 그냥 결과를 받을 때까지 대기해야하는 동기식 방식도 괜찮은듯  
   
#### 3. ~~이미지 내 텍스트 추출~~  
   - [AWS Image Rekognition API](https://docs.aws.amazon.com/ko_kr/rekognition/latest/dg/text-detection.html) 최대 50개 단어 탐지, 텍스트는 가로축 +- 90 degrees 이내에 있어야 함.  
      50개의 단어라 실제로 테스트를 해보아야할듯  
```   
    #include <stdio.h>  
    
    int main(){  
    
    return 0;
    } 
    이미지로 할 때는 어떻게 이정도의 기본 구조를 제공해줄지도 고민해봐야할듯
```

실제 테스트를 해보았는데 사용에 무리가 있음  

#### 4. 게시판 CRUD  

~~### gcc 컴파일러를 이용한 웹 컴파일러 구현~~  
- 사실상 이 부분이 이 프로젝트의 알파이자 오메가요, 시작이자 끝인 부분이다.  
  웹 컴파일러의 구현 그러니까 알 수 없는 클라이언트에서 온 소스코드를 서버의 os에서 돌리는 이 상황을 어떻게 안전하고 빠르게 제공할 것인가?  
- 가장 중요한 문제인 보안  
  '알 수 없는 클라이언트'에서 온 소스코드를 실행한다.. 서버 입장에서는 이보다 짜릿한게 있을까?  
  만약 '알 수 없는 클라이언트'가 Root 권한을 소유했다면?  
  만약 '알 수 없는 클라이언트'가 접근했을 때 리소스 용량에 제한이 없다면?  
  만약 '알 수 없는 클라이언트'가 준 소스코드가 Boxing 되어있지 않다면?  
  관련해서 알아보니 보통 코드는 파일로 전송받고, Docker와 같은 가상화 컨테이너를 이용해 SandBoxing시킨다고 한다.  
- 서버 콘솔에서 컴파일하고, 결과를 반환해주는 방식과 웹 컴파일러의 API를 가져다 쓰는 방법이 있는데 일단 API를 사용하기로 결정  

#### ~~1. [HackerEarth Compiler API](https://www.hackerearth.com/docs/wiki/developers/v3/)~~  
  
  
  
  
  
  
  
  
  
  
# 돌이켜보니 좋았던 점  

# 돌이켜보니 좋지못했던 점  

# 그래서 얻은 것은?  
