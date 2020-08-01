# Project_CoTo  
## 웹 환경에서의 컴파일을 제공하는 다목적 코딩 플랫폼 프로젝트
19.04.02 ~ 19.04.19 중단  
19.09.01 재시작 모바일 -> 웹 환경 변경  
19.09.28 정해진 기간 내에 빠르게 완성해야 했기에 많은 부분에서 수정이 이루어졌음.  
19.11.11 99% 종료, 다만 DB 꼬임으로 인한 리팩토링  
19.11월 중 종료, 창업 공모전 참여와 장려상 수상  

## 개발환경
실제로 사용된 것 
- Windows 10, Cygwin, Linux Ubuntu Server 18.04 LTS
- Amazon Free tier EC2 Instance  
- Putty, PuttyGen  
- Python 3  
- BootStrap 4.0  
- sqLite(로컬 환경 테스트)  
- Mysql 8.0 SE (EC2)
- django Framework  

## Client Side
#### 1. 로그인 기능 구현   
Google API를 통한 Google 로그인 기능 구현  
~~Facebook API를 통한 Facebook 로그인 기능 구현~~   
~~Linux Ubuntu 18.04로 만들어진 Amazon EC2 인스턴스 내에 Node.js와 Express.js를 사용하여 WebServer를 구성예정  
*_암호화 방식은 SHA - 256방식을 사용할 예정 [SHA-256](https://victorydntmd.tistory.com/144 )_*~~    


#### 2. 반응형 웹페이지 구현  
- BootStarp을 사용한 Tablet / PC / Mobail 테스팅 
  
## Server Side  
#### 웹 컴파일러를 이용한 컴파일 결과 생성  
Ifream을 이용해 웹 컴파일러 사이트를 띄우는 것으로 타협  
   
#### 이미지 내 텍스트 추출  
   - [AWS Image Rekognition API](https://docs.aws.amazon.com/ko_kr/rekognition/latest/dg/text-detection.html)  
    최대 50개 단어 탐지, 텍스트는 가로축 +- 90 degrees 이내에 있어야 함.  
    50개의 단어라 실제로 테스트를 해보아야할듯  
```   
    #include <stdio.h>  
    
    int main(){  
    
    return 0;
    } 
    이미지로 할 때는 어떻게 이정도의 기본 구조를 제공해줄지도 고민해봐야할듯
```

실제 테스트를 해보았는데 인식되는 텍스트의 제한때문에 사용에 무리가 있었음. 

- [Google Tesseract OCR API](https://github.com/tesseract-ocr/tesseract)  
  Google의 OCR(Optic Character Recognaition) Engin을 사용한 이미지 텍스트 인식을 적용해보았음  
  기존 AWS의 Image Recognition API는 딥러닝을 이용한 인식이고 Tesseract는 [광학 문자인식]   (https://en.wikipedia.org/wiki/Optical_character_recognition)인데 인식되는 텍스트는 딥러닝보다 많았지만 문자의 정확도가 많이 떨어진다.  

#### 게시판 CRUD  

~~### gcc 컴파일러를 이용한 웹 컴파일러 구현~~  
- 사실상 이 부분이 이 프로젝트의 알파이자 오메가요, 시작이자 끝인 부분이다.  
  웹 컴파일러의 구현 그러니까 알 수 없는 클라이언트에서 온 소스코드를 서버의 os에서 돌리는 이 상황을 어떻게 안전하고 빠르게 제공할 것인가?  
- 가장 중요한 문제인 보안  
  '알 수 없는 클라이언트'에서 온 소스코드를 실행한다..  
  만약 '알 수 없는 클라이언트'가 Root 권한을 소유했다면?  
  만약 '알 수 없는 클라이언트'가 접근했을 때 리소스 용량에 제한이 없다면?  
  만약 '알 수 없는 클라이언트'가 준 소스코드가 Boxing 되어있지 않다면?  
  관련해서 알아보니 보통 코드는 파일로 전송받고, Docker와 같은 가상화 컨테이너를 이용해 SandBoxing시킨다고 한다.  
- 서버 콘솔에서 컴파일하고, 결과를 반환해주는 방식과 웹 컴파일러의 API를 가져다 쓰는 방법이 있는데 일단 API를 사용하기로 결정  

#### ~~1. [HackerEarth Compiler API](https://www.hackerearth.com/docs/wiki/developers/v3/)~~  

#### 5. EC2 인스턴스 생성    
Windows와 Linux(Mac)의 ssh접근 방식이 달랐다.  
- Linux(Mac)의 경우  
이렇게 접근이 가능하지만    
```
$ ssh -i [Key pair filename] ubuntu@[Public DNS]
```

- Windows  
윈도우의 경우는 Putty를 이용해서 접근해야하고, PuttyGen을 이용하여 EC2 Keypair를 Putty ssh키 방식으로 변환 해줘야한다.  
자세한 [링크는](https://supdev.tistory.com/22)  

#### 6. 배포 자동화 해보기  
소스코드는 compile -> build -> deploy의 과정을 거침. (인터프리터라면 컴파일 과정 생략)  
이러한 소스 코드를 deploy하기 위해선 로컬 서버의 소스를 운영(서비스)서버에서 동작시켜야 함.  
매번 코드를 Putty를 이용해서 배포하는 것은 우리 수준에서는 문제가 없긴함.  
어차피 하나의 서버기 때문에 패키지, 프로그램등을 전부 스스로 설치해도 되니까.  
하지만 배포 자동화 방식을 알아볼 겸 택하기로 함.  
각 배포 자동화 방식의 차이를 알아보고 선택하기로 함.  
- Docker를 이용한 이미지 컨테이너 방식  
- AWS CodeBuild와 같은 Serverless Arechitecture를 이용한 방식   
- 쉘 스크립트를 쓰고, CI와 같은 툴을 통해 Github와 연동하는 방식  
- Remote Shell을 이용하는 방식  

그리고 배포 자동화와 무중단 배포는 뭐가 다른지도 알아보기로 함.

1. Dokcer를 이용한 배포 자동화  
Docker의 이미지 컨테이너 방식을 이용하는 것으로 어떤 언어에 상관없이 컨테이너에서 실행 할 이미지만 있으면 됨.  
Node든 Java든 Python이든 상관 없음.  
그런데 Windows 환경에서 Docker 구동은 지옥이나 다름 없기에 패스  

2. AWS CodeBuild와 같은 플랫폼 툴 사용   
AWS와 같은 클라우드 플랫폼의 툴을 사용하는 방식으로 같이 사용하는 인스턴스의 요금만 내면 되는 장점.
AWS에서 가이드가 잘 되어있음.  

3. CI를 통한 배포  
Circle CI, Travis CI등의 프로그램이 Github에 push된 소스를 자동으로 컴파일, 빌드, 테스트 해준다고 해서 헉 대박! 했는데  
알고보니 배포는 배포를 할 수 있는 또 다른 툴이 있어야한다.  
CI + 배포 툴이였던 것  

4. Remote Shell을 이용  
전통적인 방식으로 Shell Script을 이용한다.  
Python의 경우 Fabric이라는 오픈 소스 툴이 있어서 원격으로 쉘 스크립트를 실행해 준다고 한다.  

5. 무중단 배포와 배포 자동화  
- 
  - 무중단 배포  
  무중단 배포는 서버가 돌아가고 있는 상태에서 서버의 작동을 멈추지 않고, 수정사항을 반영시키는 것을 말한다.  
  원래라면 컴파일 언어로 작성 된 서버의 경우 컴파일 과정에서 서비스가 중단되게 되어있다.  
  이러한 과정을 없앤 것이 무중단 배포  
  무중단 배포 방식에는 AWS와 같은 클라우드 플랫폼에서 제공하는 툴을 사용하는 방식과 Docker의 이미지, NginX를 이용하는 방법이 있다.  
  ![image](https://user-images.githubusercontent.com/38939634/65850072-3d98eb00-e388-11e9-96b7-c3f1e571fe48.png)  
  무중단 배포 프로세스라고 하는데 도메인 스위칭을 통해 각 빌드를 거치는 방식인 것 같다.  
  그래서 DB에 영향을 주는 배포의 경우 이러한 방식을 사용하면 안된다고 한다.  
  Docker를 사용하는 방식은 이러한 단점을 해결해 줄 수 있다고 한다.
  
  - 배포 자동화  
  배포 자동화는 이러한 무중단 배포를 위해 사용되는 방식이다.  
  흔히 빌드와 배포를 동시에 해주며 Github에 올라오는 소스 코드를 내려 받아 빌드 스크립트를 실행하고, 배포하는 과정을  
  배포 자동화 툴이 대신 해준다.  
 
- 결론  
Docker를 지금 하기엔 러닝커브가 있을 것 같고, 로컬 환경이 윈도우라 어려움이 있다.  
따라서 가이드가 잘 되어있는 AWS의 Code Deploy를 이용하고, 빌드 자동화는 CI를 이용하기로 했다.  

#### 7. 배포 자동화 해보기  
- 캔슬  

# 코드와 추가적 내용 정리  
[다른 프로젝트 팀원이 올려놓은 코드와 정리 자료](https://github.com/JeongGyuJun/COTO_project)  
- 주 서비스 로직에 관한 개발은 이쪽이 맡음  
- 코드를 한명이 관리했는데 저장소 전략을 사용해서 관리해야 함  
- 역시나 서비스의 제대로 된 사진이 없음 ㅠㅠ  

# 그래서 얻은 것은?  
- Two is one, one is Nothing  
둘은 하나지만, 하나는 아무것도 아니다.  
- DB 설계와 ORM의 사용  
- 커뮤니케이션이 정말 왜 중요한지 알았음  
- 프로젝트 간 일정관리, 이슈 트래킹 등 기록의 중요성을 절실하게 깨달음  
- 다음 프로젝트에는 설계부터 빠삭하게 진행 중  
  - [2020년도 프로젝트](https://velog.io/@agugu95/series/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8)  
  - [2020년도 프로젝트 : 백엔드가 이 정도는 해야 한대](https://velog.io/@agugu95/series/%EB%B0%B1%EC%97%94%EB%93%9C%EA%B0%80-%EC%9D%B4-%EC%A0%95%EB%8F%84%EB%8A%94-%ED%95%B4%EC%95%BC-%ED%95%9C%EB%8C%80)  
