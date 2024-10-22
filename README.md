# Go 저장소 리스트

* [Backend server](https://github.com/gdygd/gobesvrbase)
* [Dev library](https://github.com/gdygd/goglib)
* [Shared memory](https://github.com/gdygd/goshm)
* [GpsToTilemap](https://github.com/gdygd/gps_to_tilemap)
* [Makefile](https://github.com/gdygd/gomake)
* [Kafka example](https://github.com/gdygd/gokafka)
* [Non-block tcp](https://github.com/gdygd/go-nonblock-tcp)


## 개요

이 레포지토리는 Go 언어를 사용해서 만든 백엔드 서버 모델, 몇가지 샘플코드, 유용하다고 생각되는 소스가 정리되어 있습니다. 

## 저장소 설명
### 1. Backend server
* [저장소 링크](https://github.com/gdygd/gobesvrbase)
* 이 저장소는 go 언어로 백엔드 서버 모델을 만든 것이다. 백엔드 서버에서 기본으로 지원해야 하는 기능만 구현을 해놨다. API처리, 데이터베이스 액세스, 네트워크 통신(tcp, kafka) 디버깅 툴(CLI), 프로세스 간 정보 공유를 지원하는 모델이다.
위 모델은 go로 백엔드 서버를 처음 만들 때 생각했던 디렉토리, 패키지 구조를 약간 수정해서 만들었다.

### 2. Dev library
* [저장소 링크](https://github.com/gdygd/goglib)
* go 언어를 사용해 오면서 자주 쓰는 코드를 패키지화하여 lib 형태로 개발했다. 이 라이브러리는 위 저장소(백엔드 서버)에서도 사용된다. 개인적으로 이 라이브러리에서 많이 쓰는 패키지와 함수는 로깅, 프로세스 관리, 스레드 생성/관리, 엔디안, 시간 체크를 많이 쓴다.
스레드의 경우 c/c++의 pthread와 c++builder의 thread class를 모티브로 해서 만들었다.

### 3. Shared memory
* [저장소 링크](https://github.com/gdygd/goshm)
* go 언어로 linux shm memory를 lib 형태로 개발했다. 현재도 프로세스 간 정보 공유를 할 때 사용하는 라이브러리다. 맨 처음 c/c++에서 서버 프로세스를 개발할 때 shm을 처음 사용했다. go 언어 사용하는 초기에는 오픈소스를 사용해 shm을 사용했고 나중에 오픈소스를 참고하면서 위 저장소를 만들게 되었다.

### 4. GpsToTilemap
* [저장소 링크](https://github.com/gdygd/gps_to_tilemap)
* 예전에 시스템을 구축할 때 정해진 좌표 범위 안에 있는 gps 타일만 추출했던 적이 있었다. 물론 소프트웨어에서 해당 범위만 표출하는 건 처리가 가능하지만 시스템 구축 시 전체 타일을 올리는 건 꽤 많은 용량을 차지했기에 정해진 좌표 범위의 타일만 추출하는 프로그램을 만들게 되었다.


### 5. Makefile
* [저장소 링크](https://github.com/gdygd/gomake)
* 개발하면서 중요한 것 중 하나가 버전 관리다.. 대부분 버전 관리 툴을 쓰고 있지만 간단한 commit 메세지로 관리를 잘할 수 있나? 항상 생각을 해왔다. 
그래서 컴파일 스크립트를 만들고 위 스크립트를 실행하면 컴파일과 동시에 컴파일 버전을 보여주는 스크립트를 만들게 되었고 commit 메세지로 컴파일 시 보여주는 버전 정보를 남기는 방향으로 관리를 하니 이전 코드에 대한 히스토리 관리가 더 잘된다고 느낀다.
물론 버전별 수정사항은 본인이 꼼꼼히 기록을 해야 한다.


### 6. Kafka example
* [저장소 링크](https://github.com/gdygd/gokafka)
* kafka를 공부하면서 만든 저장소다. 저장소에 가면 kafka 서버 설치부터 예제 소스 실행까지 설명해놨다.


### 7. Non-block tcp
* [저장소 링크](https://github.com/gdygd/go-nonblock-tcp)
* go를 쓰기 전에 c/c++를 사용해 tcp 소켓 프로그래밍을 처음 접했다. c/c++로 소켓을 구현할 때 read 함수가 block이 되기 때문에 read, write 스레드로 구현을 했었는데 양쪽 스레드 모두 관리를 해야 해서 non-block 모델의 싱글 스레드 모델로 구현하는 방법도 찾게 되었다. 이때 알게 된 게 select 함수와 fd를 체크하는 방법을 알게 되었다.
go 언어에서도 처음에 소켓 프로그래밍을 할 때 fd를 체크해서 non-block 모델로 구현하려고 했으나 fd를 체크하는 함수가 없어서 read, write 스레드를 따로 두어 구현을 했다가 중간중간 fd를 체크하는 방법을 찾고 non-block 코드를 테스트하면서 위 저장소를 만들게 되었다. 근데 프로젝트를 할 땐 항상 read, write 스레드를 각각 구현을 하는 방식으로 코딩을 했다.

