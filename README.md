# scouter-plugin-server-alert-alertnow
### Scouter server plugin to send a alert via AlertNow

- this project inspired by slack plugin project of 23king. thanks for this project.

- this project is  scouter server plugin project. this project goal is that send message to AlertNow.
-  this project only support a sort of Alert.
	- CPU of Agent  (warning / fatal)
	- Memory of Agent (warning / fatal)
	- Disk of Agent (warning / fatal)
	- connected new Agent
	- disconnected Agent
	- reconnect Agent

### Properties (you can modify in conf/scouter.conf of scouter server home )
* **_ext\_plugin\_alertnow\_send\_alert_** : can send AlertNow message or can'not  (true / false) - default : false
* **_ext\_plugin\_alertnow\_debug_** : can log message or can't  - default false
* **_ext\_plugin\_alertnow\_level_** : log level (0 : INFO, 1 : WARN, 2 : ERROR, 3 : FATAL) - default 0
* **_ext\_plugin\_alertnow\_webhook_url_** : AlertNow WebHook URL
* **_ext\_plugin\_elapsed\_time\_threshold_** : 응답시간의 임계치 (ms) - 기본 값은 0으로, 0일때 응답시간의 임계치 초과 여부를 확인하지 않는다.
* **_ext\_plugin\_gc\_time\_threshold_** : GC Time의 임계치 (ms) - 기본 값은 0으로, 0일때 GC Time의 임계치 초과 여부를 확인하지 않는다.
* **_ext\_plugin\_thread\_count\_threshold_** : Thread Count의 임계치 - 기본 값은 0으로, 0일때 Thread Count의 임계치 초과 여부를 확인하지 않는다.
* **_ext\_plugin\_alertnow\_xlog\_enabled_** : xlog maasege send (true / false) - default : false

* Example
```
# External Interface (alertnow)
ext_plugin_alertnow_send_alert=true
ext_plugin_alertnow_debug=true
ext_plugin_alertnow_level=1
ext_plugin_alertnow_webhook_url=Enter AlertNow webhook url here.
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
