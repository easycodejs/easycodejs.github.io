---
layout: default
title: React native 기본 환경 설정
parent: Install and Config
---

# 기본 환경설정 
## : nodejs, expo cli, Visual Studio Code 설치

1. 12.18.2 lts nodejs 설치 - 모든 옵션 함께
2. expo cli 설치 : 
    >$> npm install -g expo-cli
3. react-native 새 프로젝트 폴더 생성
    >$> expo init AwesomeProject
	>(blank 선택)
	>$> cd wesomeProject
4. react-native 프로젝트 실행
	>$> npm start // you can also use: 'expo start'  
	>$> 컨트롤 + c : 끝내기
5.  Visual Studio Code 설치

<br>

# 2) webView로 앱만들기

1. AwesomeProject 폴더로 이동
	>$> cd AwesomeProject
2. Visual Studio Code 실행
	>$> code .
3. Google 에서 검색어 "expo react native webview" 검색  
    - 선택:	WebView - Expo Documentation  
	'docs.expo.io › versions › latest › sdk' 클릭하여 이동
    - WebView 문서 중 Installation과 Usage 내용 참조
4. react-native-webview 설치
	>$> expo install react-native-webview

	Visual code 에서 : "이 시스템에서 스크립트를 실행할 수 없으므로 ...ps1 파일을 로드할 수 없습니다"라는 에러가 뜰 경우는 Windows에서 정책적으로 Powershell 실행에 제한이 있어서 뜨는 에러 메시지로서 ExecutionPolicy를 RemoteSigned로 변경해주는 것으로 해결이 가능하다.
	1. Visual Studio Code를 "관리자 권한으로 실행"한다
	2. Get-ExecutionPolicy : 현재 정책 확인  
	Set-ExecutionPolicy + 정책 : 정책 설정하기
	3. 정책의 종류

	>Restricted(제한된):
기본 실행 정책(기본적으로 적용되어 있음)  
명령어 하나씩 실행 가능(개별 명령은 허용하지만 스크립트를 실행하지 않음)  
.ps1 스크립트 파일을 로드하여 실행할 수 없음
  
	>AllSigned: 
	>- 스크립트 실행 가능
	>- 오직 신뢰된 배포자에 의해 서명된 스크립트만 실행할 수 있음
	
	>RemoteSigned:
	>- 로컬 컴퓨터에서 본인이 생성한 스크립트만 실행 가능
	>- 인터넷에서 다운로드한 스크립트는 신뢰된 배포자에 의해 서명된 것만 실행할 수 있음

	>Unrestricted(무제한):
	>- 모든 스크립트 실행 가능

	>ByPass:
	>- 어떤 것도 차단하지 않고 경고나 메시지 없이 실행할 수 있음

	>Undefined: 
	>- 설정된 정책이 없음
	>- 기본 실행 권한 정책 적용됨(Restricted)

5. Visual Studio Code에서 App.js 수정
	- WebView 내용 중 Usage 코드복사
	- App.js 기존 코드 지우고 붙여넣기
	- WebView source 'uri' 를 웹앱으로 만들 사이트 주소로 교체

6. 실행
	>$> npm start  // you can also use: 'expo start'

7. 스마트폰 expo 실행
	-  Scan QR Code 클릭하여 Metro Bundler QR Code 인식

8. 종료
	> 컨트롤 + c : 끝내기

<br><br>
----
# Expo-cli 환경설정

1. node js 설치 확인  
	> $> node -v

2. expo-cli 설치
	> $> npm install -g expo-cli

3. expoTest라는 이름의 새 react native project  생성
	> $> expo init expoTest  

	choose a template: blank 선택

4.  새로 생성된 expoTest 폴더로 이동  
	> $> cd AwesomeProject

5. expo 실행 : # you can also use: expo start
	> $> npm start

<br><br>
----
# react-native-cli 환경설정

1. node js 설치 확인  
	> $> node -v

2. expo-cli 설치
	> $> npm install -g expo-cli


<br><br>
-------
참조 도큐먼트

1. google 검색 : react native

2. React Native · A framework for building native apps using React  
https://reactnative.dev

3. Get started > Environment setup > Setting up the development environment

4. Expo CLI Quickstart & React Native CLI Quickstart 설정 참조