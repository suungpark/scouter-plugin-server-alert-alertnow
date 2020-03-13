# scouter-plugin-server-alert-alertnow
### Scouter server plugin to send a alert via AlertNow

- this project inspired by slack plugin project of 23king. thanks for this project.

- this project is  scouter server plugin project. this project goal is that send message to AlertNow.

- this project only support a sort of Alert.
	- CPU of Agent  (warning / fatal)
	- Memory of Agent (warning / fatal)
	- Disk of Agent (warning / fatal)
	- connected new Agent
	- disconnected Agent
	- reconnect Agent
    - Elapsed time threshold exceeded
    - GC Time threshold exceeded
    - Threshold of thread count exceeded

### Properties (you can modify in conf/scouter.conf of scouter server home )
* **_ext\_plugin\_alertnow\_send\_alert_** : can send AlertNow message or can'not  (true / false) - default : false
* **_ext\_plugin\_alertnow\_debug_** : can log message or can't  - default false
* **_ext\_plugin\_alertnow\_level_** : log level (0 : INFO, 1 : WARN, 2 : ERROR, 3 : FATAL) - default 0
* **_ext\_plugin\_alertnow\_webhook_url_** : AlertNow WebHook URL
* **_ext\_plugin\_elapsed\_time\_threshold_** : Threshold of elapsed time (ms) - The default value is 0, and when it is 0, it does not check whether the response time exceeds the threshold.
* **_ext\_plugin\_gc\_time\_threshold_** : GC Time Threshold (ms) - The default value is 0, and when it is 0, it does not check whether the GC Time threshold is exceeded.
* **_ext\_plugin\_thread\_count\_threshold_** : Threshold of Thread Count - The default value is 0, and when it is 0, it does not check whether the thread count threshold is exceeded.
* **_ext\_plugin\_alertnow\_xlog\_enabled_** : xlog maasege send (true / false) - default : false

* Example
```
# External Interface (AlertNow)
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
    - After building, the target directory is created under the project, and copy the scouter-plugin-server-alert-alertnow-1.0.0-SNAPSHOT.jar file and save it in the lib/ folder under the scouter server installation path.
