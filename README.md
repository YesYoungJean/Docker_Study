# Docker, 이해를 위한 기록
![image](https://github.com/YesYoungJean/Docker_Study/assets/107979338/cd18623b-9cd1-49dc-bb7b-c9fe71eb6814)
<br/>
<br/>

## Docker는 무엇인가?
    Docker는 '어플리케이션을 개발(develop), 공유(ship), 구동(run)하기 위한 컨테이너 기반의 오픈소스 가상화 플랫폼'이다.
![image](https://github.com/YesYoungJean/Docker_Study/assets/107979338/e1f34e80-3de3-4ff6-a95d-895dfd676516)  
<br/>
<br/>

## Docker 등장 배경
### 전통적인 서버 관리 방식의 문제점
    일례로, 프로세스 중 하나를 변경하면 이후의 모든 프로세스를 한-땀-한-땀 수정해야 하는 상황이 발생할 수 있다.
![image](https://github.com/YesYoungJean/Docker_Study/assets/107979338/7e75c106-e43f-4512-84f0-2054c18f06fa)
<br/>
<br/>

### 문제점 해결 노력
##### 1) 문서를 통한 서버 배포
    - "문서로는 부족해.."
    
##### 2) 상태관리 도구
    - "한 서버에 다른 버전을 여러개 설치할 때는 어떡하지?"
    
##### 3) 가상머신
    - 장점_1: "1개 서버에 여러개 서버 설치 쉽다!"
    - 장점_2: "현재 상태를 저장하기도 좋다!"
    - 큰 단점: "처음부터 다시 세팅하려면 어떻게 하지? 왜 느리지?"
    
##### 4) 자원격리
    - 장점_1: "프로세스, 파일 및 디렉토리 등을 가상으로 분리할 수 있어 좋다!"
    - 큰 단점: "고오오급 기술이라 너무 어렵다!"

### Docker 등장
    1) 격리된 환경에서 작동하는 프로세스인 컨테이너 기반으로 동작한다.
    2) 리눅스 커널의 여러 기술 활용한다.
    3) 하드웨어 가상화 기술보다 가볍다.
    4) 이미지 단위로 프로세스 실행 환경을 구성한다.
<br/>
<br/>

## Docker VS VM
    - 윈도우에 VM을 설치 시 들어가는 Hypervisor와 Guest OS가 실행 속도를 느리게 한다.
    - 반면, Docker의 Docker Engine은 '격리'만 해주기에 성능상 하락이 없다.
![image](https://github.com/YesYoungJean/Docker_Study/assets/107979338/ab53a0c3-ce93-40ed-93a7-2016a512b2b3)
<br/>
<br/>

### Docker 5개 특징
##### 1) 확장성 & 이식성
    - 도커가 설치되어 있다면, 어디서든 컨테이너를 실행할 수 있다.
    - 특정 회사나 서비스에 종속적이지 않다.
    - 개발 서버 및 테스트 서버를 쉽게 생성할 수 있다.

##### 2) 표준성
    - 기존 ruby, nodejs, go, php 등으로 만든 서비스의 배포 방식은 제각각이다.
    - 하지만, '컨테이너'라는 표준으로 서버를 배포하므로 모든 서비스의 배포 과정이 동일하다.
    - 즉, capistrano? fabric? ftp? 이제는 필요없다.

##### 3) 이미지
    - 이미지는 '컨테이너를 실행하기 위한 압축파일'을 의미한다.
    - 이미지에서 컨테이너를 생성하기에 이미지를 빌드하는 과정이 반드시 필요하다.
    - 해당 이미지는 'Docker 파일' 이라는 스크립트로 만든다.
    - 빌드 서버에서 이미지를 만들어 '이미지 저장소'에 저장하고, 운영 서버에서 해당 이미지를 불러오게끔 구성된다.

##### 4) 설정 관리
    - 설정은 보통 환경변수로 제어하며, 컨테이너 띄울 때 환경변수를 같이 지정한다. (ex MYSQL_PASS=password)
    - 하나의 이미지가 환경변수에 따라 동적으로 설정파일을 생성하도록 만들어져야 한다.
    
##### 5) 자원관리
    - 컨테이너는 삭제 후 새로 생성하면 모든 데이터가 초기화된다.
    - 업로드 파일은 외부 스토리지와 링크하여 사용하거나, S3같은 별도의 저장소가 필요하다.
    - 세션이나 캐시를 memcached나 redis와 같은 외부로 분리한다.
<br/>
<br/>
