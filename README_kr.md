# scouter-plugin-server-alert-alertnow
### Scouter server plugin to send a alert via AlertNow

- 23king 님의 slack plugin project를 토대로 만들었습니다. 감사합니다.

- 본 프로젝트는 스카우터 서버 플러그인으로써 서버에서 발생한 Alert 을 AertNow 로 전송하는 역할을 한다.
  (*[AlertNow 란?](https://www.opsnow.com/service/alertnow))
- 현재 지원되는 Alert의 종류는 다음과 같다.
	- Agent의 CPU (warning / fatal)
	- Agent의 Memory (warning / fatal)
	- Agent의 Disk (warning / fatal)
	- 신규 Agent 연결
	- Agent의 연결 해제
	- Agent의 재접속
	- 응답시간의 임계치 초과
    - GC Time의 임계치 초과
    - Thread 갯수의 임계치 초과

### Properties (스카우터 서버 설치 경로 하위의 conf/scouter.conf)
* **_ext\_plugin\_alertnow\_send\_alert_** : AlertNow 메시지 발송 여부 (true / false) - 기본 값은 false
* **_ext\_plugin\_alertnow\_debug_** : 로깅 여부 - 기본 값은 false
* **_ext\_plugin\_alertnow\_level_** : 수신 레벨(0 : INFO, 1 : WARN, 2 : ERROR, 3 : FATAL) - 기본 값은 0
* **_ext\_plugin\_alertnow\_webhook_url_** : AlertNow WebHook URL
* **_ext\_plugin\_elapsed\_time\_threshold_** : 응답시간의 임계치 (ms) - 기본 값은 0으로, 0일때 응답시간의 임계치 초과 여부를 확인하지 않는다.
* **_ext\_plugin\_gc\_time\_threshold_** : GC Time의 임계치 (ms) - 기본 값은 0으로, 0일때 GC Time의 임계치 초과 여부를 확인하지 않는다.
* **_ext\_plugin\_thread\_count\_threshold_** : Thread Count의 임계치 - 기본 값은 0으로, 0일때 Thread Count의 임계치 초과 여부를 확인하지 않는다.
* **_ext\_plugin\_alertnow\_xlog\_enabled_** : xlog maasege send (true / false) - default : false

* Example
```
# External Interface (AlertNow)
ext_plugin_alertnow_send_alert=true
ext_plugin_alertnow_debug=true
ext_plugin_alertnow_level=1
ext_plugin_alertnow_webhook_url=AlertNow webhook url 을 이곳에 입력합니다.
ext_plugin_alertnow_xlog_enabled=true

ext_plugin_elapsed_time_threshold=5000
ext_plugin_gc_time_threshold=5000
ext_plugin_thread_count_threshold=300
```

### Dependencies
* Project
    - scouter.common
    - scouter.server
* Library
    - commons-codec-1.9.jar
    - commons-logging-1.2.jar
    - httpclient-4.5.2.jar
    - httpcore-4.4.4.jar

### Build & Deploy
* Build
    - mvn clean package

* Deploy
    - 빌드 후 프로젝트 하위에 target 디렉토리가 생기며, scouter-plugin-server-alert-alertnow-1.0.0-SNAPSHOT.jar 파일을 복사하여 스카우터 서버 설치 경로 하위의 lib/ 폴더에 저장한다.
