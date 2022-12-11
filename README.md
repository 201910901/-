# 코르도바 앱 설정 방법
### 준비물 및 준비사항
Android Studio / Gradle 7.3 / Java SE 8 / Apache ant 1.9.16 / node.js   
C:\ 쪽에 HybirdApp 및 HybirdProject 폴더 만들기   
1. cmd을 키고 명령어 cd c:\ 을 치기   
2. mkdir HybirdApp 과 mkdir HybirdProject 명령어 치기(C 폴더에서 그냥 만들어도 상관 없습니다.)   
  
####  Gradle 7.3 / Java SE 8 / Apache ant 1.9.16 / node.js 설치 
C:\HybirdApp에 Gradle 7.3 / Java SE 8 / Apache ant 1.9.16을 압축 풀기   
다운로드 주소   
[Gradle](https://gradle.org/releases/) / [Java_SE_8](https://jdk.java.net/archive/) / [Apache_ant](https://ant.apache.org/bindownload.cgi) / [node.js](https://nodejs.org/ko/) / [Android_Studio](https://developer.android.com/studio?gclid=Cj0KCQiA1ZGcBhCoARIsAGQ0kkpMkg67ztQNHLwHAk9KTvjcjzZKBGghifUzjE0h6QCzYj2FjxQxIPAaAjyNEALw_wcB&gclsrc=aw.ds)   

#### 환경변수 설정하기
윈도우 + x를 누르고 시스템 선택 그리고 고급 시스템 설정 누르기
고급 탭에서 환경 변수 클릭하고 새로 만들기하여 이름과 디렉터리 경로 설정하기   
JAVA_HOME   
C:\HybirdApp\jdk1.8XX   
(자바 이름이 달라도 상관없지만 반드시 JDK8이여야함)   
ANDROID_SDK_ROOT   
C:\Users\(사용자명)\AppData\Local\Android\SDK or android-sdk   
GRADLE_HOME   
C:\gradle7.3_bin

#### 환경변수 Path 설정하기
고급 탭에서 환경 변수 클릭하고 시스템 변수 안에 path 라는 변수을 찾아 눌러주고 편집 누르기   
그 안에서 새로만들기 해서 아래의 변수 추가하기   
%JAVA_HOME%\bin   
%ANDROID_SDK_ROOT%\tools   
%ANDROID_SDK_ROOT%\platform-tools   
%ANDROID_SDK_ROOT%\build-tools   
%ANDROID_SDK_ROOT%\cmdline-tools\latest\bin   
%ANDROID_SDK_ROOT\emulator   
%GRADLE_HOME%\bin   
c:\HybridApp\apace-ant-1.9.16\bin   
확인 버튼 누르고 다시 환경변수에서 확인 누르기   

##### Cordova 및 Phonegap 다운로드 및 Npm 업데이트
Node.js Command prompt 혹은 cmd 선택   
npm / node -version 명령어로 버전 확인   
npm update -g 명령어 치기   
npm install -g phonegap 설치하기   
npm install -g cordova 설치하기   

#### Android Studio에 SDK 추가 설치 및 에뮬레이터 설정하기
Android Studio 실행하고 상단 메뉴에 Tool을 선택하고 SDK Manager 클릭   
SDK Tools 및 SDK Platform을 클릭하고 해당 설치할 파일 설치하기   
SDK platforms   
Android 12L	32   
Android 12	31   
Android 11	30   
Android R	29   
SDK Tools   
Android SDK Tools   
Android SDK Platfor-tools   
Android SDK Build-tools   
Extra   
Android Support Repository   
Android Auto Desktop head unit emulator   
Android auto API simulator   
Google Repository   
Google USB Driver   
Google Play Services   
Android SDK Command-line Tools   
Intel x86 Emulator Accelerator(HAXM installer)   
옆 메뉴에 있는 Device Manager 에서 Create Device해서 NexusX5 or Nexus5 및 API 29 ~ 32 중 하나 선택하여 디바이스 생성하기   
(해당 설치파일이 없다면 없어도 무관합니다.)   
(Android Studio 종료 후에 C:\Users\[사용자명]\.android 내에 있는 debug.keystore파일 삭제)    

#### 코르도바 앱 설정하기
상단 경로 표시가 되어 있는 곳에서 app을 클릭하고 build.gradle(:app)을 클릭하기   
-android 밑에 namespace 위에 이 코드 집어 넣기   
packagingOptions {   
      exclude 'META-INF/DEPENDENCIES.txt'   
      exclude 'META-INF/LICENSE.txt'   
      exclude 'META-INF/NOTICE.txt'   
      exclude 'META-INF/NOTICE'   
      exclude 'META-INF/LICENSE'   
      exclude 'META-INF/DEPENDENCIES'   
      exclude 'META-INF/notice.txt'   
      exclude 'META-INF/license.txt'   
      exclude 'META-INF/dependencies.txt'   
      exclude 'META-INF/LGPL2.1'   
  }   
AndroidMainfast.xml에서 application 태그 안에 이 설정 코드 추가하기   
android:largeHeap="true"   
다 한 다음 저장하기

#### 코르도바 앱 만들기
C:\HybirdProject에 들어가기   
cordova create (폴더명) com.example.test (앱이름) -d로 코르도바 앱 만들기   
cd (폴더명)한 다음 cordova platform add android해서 플랫폼 추가
다 한 다음 cordova requirements해서 경로 및 설치가 다 되었는지 확인하기   
확인이 끝난 후 Android Studio을 실행 시키고 상단 메뉴에 File 클릭하고 open을 클릭하기   
C:\HybirdProject\(폴더명)\platforms\android 선택하고 설정 다운로드 완료까지 기다리기

####
